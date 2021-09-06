---
title: "4. Disaster Avoidance and Recovery"
date: 2021-06-14T14:34:24+10:00
draft: false
weight: 40
---

{{% notice info %}}
We are seeking a contributing author as more needs to be added. For more information, see [Issue #4](https://github.com/TheNewStellW/vmware-operations-guide/issues/4) and our [Contributor guide](https://github.com/TheNewStellW/vmware-operations-guide/wiki).
{{% /notice %}}

There are operational impact when you add capability to handle disaster. There are 3 primary use cases:

#### Disaster Avoidance

You avoid disaster by doing long distance vMotion on an stretched vSphere cluster.

- Do you have enough WAN bandwidth?
- Does the vMotion complete within the expected time? - If not, what's causing it?
- What's the performance impact during the vMotion? As the pipe is shared, this can impact other VMs too.

#### DR Test

You are doing a test, as required by regulator or internal Business Continuity Plan. Your production VM is still running, so you need to bubble the network.

- Do you have enough resources on the recovery site?
- Did it complete within the expected time? If not, what's causing it?

#### DR Actual

You are doing the actual recovery. This can be planned or unplanned.

- Do you have enough resources?
- What's the performance impact on the target cluster and datastore?

In a large environment, you can have multiple clusters parcitipating in active/active DR, protecting one another. This can create complex relationship, especially if you have hundreds of business applications and they span across clusters.

There is also impact on capacity and performance.

#### Capacity

This is covered earlier in Capacity chapter.

#### Performance

Historical counters need to follow the VM. This is tricky as there are actually 2 VM on 2 different vCenters. If the DR has inferior hardware because you're only running temporarily, you need to adjust your alert settings.