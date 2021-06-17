---
title: "1. Part 1 - Operations Management"
date: 2021-06-16T14:09:36+10:00
draft: false
weight: 10
---

## Performance SLA

You should exclude CPU Co-Stop from Performance SLA because the reason for CoStop could be the VM itself. IaaS SLA should not measure problems beyond your control. Read this for details.

You should exclude CPU Contention from Performance SLA because its value can go as high as 37.5% without the application noticing any degradation. You can login to Windows or Linux and feel it’s responsive. Read this for details.

## “Good” Advice

The problem with the advice is it assumes utilization as the metric for performance. You want to drive by contention, while aiming to maximize utilization.