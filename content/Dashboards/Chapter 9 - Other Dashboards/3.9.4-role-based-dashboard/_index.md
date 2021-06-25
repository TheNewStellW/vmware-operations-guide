---
title: "4. Role-Based Dashboard"
date: 2021-06-16T14:00:42+10:00
draft: false
weight: 40
---

## Storage Team

Ask any Storage Team and Platform Team whether the collaboration between them can be improved by a mile, and you are likely to get a nod. One reason for this issue is there is lack of common visibility. You need to see the same thing if you want to collaborate. Storage Team do not get always get access vSphere. Even if they do, vCenter UI is not designed for Storage team. It is designed for VMware Admin.

vRealize Operations and Log Insight can bridge that providing a set of read-only, purpose-built dashboards, that answer common questions such as:

- When a VM Owner complains, can we agree if it's a storage issue within 1 minute? This will help reducing the ping pong game between VM Owner, vSphere Admin, and Storage Admin.

- Is the Storage serving all the VMs well? If not, who are affected, when and how bad? Read or Write? The answer has to be tier based, as Tier 1 VM expects lower latency than Tier 3.

- What's the total demand hitting the array? Are they growing fast and becoming a risk? Who are the heavy hitters among the VMs?

- When & where are we running out of capacity? How much disk space can be reclaimed? From which VMs?

- What have we got? Are they consistently configured?

The questions above cover the main areas of SDDC Operations, such as performance, capacity, configuration and availability. They enable joint troubleshooting, capacity planning, performance monitoring. For better collaboration, add physical array monitoring into vRealize Operations and Log Insight, so you can analyze physical arrays and fabrics, and then correlate back with vSphere.

The dashboards should provide overall visibility to Storage team. They give insight into the SDDC by showing relevant objects by:

- quickly showing the summary of key information.

- showing VM, datastore, datastore clusters, compute cluster, and data center. It shows their relationship, which you can interact and drill down.

-   showing all the VMs, where they are located, how much space they are allocated, and how they are using it.

-   Showing physical arrays inventory and how they map into vSphere.

## Network Team

Similar to the problem face between Storage Team and Platform Team, VMware Admin needs to reach out to Network Team. A set of purpose-built dashboards will enable both teams to look at issue from the same point of view.

The world of network is highly complex, given its nature as interconnect.

The dashboards must answer the following basic questions for Network Team:

- What have I got in this virtual environment?

    -   What is the virtual network configuration? What are the networks, and how big are they?

    -   We have Distributed Virtual Switches, Distributed Port Group, Data center, Cluster, ESXi, etc. How are they related? Distributed Switch does not span beyond vSphere Data Center. So data center is a logical choice to start analysing the relationship.

    -   Who are the consumers of my network? Where are they located?

-   Are they healthy?

    -   Do we have any errors in our networks? Which port groups see packets dropped? If there is problem, which VMs or ESXi, are affected?

    -   Do we have too many special packets? Broadcast, multicast and unknown packets. Who generates them and when?

    -   The two primary counters are bandwidth and latency. [Bruce Davie](https://www.linkedin.com/in/bruce-davie/) explains both in this book[^1], specifically this [page](https://book.systemsapproach.org/foundation/performance.html), that the two counters work together. The reason is some applications are latency sensitive, while others are bandwidth hungry.

-   Are they optimized?

    -   Just because something is healthy does not mean they are optimized. Look for opportunity to right size.

Once Network Admin know what they are facing, they are in better position to analyze:

-   Utilization

    -   Is any VM or ESXi near its peak in network? Which VXLAN is the busiest?

    -   Who are the top consumer for each physical data center? What's their workload pattern?

    -   How is the workload distributed in this shared environment?

-   Performance

    -   When VM Owner thinks Network is the culprit, can both Network Team and Platform verify that quickly?

-   Configuration

    -   Is the configuration consistent across objects of the same kind? Do they follow best practice?

    -   What are the virtual networks, and how do they map into the physical top-of-rack switches?

#### Application Team

A common request among VMware Admin is to give their customers a self-service access to their own VMs. The VM Owners should be given a simple portal, where they can easily see all their VMs and its performance. You can use the dashboard sharing feature of vRealize Operations for a login-less access.

But what if you have many tenants? You don't want to create a dashboard for each of them one by one. The challenge here is how to use the same dashboard for multiple applications teams, assuming they are not allowed to see one another VMs. This requires a security mapping. Each tenant needs to have a login ID, which must be mapped to their VM.

| **Role**      | The first step is to create a role and give it limited access. All tenants user accounts will be mapped to this role. This role should not be able to browse the inventory. Its only access is to the group of tenants. |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Dashboard** | Create a common dashboard and map to the role. This role can't see any other dashboards                                                                                                                                 |
| **Tenant**    | For each tenant, you need to create a user ID. This ID is then mapped to a group. The group has the tenant VMs. In this way, the tenant ID will not be able to see other VMs.                                           |

#### Small Team

The Small Medium Business segment is a world of its own. There are roles and process that are mandatory in Enterprise segment, but not relevant in SMB segment. As a result, products should be tailored for that market segment. You can create a set of consolidated dashboards for this market, as the environment is much smaller.

Let's look at some unique characteristics of operations in this small environment:

-   1-2 guys doing everything. No siloes in the team. You and your best friends take care of the whole darn IT.

-   You only have a few clusters. Each cluster only has a few ESXi Host.

-   You know your environment very well because it's small. They all fit into 1 rack. Architecture is simple. You have a mental picture of it in your head.

-   You don't buy hardware or VMware every quarter. In fact, it's more like every 3 years. Capacity planning and monitoring become simple as you can do it manually using a simple spreadsheet.

-   The workload is quite stable. You are not adding/removing/changing VM every day.

-   Service Tier is an overkill as you only have 1-2 clusters for all workloads.

You still need to cover all the key areas of operations, from availability to performance to compliance. As self-service is expected, you need to provide a dashboard for application team.

[^1]: The book is freely available, and that's part of the reason why I decided to make mine free.