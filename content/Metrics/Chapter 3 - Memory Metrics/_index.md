---
title: "Chapter 3 - Memory Metrics"
date: 2021-06-11T11:31:22+10:00
draft: false
chapter: true
---

### Chapter 3

# Memory Metrics

We have covered CPU in depth in the previous chapter. Let's now take a trip down memory lane.

Memory differs from CPU as it is a form of storage. CPU is highly transient in nature. Instructions enter and leave the execution pipelines in less than a nanosecond. Memory is basically a collection of pages (blocks) in physical DIMM. Information is stored in memory in standard block sizes, typically 4 KB or 2 MB. Each block is called a page. At the lowest level, the memory pages are just a series of zeroes and ones. MS Windows initializes its pages with 0, hence there is zero page counter in ESXi.

While CPU discards instructions as they leave the CPU pipeline, memory keeps information for a much longer period of time. We are comparing nanoseconds to seconds (or longer, up to months, depending upon the uptime of your VM).

Keeping this concept in mind is critical as you review the memory counters. Memory has a very different nature compared to CPU, and the storage nature of memory is the reason why memory monitoring is more challenging than CPU monitoring. Unlike CPU, memory has 2 dimensions: Speed and Space

- **Speed** is measured in nanoseconds. The only counter ESXi has is Memory Latency. This counter increases when the time to read from the RAM is longer than usual. The counter tracks the percentage of memory space that’s taking longer than expected. It’s not tracking the actual latency in nanosecond. This is the opposite of Disk, where we track the actual latency, but not the percentage of amount of space that is facing latency. Both are storage, but “server people” and “storage people” measure them differently!
- **Space** is measured in GB. This is the bulk of the counters.

{{% children %}}