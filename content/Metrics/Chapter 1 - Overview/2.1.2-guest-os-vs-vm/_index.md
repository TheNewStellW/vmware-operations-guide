---
title: "2. Guest OS vs VM"
date: 2021-06-14T15:06:50+10:00
draft: true
weight: 20
---

Guest OS and VM are 2 closely related but different entities. They are adjacent layers in SDDC stacks. The two layers are distinct, each provide unique visibility that the other layer may not be able to give. Resource consumed by Guest OS is not the same as resource consumed by the underlying VM. Other factors such as power management and CPU SMT also contribute to the differences.

The following diagram uses the English words demand and usage to explain the concept, where demand consists of usage and unmet demand. It does not mean the demand and usage counters in vSphere and vRealize Operations, meaning don’t assume these counters actually mean this. They were created for a different purpose.

![](2.1.2-fig-1.png)

I tried adding Application into the above diagram, but that complicated the whole picture that I removed it. So just take note that some applications such as Java VM and database manage their own resources. Another virtualization layer such as Container certainly takes the complexity to another level.

We can see from the above that area A is not visible to the hypervisor. 

##### Layer A

Queue inside the Guest OS (CPU Run Queue, RAM Page File, Disk Queue Length, Driver Queue, network card ring buffer). These queues are not visible to the underlying hypervisor as they have not been sent down to the kernel. For example, if Oracle sends IO requests to Windows, and Windows storage subsystem is full, it won’t send this IO to the hypervisor. As a result, the disk IOPS counter at VM level will under report as it has not received this IO request yet.

##### Layer B

What the Guest actually uses. This is visible to the hypervisor as a VM is basically a multi-process application. The Guest OS CPU utilization somehow translates into VM CPU Run. I added the word somehow as the two counters are calculated independently of each other, and likely taken at different sampling time and roll up technique. 

##### Layer C

Hypervisor overhead (CPU System, CPU MKS, CPU VMX, RAM Overhead, Disk Snapshot). This overhead is obviously not visible to the Guest OS. You can get some visibility by installing Tools, as it will add new counters into Windows/Linux. Tools do not modify existing Windows/Linux counters, meaning they are still unaware of virtualization.

From VMkernel viewpoint, a VM is group of processes or user worlds that run in the VMkernel. There are 3 main types of group:
- VM Executable (VMX) process is responsible for handling I/O to devices that are not critical to performance. The VMX is also responsible for communicating with user interfaces, snapshot managers, and remote console.
- VM Monitor (VMM) process is responsible for virtualizing the guest OS instructions, and manages memory mapping. The VMM passes storage and network I/O requests to the VMkernel, and passes all other requests to the VMX process. There is a VMM for each virtual CPU assigned to a VM.
- Mouse Keyboard Screen (MKS) process is responsible for rendering the guest video and handling guest OS user input. When you console into the VM via vCenter client, the work done is charged to this process. This in turn is charged to the VM, and not specific vCPU.

If you want to see example of errors in the above process, review [this KB article](https://kb.vmware.com/s/article/1019471).

##### Layer D

Unmet Demand (CPU Ready, CPU Co-Stop, CPU Overlap, CPU VM Wait, RAM Contention, VM Outstanding IO). 

The Guest OS experiences a frozen time or slowness. It’s unaware what it is, meaning it can’t account for it.

----

I’ve covered the difference in simple terms, and do not do justice to the full difference. If you want to read a scientific paper, I recommend [this paper](https://link.springer.com/chapter/10.1007%2F978-3-642-29737-3_26) by Benjamin Serebrin and [Daniel Hecht](https://dblp.org/pid/73/11144.html).

As we cover the CPU, Memory, Disk, Network metrics in their respective sections later in the book, we will explain the differences in more detail. For now, we will provide some examples to drive the point.