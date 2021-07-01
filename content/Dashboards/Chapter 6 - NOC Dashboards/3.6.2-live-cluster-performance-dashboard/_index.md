---
title: "2. Live! Cluster Performance Dashboard"
date: 2021-06-15T22:57:00+10:00
draft: false
weight: 20
---

This dashboard provides live information on whether the requests of the VMs are met by their underlying compute clusters. This dashboard focuses on the compute resources (CPU or Memory), and show if the cluster is performing well (i.e. meeting the demand). Use this dashboard to view if there is any problem in meeting the demands of the VMs.

This the primary dashboard for performance. It is complemented by the Live! Cluster Performance dashboard. This secondary dashboard complements it by showing if the performance problem (read: contention) was caused by high utilization. The primary dashboard answers the question "Is our IaaS performing?", while the secondary dashboard answers the question "Is our IaaS working hard?".

## Design Consideration

The dashboard shows 3 heat maps side by side. They complement each other and should be used together. The location of each cluster and ESXi hosts within those clusters is identical in all heat maps. This fixed positioning enables viewers to compare if the problem is caused by memory contention, CPU ready or CPU CoStop.

The size of each cluster and ESSi hosts are designed to be constant. Variable sizing creates a distraction, as the focus here is not capacity. Variable sizing can potentially result in small boxes, making it hard to read from a far.

The focus of performance is on population, not a single VM. This is not a single VM troubleshooting dashboard. We are looking at infra problem, not a single VM problem. As the infra counter is mathematically an aggregation of VM counters, we need to pick the right roll up strategy. As the goal is to provide early warning, we're not using average as the roll up technique, as it is too late as early warning. We use percentage of population exceeding a threshold. The threshold is set to be stringent so we can get early warning.

## How to Use

Look at the 3 heat maps and see if there is any color other than green.

- While each box is an ESXi, the counter is coming from all the VM in the host. It's not taking ESXi level counter at all. The counters used are % VMs facing CPU Ready, % VMs facing CPU CoStop, % VMs facing RAM Contention.
- The color is by percentage of VMs not being served well. We are not using Max among the VM as it's too extreme, placing too much focus on a single VM. On the other hand, we're not doing ESXi wide average, as that will be too late.
- Green indicates that almost 100% of the VMs are getting the CPU and memory they are asking. The threshold is set such that if 10% of the VM population is not getting the resources they are asking, the heat map will turn full red.
- Red indicates an early warning. Stringent thresholds are used to enable proactive attention & remediation operations. Because high standard is applied, it is possible that the heat map is showing red, but there is no complaint from VM owner yet.
- Light grey likely means there is no VM running on the host, hence the metric is not computing.

Check if there is unbalanced.

- There are 2 types of unbalanced: cluster unbalance and resource type unbalance
- The ESXi hosts are grouped together by the cluster, so unbalanced within a cluster can be seen easily. Cluster unbalance is a real possibility that is best monitored and not just assumed.
- If the 3 heat maps are quite different, there is resource unbalanced. For example, if the memory contention is mostly red, but the 2 CPU heat maps are green, that means you have unbalance between memory and CPU.
- If a single ESXi host is displaying a different color across 3 heat maps, it indicates imbalance between CPU and memory resources in the host.

For NOC Operator, drill down by selecting one of the ESXi on the heat map

- The "Trends of selected ESXi Host" will automatically show the performance counters
- It's showing from all 3 heat maps, so you can correlate. To hide any metric, simply click on its name on the legend.

As part of the deployment, it is best that you configure auto rotate among the NOC dashboard. If you only want to show 1 dashboard, you can remove vRealize Operations menu by using URL sharing feature. This will make the overall UI clean, enabling viewers to just focus on the dashboard.

## Points to Note

If you have the screen real estate, add a Heat Map for Disk Latency. Use the counter "Percentage of Consumers facing Disk Latency (%)". It is part of datastore object, not cluster, as a VM in a cluster can have disks across multiple datastores. Organize this storage performance by data center and not by cluster.