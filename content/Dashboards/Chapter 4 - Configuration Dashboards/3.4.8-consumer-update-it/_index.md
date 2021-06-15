---
title: "8. Consumer \\ Update It?"
date: 2021-06-15T22:05:55+10:00
draft: true
weight: 80
---

The “**Consumer \ Update It?**” dashboard complements the main VM configuration dashboard by displaying the actual VMs, with their relevant information. It is designed for vSphere administrator and platform team, to facilitate the follow-up action with the VM owners. It is a part of 8 dashboards that check the environment for optimization opportunities. 

The dashboard follows the same design consideration with the “Consumer \ Correct it?” dashboard. In fact, the 8 dashboards that form the Optimization Flow is designed as a set. You are meant to use them together as you go through the optimization review process. 

## How to Use

The dashboard is just a collection of tables (List View), which can be reviewed independently. There is no flow among them.

Click the object name to navigate to the Object Summary page to view more configurations. There can be valid reasons why specific configurations are not followed. It is recommended that you discuss best practices with VMware.

About Outdated Tools table
- It lists all the VMware Tools version that is still supported. You should tailor the filter to fit your operational needs. 

About Outdated VM Hardware
- It lists all the VM vmx versions that are not 13, 14, 15, or 16. You should tailor the filter to fit your operational needs.

About the outdated Windows and Red Hat
- It lists all Microsoft Windows client version that are not version 10
- It lists all Microsoft Windows server version that are not version 2016 and 2019.
- It lists all Red Hat Enterprise Linux version that are not version 7 or 8.
- If you run other Operating Systems like Ubuntu, clone the widget. Or repurpose the widget if you don’t run RHEL and MS Windows

## Points to Note

See the Points to Note section of “Consumer \ Correct it?” dashboard. This dashboard follows the same design consideration with the dashboard, hence share the same limitations and customization idea. 