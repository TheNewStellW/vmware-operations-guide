---
title: "1. Design Considerations"
date: 2021-06-15T21:16:57+10:00
draft: false
weight: 10
---

Configuration Management dashboards share the same design principles. They show the configuration that needs attention first, before showing overall configuration. The idea is to drive action towards optimizing configuration.

The overall layout is designed to balance ease of use, performance (loading time of the dashboard page) and completeness of configuration check. As a result, not all configuration settings are shown. Lack of screen real estate is another consideration behind the design. 

In some dashboards, there are simply too many configuration items to check than the screen real estate provides. If you have a larger screen, add the additional check as you deem fit, or add legends to the pie-charts. For a start, see the list of settings that you may want to check here. 

## Empty or Exist

In configuration check, we can encounter a need to check for exception. This is where the Exist or Not Exist check and Empty and Not Empty check can come in handy.
 
Some ideas are:
- Check for standalone ESXi. It will have no parent cluster
- Check for missing Telegraf agent in critical VM

Anything else? Let's collaborate to enhance the configuration dashboards!