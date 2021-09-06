---
title: "4. Datastore"
date: 2021-06-15T12:52:58+10:00
draft: false
weight: 40
---

Storage in VMware IaaS is presented as datastore. In some situation, RDM  and network file shares are also used by certain VM.

The underlying storage protocol can be files (NFS) or blocks (VMFS). vSAN uses VMFS as its *consumption* layer as the underlying layer is unique to vSAN, and hence vSAN requires its own monitoring technique. Because vSAN presents itself as a VMFS datastore you need to know that certain metrics will behave differently when datastore type is vSAN.

For NFS, as it is "Network File Share" (as opposed to block), you have no visibility to the underlying storage. The type of counters will also be more limited.

![NFS backed datastore](2.4.4-fig-1.png)

## Performance

Take note that datastores that share the same underlying physical array can experience problem at the same time. The underlying array can experience a hot spot on its own, as it is made of independent magnetic disks or SSD.

VMs in the same datastores can experience different latency. The following heat map shows all the VMs in a single VMFS datastore, backed by ExtremeIO. Notice two of the VMs experience latency above 10 ms, while many other VMs experience less than 1 millisecond.

![Differing latency](2.4.4-fig-2.png)

There are more counters available via vCenter API than what's presented in the UI. Just to recap, this is what you get in the UI.

![vCenter Metrics](2.4.4-fig-3.png)

Counters such as `Datastore \ Outstanding Read Requests` and `Datastore \ Outstanding Write Requests` are available only in the API. They are required for performance troubleshooting and capacity monitoring.

## Capacity

The primary counter for storage capacity is disk space. IOPS and Throughput are treated as performance metrics as they have no clearly identifable 100% marker. In capacity, you must be able to determine what is 100%.

| Counters | Description |
| --- | --- |
| `Disk Space \ Total Capacity` | The configured capacity from ESXi's viewpoint. This is what the ESXi host sees. This is not the underlying LUN or physical layer. It's a raw metric from vCenter, not a computed metric by vRealize Operations.<br>Same value with `Capacity \ Total Capacity` and `Summary \ Disk Capacity`. |
| `Disk Space \ Free Space` | The actual free space in your datastore. Allocated space but not consumed is not counted.<br>Same with `Capacity \ Available Space`|
| `Disk Space \ Utilization` | This is the actual consumption, not the allocated/provisioned as in Thin Provisioning case.<br>It's a raw metric from vCenter, not a computed metric by vRealize Operations.<br>Same with `Capacity \ Used Space`.|
| `Disk Space \ Virtual Disk` | Sum of all the VM metric `Disk Space \ Virtual Disk Used`|
| `Disk Space \ Snapshot` | Sum of all the VM metric `Disk Space \ Snapshot Space`<br>Use this to find which datastores are plagued by huge amount of snapshot.|
| `Disk Space \ Other VM` | Calculated internally by summing all the VM files that do not belong to virtual disk, snapshot and swap file.<br>Use this to find which datastores have potentially unused files.|
| `Disk Space \ Swap File` | Calculated internally by summing all the VM swap file. |
| `Capacity \ Total Provisioned Consumer Space` | You can certainly provision/allocate more than the physical capacity, by using thin provisioning. |

As you can see from the following, the last metric will be blank if there is no VM in the datastore.

![No VM empty datastore](2.4.4-fig-4.png)