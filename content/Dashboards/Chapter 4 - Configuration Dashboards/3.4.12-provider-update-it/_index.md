---
title: "12. Provider / Update It?"
date: 2021-06-15T22:21:12+10:00
draft: false
weight: 120
---

The "**Provider \ Update It?**" dashboard complements the main vSphere configuration dashboards by displaying the actual vSphere objects, with their relevant information. It is designed for vSphere administrator and platform team. It is a part of 8 dashboards that check the environment for optimization opportunities. 

As part of operations best practices, keep the infrastructure up to date. Running outdated components that are too far behind the latest version, can cause support problems or upgrade problems. It is common that the fix for the problem is only available in the later versions. Outdated hardware can also result in higher operating costs. Outdated hardware might cost more data center footprint, such as rack space, cooling, and UPS. Refreshing your technology and consolidation are two common techniques to optimize cost.

The dashboard follows the same design consideration with the "Consumer \ Correct it?" dashboard. In fact, the 8 dashboards that form the Optimization Flow is designed as a set. You are meant to use them together as you go through the optimization review process. 

## How to Use

The dashboard is just a collection of tables (List View), which can be reviewed independently. There is no flow among them.

Click the object name to navigate to the Object Summary page to view more configurations. There can be valid reasons why specific configurations are not followed. It is recommended that you discuss best practices with VMware.

About the outdated vSphere components
- It lists all the vCenter Server that are not 6.7 or 7.0. 
- It lists all the ESXi Host that are not 6.5, 6.7 or 7.0
- It lists all the vSAN ESXi Host that are not 6.7 or 7.0. A more stringent filter is applied for vSAN due to relatively higher maturity in the latest release. Specifically from vRealize Operations and Log Insight, there are more counters, properties and events that improve monitoring and troubleshooting. 
- It lists all the vSphere Distributed Switch, regardless of version. 
- You should tailor the filter to fit your operational needs.

About Outdated Server BIOS
- It lists all the ESXi regardless of the BIOS version. Edit the widget and tailor the filter to fit your operational needs.

Other than customizing the existing widgets, consider adding the following checks. 
- ESXi hosts with outdated hardware, using a filter based on your environment. 
- ESXi hosts that are no longer on warranty. Create a custom property to capture the end of warranty. 
- Physical storage arrays with outdated firmware, model and expiring warranty expire. 
- Physical network switch with outdated OS version and hardware model

Note that the last 2 items above requires you to install relevant management pack.

## Points to Note

See the Points to Note section of "Consumer \ Correct it?" dashboard. This dashboard follows the same design consideration with the dashboard, hence share the same limitations and customization idea.