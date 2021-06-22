---
title: "6. Usable Capacity"
date: 2021-06-14T10:59:22+10:00
draft: false
weight: 60
---

As covered earlier in the book, **usable** is a concept that applies only to capacity. There is no such thing as usable performance. Usable capacity is a non-real number that you get after deducting total capacity with the portion that capacity team decides to exclude. This portion typically accounts for availability, invisible demand and auxiliary demand. The number is non-real as the real available capacity can exceed that.

#### Availability

For hardware, this means the part that is added to cater for unavailability period. Common examples are RAID in disk, hot spare in storage array, vSphere HA in vSphere Cluster. Many hardware deployment come in a pair (e.g. network switches) because one of the node is for availability, not capacity.

In vSphere Cluster, you typically design with at least 1 host as spare, so you can perform maintenance, upgrade without service degradation. While this host is participating in reality, you exclude this in your capacity. vRealize Operations excludes HA from usable capacity.

#### Auxiliary Demand

This is typically overhead, which can happen at consumer layer (e.g. VM snapshot) or provider layer (e.g. vSAN resync, VMkernel CPU)