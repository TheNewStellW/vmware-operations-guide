---
title: "13. Provider / Simplify It?"
date: 2021-06-15T22:24:32+10:00
draft: false
weight: 130
---

The "**Provider / Simplify It?**" dashboard complements the main vSphere configuration dashboards by displaying the actual vSphere objects, with their relevant information. It is designed for vSphere administrator and platform team. It is a part of 8 dashboards that check the environment for optimization opportunities.

The dashboard follows the same design consideration with the [Consumer / Correct it?](/dashboards/chapter-4-configuration-dashboards/3.4.7-consumer-correct-it/) dashboard. In fact, the 8 dashboards that form the Optimization Flow is designed as a set. You are meant to use them together as you go through the optimization review process.

## How to Use

Select one of the cluster from the table.

- A cluster is more complex to operate when it has resource pools, shares, and limits.

Review the Resource Pools list

- Ensure that the number of VMs in each resource pool reflects the intended settings for the resource pool. The resource pool value is divided and shared among the VMs. The more the VMs, the lesser the resources allotted to each VM.
- Verify if there are VMs who are sibling to the resource pools.
- Verify if the resource pools are further split into sub resource pools.

Review the CPU Share and Memory shares pie charts

- Multiple combinations of shares, especially both CPU and memory, makes troubleshooting difficult.
- Each share should map to exactly one class of service, such as one for Gold and one for silver, as the shares defines the class of service. Shares are also relative, meaning the value depends on the value of sibling objects such as, resource pool or VM.
- Ensure that the values are consistent across clusters to avoid unintended consequences while moving the VM to another cluster.

Review the CPU Reservation and Memory Reservation tables

- High total reservation, especially both CPU and memory, complicates the cluster operations as it impacts the HA slot calculation and limits the DRS choice of placement.

Click the object name to navigate to the Object Summary page to view more configurations. There can be valid reasons why specific configurations are not followed. It is recommended that you discuss best practices with VMware.

## Points to Note

See the [Points to Note](/dashboards/chapter-4-configuration-dashboards/3.4.7-consumer-correct-it/#points-to-note) section of [Consumer \ Correct it?](/dashboards/chapter-4-configuration-dashboards/3.4.7-consumer-correct-it/) dashboard. This dashboard follows the same design consideration with the dashboard, hence share the same limitations and customization idea.