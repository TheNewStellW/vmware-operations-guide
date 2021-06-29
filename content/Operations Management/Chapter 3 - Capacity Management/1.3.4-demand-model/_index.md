---
title: "4. Demand Model"
date: 2021-06-14T10:54:46+10:00
draft: false
weight: 40
---

Demand reflects the reality in production, as it's based on the actual demand for resources in a cluster and datastore. It is enabled by default without any configuration and cannot be disabled.

Demand is more than the active load that is consuming your capacity. Active load is the visible demand, which you can monitor with the utilization metrics. There are demand that are not visible, because it has no utilization at present.

Use the Allocation Model and buffer settings in vRealize Operations to cater for this invisible demand. Note that buffer is applied after Availability.

#### Sudden Demand

This can wreak havoc in a shared environment. A group of highly demanding VMs can collectively impact overall performance of the cluster or datastore. An example of this is annual sales or stock market crash. In this case, the capacity team should set an appropriate overcommit ratio and drive by allocation as the demand is low most of the time.

#### Latent Demand

Many critical VMs are protected with Disaster Recovery. During a DR drill or actual disaster, this load will 'wake up' and consume. You should consider the Site Recovery Manager plans into your capacity.

#### Potential Demand

Many newly provisioned VMs take time to reach their full expected demand. It takes time for the database to reach the full size, the user base to reach the target, and the functionalities to be complete. Newly provisioned VM tend to be idle (which can be months) and may suddenly grow. When this happens, it will result in an increase in demand.

#### Unmet Demand

There are 2 parts to it: inside the VM and outside the VM.

If the VM is undersized, the unmet demand will not be visible to the underlying infrastructure. Unless that is intentional, it is wise to include undersized VM in the cluster capacity monitoring.

The visible part of unmet demand becomes part of IaaS KPI and SLA, covered in Performance Management chapter.

------

There are 2 other consideration when calculating demand in the context of capacity.

- Reservation
- Limit

Reservation that is not yet consumed impacts capacity but not performance. Using a restaurant analogy, if all your tables are reserved but only 20% turns up, you have 0 capacity left but can easily serve all customers the real demand is only 20%.

CPU and Memory behave differently as CPU reservation does not take effect when the reservation holder does not use it.

Limit needs to be considered as the demand can't exceed the enforced limit. The good part is the demand counter already takes that into account.
