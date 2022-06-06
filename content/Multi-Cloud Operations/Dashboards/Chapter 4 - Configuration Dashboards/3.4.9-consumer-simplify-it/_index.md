---
title: "9. Consumer / Simplify It?"
date: 2021-06-15T22:08:41+10:00
draft: false
weight: 90
aliases: ['/dashboards/chapter-4-configuration-dashboards/3.4.9-consumer-simplify-it']
---

The "Consumer / Simplify It?" dashboard complements the main VM configuration dashboard by displaying the actual VMs, with their relevant information. It is designed for vSphere administrator and platform team, to facilitate the follow-up action with the VM owners. It is a part of 8 dashboards that check the environment for optimization opportunities.

The dashboard follows the same design consideration with the [Consumer / Correct it?](/dashboards/chapter-4-configuration-dashboards/3.4.7-consumer-correct-it/) dashboard. In fact, the 8 dashboards that form the Optimization Flow is designed as a set. You are meant to use them together as you go through the optimization review process.

## How to Use

The dashboard is just a collection of tables (List View), which can be reviewed independently. There is no flow among them.

Click the object name to navigate to the Object Summary page to view more configurations. There can be valid reasons why specific configurations are not followed. It is recommended that you discuss best practices with VMware.

About the Large VMs (CPU, memory, and Disk) tables:

- A large VM, relative to the underlying ESXi host and datastore, requires more careful planning (Day 0) and monitoring (Day 2).
- Ensure that the VM size does not exceed the size of the underlying ESXi host. If your ESXi host has CPU hyper-threading, do not count the logical processor. Instead, count the physical core. For best performance, keep it within a (non-uniform memory access) NUMA boundary.
- During monitoring, verify if the VM is highly utilized. If the VM vCPU count is equal to the ESXi cores, and the VM is running at almost full capacity, you might not be able to run other VMs. Large VMs can impact the performance of other VMs, especially if it's given higher shares. Only when the large VM is under-utilized, can the ESXi run other VMs.
- Note that if the number of configured vCPUs on a VM is higher than number of cores per socket on the ESXi, the VM can experience NUMA effect. If the ESXi has more than one physical CPU (socket), cross-NUMA access negatively impacts performance
- The larger the VM, the longer time is required to vMotion, Storage vMotion, and backup.
- For disk space, if the disk is thin-provisioned and under-utilized, you can deploy other VMs in the same datastore. Ensure that the snapshot is tracked closely, as the risk of capacity running out is higher for a large virtual disk.

VMs with many virtual disks:

- It is simpler to have a 1:1 mapping between Guest OS partitions and the underlying virtual disk (VMDK or RDM).
- For performance and capacity, evaluate the disks and partitions. Each virtual disk must be monitored in terms of IOPS, throughput, and latency. Having multiple virtual disks increases the monitoring and troubleshooting need.
- If the reason for having many virtual disks is performance, identify which counter serves as proof that multiple virtual disks are required. It is possible that the performance required is met by a single virtual disk.

VM with many IP addresses or NICs:

- A VM might need multiple networks, such as production, back up, and management. It is recommended that you route the network interfaces through the NSX-Edge VM. A VM that has multiple network interfaces can bridge the network, causing security risks or network issues.
- A VM that is part of multiple networks can do so with just a single NIC card. A single NIC can be configured to access multiple networks, with each interface having their own IP configuration

## Points to Note

See the [Points to Note](/dashboards/chapter-4-configuration-dashboards/3.4.7-consumer-correct-it/#points-to-note) section of [Consumer / Correct it?](/dashboards/chapter-4-configuration-dashboards/3.4.7-consumer-correct-it/) dashboard. This dashboard follows the same design consideration with the dashboard, hence share the same limitations and customization idea.
