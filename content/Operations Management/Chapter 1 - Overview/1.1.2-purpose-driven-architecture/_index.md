---
title: "2. Purpose-Driven Architecture"
date: 2021-06-11T11:31:22+10:00
draft: true
toc: true
---

When you architect IaaS or Desktop as a Service (DaaS), what goals do you have in mind? I don’t mean the design considerations, such as availability and performance best practices. I mean the business result that your architecture has to deliver, viewed from the people who paid for the architecture. 
Logically, the answer depends on what is being sold. You can either sell application or infrastructure, broadly speaking.

For applications, the following tables shows the variety of services. 

![Common 'As a Service' offerings](1.1.2-fig-1.png?width=60pc&classes=shadow,border)

In the case of DaaS, the goal is to ensure End Users are getting a quality desktop experience while keeping the price per user low. We will discuss more on this here.

Let’s dive into the IaaS business. There are three variants of IaaS. Each sells a different item, hence the goal can’t be identical.

![](1.1.2-fig-2.png?width=60pc&classes=shadow,border)

![](1.1.2-fig-3.png?classes=shadow,border)

The most popular variant of IaaS is VM as a Service. In this variant, the business goal is to ensure the application and VMs (VM) are running **well yet cost effective.**

![](1.1.2-fig-4.png?width=50pc&classes=shadow,border)
 
The cost part is easy to quantify. You know what you spend on hardware, software, services and salary. The “well” in running well is the hard part as there is a big unknown.

Let’s use IaaS as the example. Say you are architecting for 10K VMs in 2 data centers. You envisage 2K VM in the first month, 5K VM in the first half year, and eventually to 10K within the first year. Do you know the basic info about each of these 10K VMs, so that you can architect an infrastructure to serve them well?

- How big are they? What are their vCPU, RAM, Disk configuration?
- How intense are they? CPU utilization, RAM utilization, disk IOPS, network throughput?
- What are their workload patterns? Daily, weekly, monthly, no pattern, etc.

The answer is obviously no. Even application teams do not know as some of the applications may not be developed yet. Their vendors may not know either as the usage is not yet known.

Promising that the SDDC will serve all 10K VMs well is akin to promising the highway you architect will serve all the cars, buses and motorcycles well, when we can’t predict how many they are and how often they will use it. We will cover this more in the Performance section. 

So how can we promise that your IaaS will serve your customers well?

We can by using the price/performance. The principle you share with your customers is the common sense used in all service industries:

You want it cheap; it won't be fast. You want it fast; it won't be cheap.

This is where the Class of Service and the associated Service Level Agreements come in. The highest class of service provides the best uptime and performance but comes at a price. All these attributes are well defined in the SLA, leaving no room for ambiguity. The contract is not subject to interpretation. You define all the key metrics up front, assuring your customers that you are confident of delivering as promised.

You then architect your IaaS to deliver the above classes of service. The class of service becomes your business offering. With that, you are ready to begin with the end in mind.