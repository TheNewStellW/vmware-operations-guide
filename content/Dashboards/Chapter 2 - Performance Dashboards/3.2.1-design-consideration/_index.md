---
title: "1. Design Consideration"
date: 2021-06-15T14:51:30+10:00
draft: false
weight: 10
---

Performance Management dashboards share the same design principles. They are intentionally designed to be similar, as it will be confusing if each dashboard looks totally different from one another, considering they have the same objective.

The first thing to check when a VM has a performance problem is if other VMs have the same problem. If the problem is widespread the root cause is not with the VM. Hence it's important to see the big picture, before diving into a particular area in your SDDC. 

At the infrastructure layer, we care whether it serves everyone well. Make sure that there is no contention for resource among all the VMs in the platform. Only when the infrastructure is clear from contention can we troubleshoot a particular VM. If the infrastructure is having a hard time serving majority of the VMs, there is no point troubleshooting a particular VM. Notice all the previous sentences are about the VM. Yes, the infrastructure counters are not that relevant.

For objects where there are many counters, I split the dashboard into 2: contention and utilization. This keeps the dashboard simple, while emphasizing the concept of contention as the primary counter for performance.

The dashboard is designed "top down". It has 2 sections: summary and detail.
- The summary section is typically placed at the top of the dashboard. It gives the big picture. 
- The detail section is placed below the summary section. It lets you drill down into a specific object. For example, if it's a VM performance, you can get the detail performance of a specific VM. 

This detail section is also designed with quick context switch, as you may want to check the performance of multiple objects during performance troubleshooting. Take for example VM performance. The dashboard gives you all the VM-specific information and allows you to see the KPIs without changing screens. You can move from one VM to another and view the details without opening multiple windows.

UI wise, the dashboard uses progressive disclosure to minimize information overload and ensure the webpage loads fast. On the other hand, so long your browser session remains, it remembers your last selection.

You may notice that many of the performance dashboards and the capacity dashboards share similar layout. The reason is there is commonality in both pillars of operations. 