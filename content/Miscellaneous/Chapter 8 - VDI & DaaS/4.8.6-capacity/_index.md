---
title: "6. Capacity"
date: 2021-06-16T23:23:42+10:00
draft: false
weight: 60
---

{{% notice info %}}
This page is still in draft.
{{% /notice %}}

Horizon consists of different components, each having their own capacity model.

## Users

Sizing what a user needs is challenging as each users work differently. Corporate office hours do not apply as users may even work on the weekends.

![Usage timeline](4.8.6-fig-1.png)

## RDS Farm

| Number of Sessions Remaining |     |
|------------------------------|-----|

VDI Pool has Utilization (GHz), which is the total utilization not average.

Total - Unavailable - Bad State = Usable Capacity

- Unavailable (nothing wrong. Intentional or will fix by itself)  
  - = Provisioned + In progress + Already used + Provisioning + Customizing + Deleting + Waiting for Agent + Maintenance mode + Startup + Agent needs reboot
- Bad state (something wrong. Need manual intervention)  
  - = Configuration error + Provisioning error + Error + Unknown + Protocol failure + Domain failure + Agent disabled + Agent unreachable + Invalid IP

Usable Capacity consists of

- Used = Connected + Disconnected + Unassigned user connected + Unassigned user disconnected
- Available = Available