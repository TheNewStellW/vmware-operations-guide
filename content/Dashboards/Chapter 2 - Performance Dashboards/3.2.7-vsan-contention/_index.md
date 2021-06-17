---
title: "7. vSAN Contention"
date: 2021-06-15T16:06:15+10:00
draft: false
weight: 70
---

The vSAN Contention Dashboard is the primary dashboard for vSAN performance. It’s designed for VMware Administrator or Architect, and can be used in both monitoring and troubleshooting. Once you determine there is performance issue, use the vSAN Utilization dashboard to see if the contention is caused by very high utilization. 

See the Performance Dashboard page for common design consideration among all the dashboards for performance management. 
As this dashboard is designed to complement the vSphere Cluster Capacity dashboard, it shares the same design consideration. It focuses on the storage and vSAN specific metrics, and does not repeat what’s already covered. It also does not list non vSAN cluster.

## How to Use

Review the 3 distribution charts
- They give an overview of all the vSAN clusters performance. 
- The first chart shows if the distribution of disk latency experienced by all the VMs in the cluster. You should expect majority of the VMs to experience latency that matches your expectation. For example, in an all flash systems, the VMs should not be having >20 ms disk latency. If your vSAN environment is all flash, you may need to adjust the distribution bucket to a more stringent set.
- The second chart shows if any of the vSAN kernel module has to wait for CPU. Expect this number to be near 0% and below 1%, as vSAN should not be waiting for CPU time. vSAN gets higher priority than VM World as it lives in the kernel space.
- The third chart shows if any of the vSAN cluster is dropping packet in the vSAN network (not the VM network). vSAN relies on network to keep the cluster in-sync. This number should be near 0% and less than 1%.

Review the **vSAN Clusters** table
- It lists all the vSAN clusters, sorted by the least performing. 
- It lists all the ESXi hosts, sorted by the worst performance in the last 24 hours. If the table is all showing green, then there is no need to analyze further. The reason 24 hours is chosen instead of 1 week is the performance > 24 hours are likely to be irrelevant. 
- You can change the time period to the period of your interest. The maximum number will be reflected accordingly. 
- All Flash and Hybrid have different performance. Since there is only 1 benchmark, the all flash will perform better than hybrid, and that’s what you expect to see.

Select a vSAN cluster from the table
- All the health charts will automatically show the KPI of selected cluster.
- vSAN Resync is a type of utilization metric, but its presence can impact performance. vSAN has two scenarios that trigger rebalance (the reason for resync). 
  - **Proactive**: A large variance among devices disk space utilization.
  - **Reactive**: When devices reach a critical capacity threshold (typically ~80%). This adjustment can be in the form of object components moving to other disks, disk groups, or hosts, or even splitting of existing large components into smaller components to achieve the desired result.
- If you are using SMART, the 2 heat maps at the bottom of the dashboard provides early warning.