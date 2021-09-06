---
title: "Chapter 1 - Overview"
date: 2021-06-11T11:31:22+10:00
draft: false
chapter: true
---

### Chapter 1

# Overview

Counters are essentially an accounting of systems in operation. To understand the counter requires a knowledge of how the system works. Without internalizing the mechanics, you will have to rely on memorizing. Memorizing is only good for exams. Take the time to truly understand it.

vSphere counters are more complex than physical machine counters because there are many components as well as inconsistencies that are caused by virtualization. When virtualized, the 4 elements of infrastructure (CPU, RAM, Disk, Network) behave ***differently***.

The complexity created by a new layer because it impacts the adjacent layers below and above it. So the net effect you need to learn three layers. That's why from a monitoring and troubleshooting viewpoint, [container](https://en.wikipedia.org/wiki/OS-level_virtualization) technology requires a deeper knowledge as the boundary is even less strict. Think of all the [problems](https://www.settlersoman.com/ftf-012-resource-pools-in-practice/) you have with vSphere Resource Pool performance troubleshooting, and now make it granular at process level!
