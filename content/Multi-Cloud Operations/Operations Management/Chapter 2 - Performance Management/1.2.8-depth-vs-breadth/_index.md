---
title: "8. Depth vs Breadth"
date: 2021-06-13T15:30:22+10:00
draft: false
weight: 80
aliases: ['/operations-management/chapter-2-performance-management/1.2.8-depth-vs-breadth']
---

What do you notice from the following screenshot?

![CPU Contention example](1.2.8-fig-1.png)

Notice the Maximum is >10x higher than the average. The average is also very stable relative to the maximum. It did not move even though the maximum became worse. Once the Cluster is unable to cope, you'd see a pattern like this. Almost all VMs can be served, but 1-2 were not served well. The maximum is high because there is always one VM that wasn't served.

***Be careful*** when you look at counters at parent object such as cluster and datastore, as average is the default counter used in aggregation. Review the following cluster level chart. Do you notice a problem?

![Cluster level chart](1.2.8-fig-2.png)

That's right. No performance issue at all in the last 7 days. The cluster is doing well.

This cluster runs more than 100 VMs. What you see above is the average experience of all these VMs, aggregated at cluster level. If there is only a few VMs having a problem, but the majority are not, the above fails to show it.

What you need is a cluster-level metric that tracks if any of the VMs is having contention. We have that, and the result is telling.

![Worst VM in cluster chart](1.2.8-fig-3.png)

Same pattern, but the scale is 6000%!

The following diagram explains how such thing can happen.

![Disk group latency chart](1.2.8-fig-4.png)

The above charts show 6 objects that have varying disk latency. The thick red line shows that the worst latency among the 6 objects varies over time.

Plotting the maximum among all the 6 objects, and taking the average, give us two different results as shown below:

![SLA and metrics](1.2.8-fig-5.png)

The chart shows that it is possible that the average is still well below threshold, but one or more objects was affected. The average number is stable.
Only when the cluster is unable to serve ~50% of its VMs, will the average number become high. Therefore, the average is a poor roll up technique. It's a lagging indicator.

Proactive monitoring requires insights from more than one angle. When you hear that a VM is hit by a performance problem, your next questions are naturally:

- How bad is it? You want to gauge the depth of the problem. The severity also may provide a clue to the root cause.
- How long did the problem last? Is there any pattern?
- How many VMs are affected? Who else are affected? You want to gauge the breadth of the problem.

Notice you did not ask "What's the _average_ performance?". Obviously, average is too late in this case. By the time the average performance is bad, likely half the population is affected.

The answer to the 3rd question impacts the course of troubleshooting. Is the incident isolated or widespread? If it's isolated, then you will look at the affected object more closely. If it's a widespread problem then you'll look at common areas (e.g. cluster, datastore, resource pool, host) that are shared among the affected VMs.

When calculating the breadth of the problem, you need to use a stringent threshold. Without this, you will not be able to catch values that are just below the threshold. On the other hand, if you set it too low, you will get a lot of early warning.

![Example metrics](1.2.8-fig-6.png)
