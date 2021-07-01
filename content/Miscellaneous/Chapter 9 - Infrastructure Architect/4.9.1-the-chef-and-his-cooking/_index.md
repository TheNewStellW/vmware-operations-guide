---
title: "1. The Chef and His Cooking"
date: 2021-06-16T23:41:14+10:00
draft: false
weight: 10
---

I see myself as an Infrastructure Architect. After almost a decade in application world, I entered the weird and wonderful world of enterprise IT infrastructure, starting as a presales with Sun Microsystems in 2003. My job titles, roles and departments have changed many times since then, but fundamentally it's about architecting enterprise infrastructure. My official role is a Product Manager for an operations management product, but I still see myself as the engineer doing the performance troubleshooting and reading logs.

## The Chef and His Cooking

![Stock photo of chef](4.9.1-fig-1.jpg)

This is a story of the life of a VMware Admin that I shared as an impromptu presentation at our VMUG Singapore back in 2014 and it still resonates until today.

The restaurant business provides a good analogy to our IaaS business. We, the infrastructure architect, are the Chef. In that end-user environment where you work, you are the expert in producing what your customers want. You architect and design a solid platform, where your customers can confidently run their VMs. If there is an issue, you often get involved, restoring their confidence in your creation. You are seen as the VMware expert, or the virtualization expert. Yes, you may engage VMware Professional Services or Support, but they are not employees of you company. You are the employee. As far as your customers concern, the buck stops at you.

You do not sell hardware nor software; you charge your customers per VM. In fact, to ensure that your customers order the right kind of VM, you need to charge per vCPU, per vRAM and per vDisk. The chargeback model is something that I very rarely see discussed. We tend to stay in technical discussions. We need to realise we are no longer just a System Builder. We are Service Provider. By not extending our circle of influence into how App Teams should pay for our service, we created the issue we have today (Oversized VMs, dormant VMs, VM sprawl). We need to "step out from the kitchen" from time to time. We need to be like the Chef who steps out into the dining area, building relationships with his customers, explaining the reason behind his cooking.

As the Architect, we are the best person to determine how much to charge for these. We built this environment. We know the costs, and we know the capacity. Not convinced? Put it this way, would you rather someone else determine how much your creation is worth?

We all know that IT exists because of Business. It starts with the Business. Some of the issues we have are caused by unsuitable chargeback models and incorrect Service Tiering. The VM in Tier 1 (mission critical) platform cannot cost the same as the VM in Tier 3 (non-production). I'd make sure there is distinct difference in quality between Tier 1, Tier 2 and Tier 3, so it's easy for business to choose. Need a good example? Review this.

Using the restaurant analogy, say you cook fried rice. It's your dish. You need to determine the price of the fried rice. You also need to be able to justify why you have normal fried rice and special fried rice, and why the special one costs a lot more for the same amount of food.

To me, the Chargeback model and the Service Tiering serve as Key Drivers to our Architecture. I will not consider my architecture complete unless I include these 2 in my design. We are architecting to meet the business requirements, which are "defined" in the chargeback model (e.g. the business wants a $100 VM per month, not a $100K VM per month), and service tiering (e.g. the business wants 99.999% and 3% CPU Contention).

As shared, I see a chance for us to **step up** and **step out**.

- Step out of the kitchen and network with your customers (the Application team). Educate and fix the problem at the source.
- Step up from pure IT architecture to business architecture. Architect your pricing strategy and service tiering.

The good thing about pricing is... your benchmark is already set.

Azure, AWS, Google, and many Service Providers have already set the benchmark. Your private cloud cannot be too far from it. Too low and you will likely make a loss (it's almost impossible to beat their efficiency). Too high and you will get a complain. Another source of benchmark is to consider what it would cost to run the same applications on physical servers

If you are pricing your VDI, the cost of a PC sets your benchmark. You can be higher, but not by a huge gap. A PC costs $800 with Windows + 3 year warranty + 17" monitor. Add your IT Desktop cost, and you meet your benchmark.

I hope you enjoyed it and do share your life story!