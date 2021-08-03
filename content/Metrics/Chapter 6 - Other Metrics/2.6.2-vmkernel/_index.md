---
title: "2. VMKernel"
date: 2021-06-15T13:45:52+10:00
draft: false
weight: 20
---

There are two types of counters here: reservation and actual consumption.

Reservation in turn has 2 parts: minimum and maximum. The minimum is guaranteed and the maximum is the limit that the resource group can go. Actual consumption is a value within this range.

All these counters are grouped by their respective resource group, because each process running on ESXi belongs to one these four top-level resource group:

- System (host/system resource pool)
- IO Filter (host/iofilter resource pool)
- VIM (host/vim resource pool). This includes hostd, vpxa, etc.
- User (host/user resource pool)

All the running VMs are children of the User resource pool. This includes the VM overhead as it's part of the VM.

## Reservation

This is more of a property than a metric, as it does not change often. The formula is `Overhead = CPU Total Capacity - CPU Capacity Available to VMs`.

Where capacity available to VMs is the capacity reserved by and available for VMs.

Since it is just a reservation (allocation), its not included in the calculation of the parent cluster usable capacity.

![VMKernel overhead](2.6.2-fig-1.png)

If you are curious about the actual values, they sort of map to the actual size of the ESXi. Based on a sample of almost 400 ESXi in production environment, here is what I got. By far the majority of the value is 6-10 GHz.

![Overhead graph](2.6.2-fig-2.png)

Their values tend to be stable over days, although from time to time I see fluctuating counters. I’m unsure why they are fluctuating so frequently as it’s a reservation, so if you know let me know. The following chart shows both the fluctuating pattern and steady pattern (most common). They are from 2 ESXi hosts.

![Overhead fluctuation](2.6.2-fig-3.png)

## Consumption

What if you want to know the actual consumption? vCenter provides visibility into the VMkernel utilization. It's available under **System**, and you can get CPU and memory usage and reservation (allocation).

![System Metrics](2.6.2-fig-4.png)

You need to select host/iofilters, host/system, and host/vim.

Everything else runs under one of the three resource pools. You can plot their values in vCenter by stacking up their values, as shown below.

![ESXi System Graph](2.6.2-fig-5.png)

For memory, choose the metric Resource Memory Consumed. Stack them, and you see something like this. The system part typically dwarf the other 2 resources.

![Host system metrics](2.6.2-fig-9.png)

Do not take the value from **Memory \\ VMkernel consumed** counter. That’s only the system resource. You can verify by plotting this and compare against host/system resource. You will get identical charts.

![VMKernel Consumed](2.6.2-fig-10.png)

The above is for one ESXi Host. If you have many and want to see all the values in one go, create a view in vRealize Operations. Here is a sample from ~400 ESXi hosts, where I shot the top 7 from highest System usage.

![ESXi System Usage Table](2.6.2-fig-6.png)

The bottom two rows show the summary. The first summary is the average among all the hosts, while the last row is the highest value.

BTW, a high CPU Ready in system group in esxtop is perfectly normal as this group includes idle threads.

![High CPU Ready in System](2.6.2-fig-7.png)

You can see from the following that Idle accumulates 2400% CPU Ready:

![Idle High CPU Ready](2.6.2-fig-8.png)