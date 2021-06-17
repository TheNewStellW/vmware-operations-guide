---
title: "14. Provider \\ Optimize It?"
date: 2021-06-15T22:27:39+10:00
draft: false
weight: 140
---

The “**Provider \ Optimize It?**” dashboard complements the main vSphere configuration dashboards by displaying the actual vSphere objects, with their relevant information. It is designed for vSphere administrator and platform team. It is a part of 8 dashboards that check the environment for optimization opportunities. 

The dashboard follows the same design consideration with the “Consumer \ Correct it?” dashboard. In fact, the 8 dashboards that form the Optimization Flow is designed as a set. You are meant to use them together as you go through the optimization review process. 

## How to Use

The dashboard is organized into 3 sections for ease of use. 

The first section cover vSphere clusters configuration
- A small cluster has a higher HA overhead when compared to a large one. For example, a three-node cluster has 33% overhead while a 10-node cluster has 10%. For vSAN, a low number of hosts limits the availability option. Your choice of FTT is relatively more limited. 
- Many small clusters result in silos of resources. As a cluster behaves like a single computer, ensure that it has enough CPU cores, CPU GHz, and Memory. For ESXi in 2020, it is typical to have 512 GB of memory. This results in 12 TB of memory for a 12-node cluster, which is enough for DRS to place many VMs as it balances them. 
- If you have a lot of reservation, add a list for clusters with a relatively high reservation. If your clusters are of different size, use a super metric to convert the reservation value to a percentage.

The second section cover ESXi Host configuration
- Small ESXi. A small host faces scalability limits in running a larger VM. While a 2-socket, 32-cores, 128 GB memory ESXi can run 30 vCPU, 100 GB memory VMs, the VM experiences a non-uniform memory access (NUMA) effect. 
- ESXi powered off. You can mark the ESXi hosts for decommissioning using the custom property feature of vRealize Operations. You can then create a separate list so they are not overlooked. 

The third section cover storage and network
- Unused network (distributed port group). This is a potential security risk as you may have the tendency of not monitoring it

## Points to Note
- See the Points to Note section of “Consumer \ Correct it?” dashboard. This dashboard follows the same design consideration with the dashboard, hence share the same limitations and customization idea. 
- For CPU cores, a change in vSphere licensing means that the ideal core is 32 cores per CPU socket. This maximizes the software license. For more information, see vSphere [Pricing Model](https://www.vmware.com/company/news/updates/cpu-pricing-model-update-feb-2020.html).
