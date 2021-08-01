---
title: "7. Availability"
date: 2021-06-16T23:26:39+10:00
draft: false
weight: 70
---

{{% notice info %}}
This page is still in draft.
{{% /notice %}}

We covered in [Part 1 Chapter 1](/operations-management/chapter-1-overview/1.1.8-pillar-process-people/) that Availability can impact Performance and Capacity, but need to be measured separately.

Horizon consists of different components, each having their own availability metrics.

| Object | Availability Metric |
| --- | --- |
| **RDS Farm** | Number of RDS Hosts in Bad State <br />Aim for this number to be 0 at all times.|
| **VDI Pool** | Number of VMs in the pool that is not used yet not available. The metric Desktop in Bad State can be unavailable because they are in one of these states:<br /><ul><li>Provisioning \| Customizing \| Starting Up \| Deleting \| Waiting for Agent<li>Maintenance mode \| In Progress<li>Agent disabled \| Agent unreachable \| Agent needs reboot<li>Invalid IP \| Protocol failure \| Domain failure<li>Configuration error \| Provisioning error \| Error Unknown</ul>For the description, see [this](https://docs.vmware.com/en/VMware-Horizon-7/7.13/horizon-virtual-desktops/GUID-C66AE54D-21A1-41B3-93A6-8D8E7F448451.html).|
| **Connection Server** |  |
| **Pod** | Number of Connection Servers that are not available. The formula depends on the design. If it is N+1, then the availability will be affected when there is >1 unavailable server. |