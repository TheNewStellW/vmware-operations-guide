---
title: "4. VMware Tools"
date: 2021-06-15T13:58:38+10:00
draft: false
weight: 40
---

The following table explains the meaning of the value of Tools status property

| Value | Description|
| ----- | -----------|
| Guest Tools Not Installed | Tools are not installed on the VM. You should install it as you get both drivers and visibility|
| Current | Tools version matches with the Tools available with ESXi. Each ESXi has a version of Tools that comes with it. See this for the list. This is the ideal scenario|
| Supported New | Newer than the ESXi VMware tools version, but it is supported|
| Supported Old | The opposite of New. It is also supported. Even it is older by 0.0.1 is considered old. It does not have to far behind|
| Too Old | Tools version is older than the minimum supported version of Tools across all ESXi versions. Minimum supported version is the oldest version of Tools we support. Basically, guest is running unsupported Tools. You should upgrade. As of now for Linux and Windows guests. minimum supported version is the Tools version bundled with ESXi 4.0 which is 8.0.1. Supporting such old versions is challenging. We are planning to change this in future to something newer. In the meantime, you should upgrade as might not work as expected|
| Unmanaged | Tools installed in the guest did not come from ESXi, so Tools is not being managed by ESXi host. It may be supported or maybe not, depends on what type of Tools is running in the guest. We support open-vm-tools packaged by Linux vendors and OSPs, which both show up as unmanaged.<br />If a customer builds their own open-vm-tools from source code, we may not support that because we will not know if they have done it correctly or not|

I covered the various counters used by Tools in their respective section. The following table provides a summary with their key and formula. ***Not all counters*** are exposed by Tools and vRealize Operations.

If you notice a rare intermittent collection, check `vmware.log` of the VM. It could be that **vmtoolsd** daemon in Guest OS paused for a while, due to guest workload or other issue in Windows or Linux.

## Linux Memory Metrics

<table><colgroup><col style="width: 28%" /><col style="width: 58%" /><col style="width: 12%" /></colgroup><thead><tr class="header"><th>Stat Name</th><th>Source</th><th>Unit</th></tr></thead><tbody><tr class="odd"><td>guest.contextSwapRate</td><td>"ctxt" from /proc/stat</td><td>Number/sec</td></tr><tr class="even"><td>guest.mem.activeFileCache</td><td>"Active(file)" from /proc/meminfo</td><td>KB</td></tr><tr class="odd"><td>guest.mem.free</td><td>"MemFree" from /proc/meminfo</td><td>KB</td></tr><tr class="even"><td>guest.mem.physUsable</td><td>Sum of /proc/zoneinfo#present across all zones. Equals to VM configured RAM.</td><td>KB</td></tr><tr class="odd"><td>guest.mem.needed</td><td>"guest.mem.physUsable" - max(0, "MemAvailable" from /proc/meminfo - 5% of "guest.mem.physUsable")</td><td>KB</td></tr><tr class="even"><td>guest.page.inRate</td><td><p>"pgpgin" from /proc/vmstat</p><p>The rate of reads going through the underlying paging/cache system. It includes not just swapfile I/O, but cacheable reads as well.</p><p>I think Tools take the last value, and not the average over the last collection period. Meaning if Tools collect every 60 seconds, it takes 1 value at 60<sup>th</sup> second, not the average of 60 values in the entire 60 seconds.</p></td><td>Pages/sec</td></tr><tr class="odd"><td>guest.page.outRate</td><td><p>"pgpgout" from /proc/vmstat</p><p>The rate of writes going through the underlying paging/cache system. It includes not just swapfile I/O, but cacheable writes as well.</p></td><td>Pages/sec</td></tr><tr class="even"><td>guest.swap.spaceRemaining</td><td><p>"SwapFree" from /proc/meminfo</p><p>The amount of swap space remaining, taking into account the possibility of swapfile growth where possible. If the OS is configured without a swapfile, this will return zero.</p></td><td>KB</td></tr><tr class="odd"><td>guest.page.size</td><td>sysconf(_SC_PAGESIZE)</td><td>Bytes</td></tr><tr class="even"><td>guest.hugePage.size</td><td>"Hugepagesize" from /proc/meminfo</td><td>KB</td></tr><tr class="odd"><td>guest.hugePage.total</td><td><p>"HugePages_Total" from /proc/meminfo</p><p>Total large pages allocated</p></td><td>Large page count</td></tr><tr class="even"><td>guest.mem.neededReservation</td><td>5% of "guest.mem.physUsable"</td><td>KB</td></tr><tr class="odd"><td>guest.mem.available</td><td>"MemAvailable" from /proc/meminfo</td><td>KB</td></tr><tr class="even"><td>guest.mem.slabReclaim</td><td>"SReclaimable" from /proc/meminfo</td><td>KB</td></tr><tr class="odd"><td>guest.mem.buffers</td><td>"Buffers" from /proc/meminfo</td><td>KB</td></tr><tr class="even"><td>guest.mem.cached</td><td>"Cached" from /proc/meminfo</td><td>KB</td></tr><tr class="odd"><td>guest.mem.total</td><td>"MemTotal" from /proc/meminfo</td><td>KB</td></tr></tbody></table>

The above mapping and calculation are based on latest Linux [document](http://man7.org/linux/man-pages/man1/free.1.html) and [source code](https://gitlab.com/procps-ng/procps). As older Linux has used different formula, the future may change.

## Windows Memory Metrics

<table><colgroup><col style="width: 28%" /><col style="width: 71%" /></colgroup><thead><tr class="header"><th>Stat Name</th><th>Source</th></tr></thead><tbody><tr class="odd"><td>guest.contextSwapRate</td><td>Win32_PerfFormattedData_PerfOS_System = @#ContextSwitchesPersec from WMI</td></tr><tr class="even"><td>guest.mem.activeFileCache</td><td>Win32_PerfRawData_PerfOS_Memory = @#SystemCacheResidentBytes from WMI</td></tr><tr class="odd"><td>guest.mem.free</td><td>Win32_PerfRawData_PerfOS_Memory = @#FreeAndZeroPageListBytes from WMI</td></tr><tr class="even"><td>guest.mem.physUsable</td><td>Win32_OperatingSystem = #TotalVisibleMemorySize from WMI</td></tr><tr class="odd"><td>guest.mem.needed</td><td><p>guest.mem.physUsable - max(0, UNNEEDED_BYTES - 5% of guest.mem.physUsable),</p><p>where UNNEEDED_BYTES = "Win32_PerfRawData_PerfOS_Memory =@#FreeAndZeroPageListBytes" + "Win32_PerfRawData_PerfOS_Memory =@#StandbyCacheReserveBytes"</p></td></tr><tr class="even"><td>guest.page.inRate</td><td>Win32_PerfFormattedData_PerfOS_Memory = @#PagesInputPersec from WMI</td></tr><tr class="odd"><td>guest.page.outRate</td><td>Win32_PerfFormattedData_PerfOS_Memory = @#PagesOutputPersec from WMI</td></tr><tr class="even"><td>guest.swap.spaceRemaining</td><td>(maximum possible - used) swap space</td></tr><tr class="odd"><td>guest.page.size</td><td><a href="https://docs.microsoft.com/en-us/windows/desktop/api/sysinfoapi/ns-sysinfoapi-_system_info">SYSTEM_INFO.dwPageSize</a> returned by <a href="https://docs.microsoft.com/en-us/windows/desktop/api/sysinfoapi/nf-sysinfoapi-getsysteminfo">GetSystemInfo()</a></td></tr><tr class="even"><td>guest.hugePage.size</td><td><a href="https://docs.microsoft.com/en-us/windows/desktop/api/memoryapi/nf-memoryapi-getlargepageminimum">GetLargePageMinimum()</a></td></tr><tr class="odd"><td>guest.mem.neededReservation</td><td>5% of "guest.mem.physUsable"</td></tr><tr class="even"><td>guest.mem.availableToMm</td><td>Win32_PerfRawData_PerfOS_Memory = @#AvailableBytes from WMI</td></tr><tr class="odd"><td>guest.mem.standby.normal</td><td>Win32_PerfRawData_PerfOS_Memory = @#StandbyCacheNormalPriorityBytes from WMI</td></tr><tr class="even"><td>guest.mem.standby.reserve</td><td>Win32_PerfRawData_PerfOS_Memory = @#StandbyCacheReserveBytes from WMI</td></tr><tr class="odd"><td>guest.mem.standby.core</td><td>Win32_PerfRawData_PerfOS_Memory = @#StandbyCacheCoreBytes from WMI</td></tr><tr class="even"><td>guest.mem.modifiedPages</td><td>Win32_PerfRawData_PerfOS_Memory = @#ModifiedPageListBytes from WMI</td></tr></tbody></table>

## Linux CPU and Disk Metrics

| Name                       | Source                                                                  | Unit   |
|----------------------------|-------------------------------------------------------------------------|--------|
| guest.cpu.runQueue         | "procs_running" from /proc/stat                                         | Number |
| guest.disk.requestQueue    | Sum of pending IOs from /proc/diskstats across all active block devices | Number |
| guest.disk.requestQueueAvg | Sum of weighted time deltas across all active block devices             | Number |

## Windows CPU and Disk Metrics

| Stat Name             | Source                                                                                              |
|-----------------------|-----------------------------------------------------------------------------------------------------|
| guest.processor.queue | Win32_PerfFormattedData_PerfOS_System = @#ProcessorQueueLength from WMI                             |
| guest.disk.queue      | Win32_PerfFormattedData_PerfDisk_PhysicalDisk.Name = \\"\_Total\\"#CurrentDiskQueueLength" from WMI |
| guest.disk.queueAvg   | Win32_PerfFormattedData_PerfDisk_PhysicalDisk.Name = \\"\_Total\\"#AvgDiskQueueLength" from WMI     |