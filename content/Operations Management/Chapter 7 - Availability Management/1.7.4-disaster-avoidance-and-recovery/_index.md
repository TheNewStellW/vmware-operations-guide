---
title: "4. Disaster Avoidance and Recovery"
date: 2021-06-14T14:34:24+10:00
draft: true
weight: 
---

{{% notice info %}}
This page is for rent. Meaning we need a contributing author!
{{% /notice %}}

There are operational impact when you add capability to handle disaster. There are 3 primary use cases:

##### Disaster Avoidance

You avoid disaster by doing long distance vMotion on an stretched vSphere cluster. 

- Do you have enough WAN bandwidth? 
- Does the vMotion complete within the expected time? - If not, what’s causing it?
- What’s the performance impact during the vMotion? As the pipe is shared, this can impact other VMs too.

##### DR Test

You are doing a test, as required by regulator or internal Business Continuity Plan. Your production VM is still running, so you need to buble the network.

- Do you have enough capacity on the recovery site?
- Did it complete within the expected time? If not, what’s causing it?

##### DR Actual

You are doing the actual recovery. This can be planned or unplanned.
- Do you have enough capacity?
- What’s the performance impact on the target cluster and datastore?

In a large environment, you can have multiple clusters parcitipating in active/active DR, protecting one another. This can create complex relationship, especially if you have hundreds of business applications and they span across clusters.