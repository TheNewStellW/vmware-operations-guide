---
title: "9. Network Performance"
date: 2021-06-15T16:10:21+10:00
draft: false
weight: 90
---

Use the Network Performance dashboard to view performance problems related to network such as high latency, frequent retransmit, and many dropped packets. This dashboard is designed for both VMware administrator and Network administrator, with the goal of fostering closer collaboration between the 2 team.

See the [Performance Dashboard](/dashboards/chapter-2-performance-dashboards/) page for common design consideration among all the dashboards for performance management.

The dashboard enables drill down from distributed switch to the ESXi host and port groups in the switch, and then to the VM.

## How to Use

Review the **Distributed Switches** table

- It lists all the switches, sorted by the highest packet dropped. The table splits the incoming traffic and outgoing traffic for better analysis.
- As the focus is performance and not capacity, the throughput counters are **not** shown.

Select a switch from the table

- The health chart will automatically show the dropped packet trend over time.
![Dropped Packet over time](3.2.9-fig-1.png)
- However, it will not narrow down the list of port groups automatically, as the list of port groups are always showing all the port groups in your environment.
- If necessary, expand the 2 collapsed widgets. They are showing the network throughput and broadcast packets. Utilization is also shown so you can correlate if the dropped packets are due to higher utilization

Review the port groups and ESXi hosts in the selected switch

- They are automatically listed when you selected a switch from the table above.
- Just like the distributed switch, you can also see their relevant countes.

If your environment has unused network switches, you can filter them out from this list, as this dashboard focuses on performance.

## Points to Note

- Latency within a data center should be below one millisecond. Use vRealize Network Insight to study the latency or the retransmitting problems, caused by moving into the lateral traffic.
- Add a physical network using the appropriate management pack, such as True Visibility Suite.
- Most packets are unicast, between a pair of sender and receiver. If your environment has many VMs sending broadcast packets to everyone and multicast packets to many targets, add a Top-N widget to find out which VMs are sending these packets.