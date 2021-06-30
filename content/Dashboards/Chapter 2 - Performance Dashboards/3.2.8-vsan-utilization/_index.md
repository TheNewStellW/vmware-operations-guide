---
title: "8. vSAN Utilization"
date: 2021-06-15T16:08:15+10:00
draft: false
weight: 80
---

The **vSAN Utilization** dashboard complements the **vSAN Contention** dashboard. Together, their goal is to help VMware Administrator in performance management.

Use this dashboard to identify vSAN clusters with high utilization in a selected data center. When utilization exceeds 100%, performance can be negatively impacted especially when VM experience contention. By default, vRealize Operations has a 5-minute collection interval. For 5 minutes, there may be 300 seconds worth of data points. If a spike is experienced for a few seconds, it may not be visible if the remaining of the 300 seconds is low utilization.

See the [Performance Dashboard](/dashboards/chapter-2-performance-dashboards/) page for common design consideration among all the dashboards for performance management.

## How to Use

Review the Clusters Utilization table

- It lists all the vSAN clusters, sorted by the least performing.
- The table shows the highest 5-minute average in the given period. Peak was chosen due to customers focus on peak when it comes to performance monitoring. To avoid outlier, change to 99thpercentile if that fits your operations better.
- vSAN clusters IOPS and Throughput are typically correlated with the number of host and VM.

Select a vSAN cluster from the table

- All the health charts will automatically show the KPI of selected cluster.
- Both IOPS and Throughput as large block size can result in high throughput in relatively low IOPS. If you are seeing large block size when You are not expecting it, investigate which applications are the using it.
- Read and Write are split as they tend to have different patterns.
- Health chart is not used as utilization can't be color coded.
- Max IOPS among capacity disk is shown as a disk has a limit, especially magnetic disk. A typical magnetic disk delivers ~200 IOPS, and this can be easily saturated.
Review the Disk Groups table
- It lists all the vSAN clusters, sorted by the least performing.
Select a Disk Group from the table
- All the health charts will automatically show the KPI of selected cluster.

## Points to Note

See the [vSAN Contention](/dashboards/chapter-2-performance-dashboards/3.2.7-vsan-contention/) dashboard as this dashboard is designed to complement it.