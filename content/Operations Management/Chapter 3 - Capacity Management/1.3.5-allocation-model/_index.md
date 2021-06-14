---
title: "5. Allocation Model"
date: 2021-06-14T10:57:22+10:00
draft: true
weight: 50
---

The allocation model is ***not*** enabled by default as the overcommit ratio varies among customers. You should configure it appropriately to account for all the types of demand that is relevant for that cluster. By using both, you can account for both inputs (real demand and unreal demand).

The next use case for allocation is showback and reporting. There are typically restrictions such as contractual obligations or SLAs that mandate capacity not be overcommitted beyond an agreed upon ratio. Note these restrictions are usually non-technical.

Some customers like to do procurement planning based on overcommit ratios. A comfortable overcommit ratio is determined, and that’s what is used to project utilization into the future. The overcommit ratio is intended to be a rough estimate of utilization, e.g. 4:1 CPU overcommit ratio means that on average each vCPU will only run 25% utilization.

The allocation model has 3 main limitations:

##### VM Size

VM size is not considered in the overcommit ratio. It assumes that scheduling two monster VMs is as easy as scheduling many small VMs. The ESXi scheduler can juggle more small VMs than a few large ones, especially if they peak at different times.

##### Over-provisioned VM

It is common to have over-provisioned VM issue, especially among the large VMs. It is hard to solve this in production environment as it will involve downtime and the burden is on you to prove it will not have performance impact. Politically, it may make the team who sized the VM and justified the cost look bad. Your best bet is to prevent the problem from happening in the first place, by using progressive pricing. This is covered in the Pricing section of the book.

##### IaaS Workload

IaaS workload that do not take the shape of VM is not considered. VMkernel, vSAN, NSX, vSphere Replication, and vMotion all need to be considered. On the other hand, Agent VM is included as it takes the shape of a VM, although it tends to use local datastore.