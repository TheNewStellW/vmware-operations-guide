---
title: "Chapter 7 - Availability Management"
date: 2021-06-11T11:31:22+10:00
draft: false
chapter: true
aliases: ['/operations-management/chapter-7-availability-management']
---

### Chapter 7

# Availability Management

[Availability](https://en.wikipedia.org/wiki/High_availability) is a characteristic of a system which aims to ensure an agreed level of operational performance, usually uptime. We strive towards achieving higher uptime or higher availability of the solution, which can be business service or infrastructure service.

High availability is hard to architect. Each additional nine (as in going up from 99.999% to 99.9999% availability) often requires a different architecture. For non-technical folks, it's easy to see "hey it's just another decimal" when viewed from availability angle. The correct view should be from the non-availability angle, where the downtime window actually goes down by 1000%. Instead of having 100 minutes of downtime you only have 1 minute, so suddenly every second matters. For deeper reading, review [this](https://blog.ipspace.net/2020/12/50-shades-high-availability.html) by [Ivan Pepelnjak](https://www.ipspace.net/About_Ivan_Pepelnjak).

{{% children %}}
