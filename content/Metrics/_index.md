---
title: "Metrics"
date: 2021-06-11T11:31:22+10:00
draft: false
weight: 40
---

Part 2 (Metrics) is a deep dive into the key metrics that you will most commonly use and should be considered a pre-requisite to Part 3. 

vRealize Operations ships with thousands of metrics and properties, covering objects in vSphere, vSAN, the Guest OS and others. If we take object by object, and document metrics by metrics, it would be both dry and confusing. Most likely you will be disappointed as it does not explain how your problems are solved.

This document begins with you. It focuses on the problems You are trying to solve when running your multi-cloud operations. It looks at all the use cases and breaks down the metrics from there, which helps you appreciate why the metrics are layered in such manner. vRealize Operations takes raw counters from the systems that are monitored, and formulates higher-level counters that meet your operational needs better.

{{% children depth="2" %}}