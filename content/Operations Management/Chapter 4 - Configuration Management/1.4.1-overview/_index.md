---
title: "1. Overview"
date: 2021-06-14T12:50:57+10:00
draft: true
weight: 10
---

As an operation management software, vRealize Operations focuses on the impact to day-to-day operations a product has, rather than the feature of the product itself. Products under monitoring, such as vSphere and vSAN, can have features that are related, but have different impact to operations. Take for example, vSphere provides Limit, Reservation and Share for VM. As feature, they are closely related, appear in the same dialog box in vCenter client UI and should be mastered as one. However, they impact operations differently. The following table describes that in more details.

![](1.4.1-fig-1.png)

vRealize Operations takes the principle that there are different impacts to operations, and applies a methodology for looking at configuration. It does not group the settings by features or objects. Rather, it begins with the impact in mind, and prioritize what can be done. 