---
title: "3. Plan vs Reality"
date: 2021-06-14T12:55:25+10:00
draft: false
weight: 30
aliases: ['/operations-management/chapter-4-configuration-management/1.4.3-plan-vs-reality']
---

The actual configurations you have in production should reflect your current architecture standard. Your architecture or standard may change over the years, but it should be documented. You then use the configuration dashboards to compare the reality versus intended standard. If they differ, one of them is wrong and needs to be addressed.

Standards make operations simpler and are often required for compliance. For example, you have a standard for VMware Tools versions, and you choose one version as your standard, but allow 2 other versions across your environment as it takes time to upgrade. You can create a pie chart showing the distribution of VMware Tools version. Each slice in the pie chart counts the occurrence of a particular value. You should expect to see only three slices. If You are seeing more than three, then the reality differs to your standard.
