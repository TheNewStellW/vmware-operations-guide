---
title: "5. Miscellaneous"
date: 2021-06-15T14:05:25+10:00
draft: true
weight: 50
---

## vSphere Data Center

he use case for higher level objects, such as Data center, Custom DC, vCenter and World need to reflect the nature of the object. The complex nature of the object needs to be accounted for. For example, a vCenter Data center object may span across physical data centers. This comes from the limitation that a stretched cluster is not a child of 2 separate data center objects, even when the clusters are physically in 2 separate buildings.

Large objects such as vCenter also tend to host clusters that serves different purpose, and hence are not compatible with one another. A free capacity on the NSX Edge cluster may not mean the business VM can be deployed, due to different storage, security, and network requirements.

These also apply to vRealize Custom Data Center, vCenter and World objects.

### Memory 

| Utilization (KB)     | Memory utilization level based on descendant VMs utilization. Includes reservations, limits and overhead to run VMs                     | Sum (\[HostSystem\]Memory\|Utilization)                                                  |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| Total Capacity (KB)  | Amount of physical memory configured on descendant ESXi hosts                                                                           | Sum (\[HostSystem\]Memory\|Total Capacity)                                               |
| Usable Capacity (KB) | Amount of usable memory resources for VMs after considering reservations for vSphere High Availability (HA) and other vSphere Services. | Sum (\[Cluster\]Memory\|Usable Capacity)                                                 |
| Workload (%)         |                                                                                                                                         | \[(Memory\|Machine Demand + Memory\|ESX System usage) / Memory\|Usable Capacity\] \* 100 |

### Disk Space

| Utilization (GB)    | Storage space utilized on connected vSphere Datastores        | Sum (\[Datastore\]Disk Space\|Utilization)                        |
|---------------------|---------------------------------------------------------------|-------------------------------------------------------------------|
| Total Capacity (GB) | Total Storage space available on connected vSphere Datastores | Sum (\[Datastore\]Disk Space\|Total Capacity)                     |
| Workload (%)        |                                                               | \[(Disk Space\|Utilization)/(Disk Space\|Total Capacity)\] \* 100 |

### CPU

| Demand (MHz)                  | CPU utilization level based on descendant VMs utilization. Includes reservations, limits and overhead to run VMs                     | Sum (\[HostSystem\]CPU\|Demand)                                                  |
|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| Total Capacity (MHz)          | Amount of CPU resources configured on descendant ESXi hosts                                                                          | Sum (\[HostSystem\]CPU\|Total Capacity)                                          |
| Usable Capacity (MHz)         | Amount of usable CPU resources for VMs after considering reservations for vSphere High Availability (HA) and other vSphere Services. | Sum (\[Cluster\]CPU\|Usable Capacity)                                            |
| Overhead (MHz)                |                                                                                                                                      | Sum (\[HostSystem\]CPU\|Overhead)                                                |
| Demand without overhead (MHz) |                                                                                                                                      | Sum (\[HostSystem\]CPU\|Demand without Overhead)                                 |
| Workload (%)                  |                                                                                                                                      | \[(CPU\|Demand without overhead + CPU\|Overhead) / CPU\|Usable Capacity\] \* 100 |

### Other Metrics

<table><colgroup><col style="width: 19%" /><col style="width: 45%" /><col style="width: 35%" /></colgroup><thead><tr class="header"><th>Maximum number of VMs</th><th><p>The supported configuration maximum as stated in vSphere Configuration <a href="https://configmax.vmware.com/home">website</a>. This number tends to be very high relative to typical deployment.</p><p>The metrics exist for vSphere, vCenter Data Center, vSphere Cluster, ESXi Host, Datastore and vRealize Operations Custom Data Center object</p></th><th>Number of Hosts * Maximum number of VMs per ESXi Host</th></tr></thead><tbody></tbody></table>

## Metric and Property Changes

One popular request among customers is we simplify our metrics and properties to improve both scalability and usability. You notice that some metrics are marked for deprecation:

- [vRealize Operations 8.3](https://kb.vmware.com/s/article/82345)
- [vRealize Operations 8.2](https://kb.vmware.com/s/article/80895)
  - We disable some instanced metrics here. You can enable them back.
- [vRealize Operations 8.1](https://kb.vmware.com/s/article/78493)
- [vRealize Operations 8.0](https://kb.vmware.com/s/article/74950)
- [vRealize Operations 7.5](https://kb.vmware.com/s/article/67734)
- [vRealize Operations 7.0](https://kb.vmware.com/s/article/58843)

Metrics and Properties can be deprecated or disabled for the following reasons:
- They are rarely used and hence have been disabled. If you plan to use them, you can enable them.
- They are duplicates. The replacement metric are provided.
- They are not the right indicator of performance or capacity issues. We have provided replacement metrics and guidance on how you should interpret the results.

More details [here](http://partnerweb.vmware.com/programs/vrops/DeprecatedContent.html).
