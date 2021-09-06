---
title: "2. End-to-End Capacity"
date: 2021-06-14T10:46:13+10:00
draft: false
weight: 20
---

Capacity Management becomes easier if you begin with the planning stage. This is where you define your offering, setting the price and performance expectation. Without expectation being set, your customers will demand high performance that you cannot meet with your current infrastructure. 

Capacity Management requires an end-to-end plan and adjustment, because at the end of the day it is about comparing the reality you face with the plan you set. Good or bad is relative to your plan. If you plan for no overcommit because performance is absolute and budget is not an issue, then you'll never run out of capacity. In other cases, that could be considered bad as you could end up with a lot of wastage.

Balancing demand and supply require you to look at these 6 components below. Steps 1 and 2 are done together, and the remaining 4 steps can be done in parallel.

![Demand vs Supply](1.3.2-fig-1.png)

Unlike Performance Management, this pillar of operations does not require deep technical knowledge. Let's check your technical skills if you don't trust me.

- Can you architect a cluster where the performance matches physical?
  - Easy, just don't overcommit, or put 100% reservation for that VM.
- Can you architect a cluster that can handle monster VMs?
  - Easy, just get lots of cores per socket.
  - Easy, just get lots of core in the box.
- Can you architect with very high availability?
  - Easy, just have more HA hosts, more vSAN FTT with failure domains spread across different racks.
  - Easy, just have more HA hosts.
- Can you architect a cluster that can run lots of VMs?
  - Easy, just get lots of big hosts.
- Can you optimize the performance?
  - Sure, follow performance best practices and configure for performance.
- Can you squeeze the cost?
  - Sure, minimize the hardware and software cost, and choose the best bang for the buck. You know all the vendors and their technology. You know the pro and cons of each.

The above is not hard to do if you do it right from the start, which is why we need to begin at the planning phase. If you start from Step 6 and ignore Step 1 and 2, you will play the lead role in a [Mission Impossible](https://en.wikipedia.org/wiki/Mission:_Impossible_(film_series)) movie.