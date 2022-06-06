---
title: "9. Dashboards at Scale"
date: 2021-06-15T14:45:58+10:00
draft: false
weight: 90
aliases: ['/dashboards/chapter-1-design-considerations/3.1.9-dashboards-at-scale']
---

The number of dashboards you will have depends on the size of the environment and the number of people managing it. An environment with 100 VMs in just 5 hosts and 1 cluster will need far fewer dashboards than a global environment with 100,000 VMs spread over 5,000 ESXi, 500 clusters, 20 data centers, and 15 vCenter Servers.

In a large environment, where you have many physical data centers and even more vSphere clusters, you will likely need to display the information per physical data center. There are several reasons for this:

- Aggregating data at a global level, which spans many physical data centers, will hide too much information. Presenting data at such a level means you are getting an average of thousands of objects. If your environment is generally healthy (and it should be), the average will logically fall within a healthy range.
- In most cases, the performance in a given physical data center is independent from that of other data centers. For example, your Singapore data center typically does not impact the performance of your London data center. An exception to this case is when you link your data center at the network (stretched L2) and storage layers (synchronous replication). From experience in troubleshooting such a scenario, we recommend you keep the physical layer independent from each other. Assuming your data centers are independent, it makes more sense to display the chart on a per data center basis.
- VMs typically do not move from one physical data center to another (unless they are paired with storage replication and your network is stretched), so an imbalance among multiple data centers does not translate into a realistic rebalancing action.
