---
title: "1. A Day In The Life of a Cloud Admin"
date: 2021-06-11T11:31:22+10:00
draft: false
weight: 10
---

To understand what Performance actually is, it is always good to begin with the customer. As shared earlier, what you bought from your vendor is SDDC, but what you sell to your customers is IaaS. We have seen this in almost all customers. Whether the Application Team or VM Owner pays for the service with a chargeback model or not, it is a service. VM Owners no longer own, hence care, about the underlying infrastructure.

Here is a common story often told in the virtualization community, which will resonate with you as an IaaS provider.

A VM Owner complains to you that her VM is slow. It was not slow yesterday. Her application architect and lead developer have verified that:

- The VM CPU and RAM utilization did not increase and are within a healthy range.
- The application team has verified that CPU Run Queue is also in the healthy range.
- The disk latency is good. It is below 5 milliseconds.
- There are no network packets loss.
- No change in the application settings. In fact, the application has not had any changes in the past 1 month.
- No recent patches were installed into Windows.
- There was no reboot. It has been running fine for weeks.

She said your VMware environment is a shared environment, and perhaps an increase in the number of VMs and an increase in the workload of other VMs are straining your IaaS.

She also said that her other VM, which was [P2V](https://en.wikipedia.org/wiki/Disaster_recovery) recently, was performing much faster in physical.

You are right. She is saying it's your fault. 

What do you do? 

It is certainly a difficult situation to be in. You oversee more than 10,000 VMs. You have successfully consolidated them into 500 ESXi Hosts, saving the company 9500 servers, not to mention a lot of money. You built your reputation during the process, so this is not just a matter of her VM not performing. Your reputation is at stake here. 

You also recall that your team has been adding new VMs regularly in the past several months so she could be right. But why did it happen today, and not say a few days ago?