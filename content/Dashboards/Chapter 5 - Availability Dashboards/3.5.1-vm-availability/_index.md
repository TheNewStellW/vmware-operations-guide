---
title: "1. VM Availability"
date: 2021-06-15T22:35:44+10:00
draft: false
weight: 10
---

Use the VM Availability dashboard to calculate the availability of the Guest OS. The availability of the Guest OS is calculated because the Guest OS might not be running even when the VM is powered on. There are two layers of Availability, that is, the Consumer layer and the Provider layer. This dashboard covers the Consumer layer. You can view VMs in the selected data center, uptime trend for a selected cluster, and so on.

## Design Consideration

The dashboard is designed to help check the availability (uptime in percentage) of VMs, as availability is typically a part of services provided by the IaaS provider. 

This dashboard does not check the application up time. It is possible that the application (e.g. a database, web server) is down while the underlying Windows or Linus is up. Generally, the service provided by IaaS team is only until Windows or Linux. To check application level, use network ping or application specific agent (e.g. Telegraf)

## How to Use

Start in **Data centers** widget by selecting one of the data centers listed. 
- In small environment, or if you want to see overall, you click the **vSphere World** object. 
- The above action will update other widgets automatically. 
- Think of creating a filter for this table that reflect your class of service. Group by the class of services such as Gold, silver, and bronze and default the selection to Gold. In this way, the monitoring is not cluttered with less critical workloads, and you can focus on the important VMs. One way to achieve this is by creating a vRealize Operations custom group for each class of service

About the VMs by Uptime in the last 30 days bar chart
- It displays the average uptime of VMs grouped by their availability. The bucket distribution is designed to cater for a wide array of environment. If You are monitoring only production VMs, where uptime is expected to be near 100% all the time, edit the bucket to meet your operational need. 

About the VMs in the Selected Data center table
- It lists all VMs currently deployed to the data center. Average Uptime is displayed for the last 1 month of data. Expect this number to be 100% or near there for production VM. 
- Note that the **Services** column will be blank unless Service Discovery is enabled and services/processes were discovered on a specific VM. 
- The column **VMs** includes all VMs including powered off VMs.

Select a VM from the above table. 
- The remaining widgets will automatically show the detail of the selected VM.
- Selected VM Uptime Trend displays the selected VM’s Guest Tool Uptime (%) across the last 30 days.

Expand the 2 collapsed widgets 
- If Guest OS services or processes are discovered inside a VM, their availability is analyzed. Service ‘state’ over time is displayed in Guest OS: Services.
- The dashboard displays the process or services running inside the Guest OS. This requires the Service Discovery Management Pack.
- The ESXi Host where the VM has run widget can show historical migration of the VM. This can be useful in determining the cause of a VM downtime. 

## Points to Note
- The metric is only tracking the availability of VMware Tools, not the entire Guest OS. If Tools is not up, it assumes the Guest OS is down. To help you check that this is not a false negative, add a few line charts that shows sign of life. A good counter is IO counters such as Disk IOPS, Disk Throughput and Network Transmit Throughput, because IO requires CPU processing. CPU Usage is not a reliable counter as work by VMkernel on the VM is charged to the CPU counters. 
- vRealize Operations 8.2 sports a new ping adapter. This means you can enhance the accuracy of the uptime measurement by creating a super metric that adds the ping information or checking the process (needs an agent, such as Telegraf). 
- Add a property widget that lists the selected VM properties to give you more context about the VM. In large environment, it is possible that the VM name alone may not be providing enough context.