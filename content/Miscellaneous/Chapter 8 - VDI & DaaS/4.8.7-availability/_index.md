---
title: "7. Availability"
date: 2021-06-16T23:26:39+10:00
draft: true
weight: 70
---

{{% notice info %}}
This page is still in draft.
{{% /notice %}}

We covered in [Part 1 Chapter 1](#pillar-vs-process) that Availability can impact Performance and Capacity, but need to be measured separately.

Horizon consists of different components, each having their own availability metrics.

<table><colgroup><col style="width: 20%" /><col style="width: 79%" /></colgroup><thead><tr class="header"><th><strong>RDS Farm</strong></th><th><p>Number of RDS Hosts in Bad State</p><p>Aim for this number to be 0 at all times</p></th></tr></thead><tbody><tr class="odd"><td><strong>VDI Pool</strong></td><td><p>Number of VMs in the pool that is not used yet not available. The metric Desktop in Bad State can be unavailable because they are in one of these state</p><ul><li><p>Provisioning | Customizing | Starting Up | Deleting | Waiting for Agent</p></li><li><p>Maintenance mode | In Progress</p></li><li><p>Agent disabled | Agent unreachable | Agent needs reboot</p></li><li><p>Invalid IP | Protocol failure | Domain failure</p></li><li><p>Configuration error | Provisioning error | Error |Unknown</p></li></ul><p>For the description, see <a href="https://docs.vmware.com/en/VMware-Horizon-7/7.13/horizon-virtual-desktops/GUID-C66AE54D-21A1-41B3-93A6-8D8E7F448451.html">this</a>.</p></td></tr><tr class="even"><td><strong>Connection Server</strong></td><td></td></tr><tr class="odd"><td><strong>Pod</strong></td><td>Number of Connection Servers that are not available. The formula depends on the design. If it is N+1, then the availability will be affected when there is &gt;1 unavailable server.</td></tr></tbody></table>