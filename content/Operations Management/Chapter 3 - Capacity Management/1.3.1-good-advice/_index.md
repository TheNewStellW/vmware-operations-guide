---
title: '1. "Good" Advice'
date: 2021-06-14T10:43:13+10:00
draft: false
weight: 10
---

Can you figure out why the following statements are wrong? They are all well-meaning advice on the topic of Capacity Management. We're sure you have heard them, or even given them.

Regarding Cluster RAM:

- We recommend 1:2 overcommit ratio between physical RAM and virtual RAM. Going above this is risky.
- Memory Usage on most of your clusters is high, around 90%. You should aim for 60% as you need to consider HA.
- Memory Active should not exceed 50-60%. You need a buffer between Active Memory and Consumed Memory.
- Memory should be running at high state on each host.

Regarding Cluster CPU:

- CPU Ratio on cluster "XYZ" is high at 1:5, because it is an important cluster.
- The rest of all your clusters' overcommit ratio looks good as they are around 1:3. This gives you some buffer for spikes and HA.
- Keep the over commitment ratio to 1:4 for Tier 3 workload as they are not mission critical.
- CPU usage is around 70% on cluster "ABC". Since they are UAT servers, don't worry. You should get worried only when they reach 85%.
- The rest of your cluster's CPU utilization is around 25%. This is good! You have plenty of capacity left.

The scope of the statements above is obviously about a VMware vSphere Cluster. From a capacity monitoring point of view, cluster is the smallest logical building block, due to HA and DRS. So it is correct to assume that we do capacity planning at Cluster level, and not at Host level or Data Center level.

Can you figure out where the mistakes are?

You should notice a trend by now. They have something in common. If not, answer at the [Part 4: Quiz Answers](/miscellaneous/chapter-1-quiz-answers/4.1.1-part-1-operations-management/)!