---
title: "4. ESXi Contention"
date: 2021-06-15T15:53:46+10:00
draft: false
weight: 40
---

The ESXi Contention Dashboard is the primary dashboard for ESXi host performance. It's designed for VMware Administrators or Architects, and can be used in both monitoring and troubleshooting. Once you determine there is performance issue, use the **ESXi Utilization** dashboard to see if the contention is caused by very high utilization. 

## Design Consideration

The dashboard is designed to complement the **Cluster Contention** dashboard by providing the next level of details. Hence it has a very similar layout. 

It is also designed to complement the vSAN Contention dashboard. In vSAN, the ESXi where the VM is running is potentially not where the file blocks are residing. So there are Compute Host and Storage Hosts. There are a few Storage Hosts, depending on the vSAN FTT setting. This relationship is not shown in the UI. 

This dashboard is designed to be used as part of your [Standard Operating Procedure](https://en.wikipedia.org/wiki/Standard_operating_procedure) (SOP). It is designed to be used daily, hence the views are set to show data in the last 24 hours. The dashboard provides performance metrics for VMs in the selected data center. 

See the Performance Dashboard page for common design consideration among all the dashboards for performance management. 

This dashboard is required for environment with standalone ESXi host (not part of a cluster).

## How to use

Review the 2 distribution charts. They give an overview of all the ESXi Hosts utilization and memory performance.

![](3.2.4-fig-1.png)

Both charts are using the percentage of VM facing performance counter, and not the worst performance among VM counter. The reason is you are looking at ESXi performance, and not a single VM performance. So you want to see how it handles all the VMs.

The bar chart is color coded. You want to keep the percentage of VM population not being served as low as possible. Your tolerance level depends on the criticality of the environment. 

Review the ESXi Hosts Performance table
- It lists all the ESXi hosts, sorted by the worst performance in the last 24 hours. If the table is all showing green, then there is no need to analyze further. The reason 24 hours is chosen instead of 1 week is the performance > 24 hours are likely to be irrelevant. 
- You can change the time period to the period of your interest. The maximum number will be reflected accordingly. 
Select an ESXi Host from the table
- All the health charts will automatically show the KPI of selected cluster.
- For performance, it's important to show both depth and breadth of performance problem. A problem that impacts 1-2 VM requires a different troubleshooting that a problem that impacts all VMs in the cluster. 
- Worst CPU Overlap among VM in the host is included as it indicates a lot of interrupts. A running VM was interrupted because VMkernel needs the physical core to run something else. A high and frequent number of interruptions is not healthy. This can also impact the VM performance. 
- Expect the network error 1% and dropped packet to be 0 most of the times, if not always. If it's not, analyze to see if there is any patterns across all ESXi Hosts, and bring it up to your network team. 

## Points to Note

- Consider adding a 3rd distribution chart if you have the screen real estate. Show the CPU Co-Stop counter in this 3rd chart, as it complements the CPU Ready counter. If your environment has relatively slow network and storage IO, you can add VM Wait too. 
- Unlike the Cluster Performance dashboard, there is no average ESXi Hosts Performance (%) at vSphere World level. The reason is most ESXi Hosts are part of cluster and monitoring should be done at cluster level.
- Certain settings such as power management and hyper threading can impact performance. Consider adding a property widget to show relevant property of a selected ESXi Host.
- If you use VMFS datastores, add the disk contention metrics such as Bus Reset and Aborted Commands. You should expect they return 0 at all times.
