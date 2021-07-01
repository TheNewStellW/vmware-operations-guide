---
title: "11. Provider / Correct It?"
date: 2021-06-15T22:17:49+10:00
draft: false
weight: 110
---

The "**Provider / Correct It?**" dashboard complements the main vSphere configuration dashboards by displaying the actual vSphere objects, with their relevant information. It is designed for vSphere administrator and platform team. It is a part of 8 dashboards that check the environment for optimization opportunities.

The dashboard follows the same design consideration with the [Consumer / Correct it?](/dashboards/chapter-4-configuration-dashboards/3.4.7-consumer-correct-it/) dashboard. In fact, the 8 dashboards that form the Optimization Flow is designed as a set. You are meant to use them together as you go through the optimization review process.

## How to Use

The dashboard is organized into 3 sections for ease of use.

The first section covers vSphere clusters configuration

- A cluster is the smallest logical building block for compute. Consider it as a single computer with physically independent components. As a result, consistency matters.
- Clusters with DRS set to manual. This means that DRS initiated vMotion does not take place unless it is manually approved by administrator. Since DRS calculates every five minutes, your quick approval is required to prevent a change of condition.
- Clusters with HA disabled. Without high availability provided by the infrastructure, each application must protect itself from infrastructure failure.
- Clusters with DRS disabled. DRS focuses on performance and capacity, while HA focuses on availability. Without DRS, you must build a buffer on every ESXi host to cope with peak demand.
- Clusters with Admission Control disabled. Reservation is respected only when Admission Control is enabled.

The second section covers ESXi host configuration

- ESXi with Network Time Protocol disabled. Incorrect time can turn logs from useful to potentially misleading. Logs are a critical component of operations, and are the main source of information in troubleshooting. While troubleshooting performance across objects, the sequence of logs determines which event is the likely root cause as the oldest event started the chain of events.
- A disconnected ESXi host indicates that the ESXi host is not participating in HA and you cannot migrate any VM on it.
- An ESXi host that is in maintenance mode does not contribute resource to the cluster (or data center in the case of standalone ESXi).

The third section covers ESXi host configuration that need to be consistent within a cluster

- BIOS version and ESXi versions.
- BIOS Power Management, ESXi: Power Management. Ideally, should be set to OS controlled. The ESXi level should be set to balance level.
- ESXi Storage Path. Ensure that the number of paths and the path policies are identical.
- ESXi hardware specifications. Different specifications can result in inconsistent performances experienced by the VM.

## Points to Note

- See the [Points to Note](/dashboards/chapter-4-configuration-dashboards/3.4.7-consumer-correct-it/#points-to-note) section of [Consumer / Correct it?](/dashboards/chapter-4-configuration-dashboards/3.4.7-consumer-correct-it/) dashboard. This dashboard follows the same design consideration with the dashboard, hence share the same limitations and customization idea.
- If you have standalone ESXi and you plan to replace them with clustered ESXi host, add a table to list them.
- Based on your security settings, add a table to check Distributed Switch and Port Group to ensure that security settings such as promiscuous mode are used correctly.