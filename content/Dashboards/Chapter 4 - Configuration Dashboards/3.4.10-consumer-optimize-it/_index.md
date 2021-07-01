---
title: "10. Consumer / Optimize It?"
date: 2021-06-15T22:13:11+10:00
draft: false
weight: 100
---

The "**Consumer / Optimize It?**" dashboard complements the main VM configuration dashboard by displaying the actual VMs, with their relevant information. It is designed for vSphere administrator and platform team, to facilitate the follow-up action with the VM owners. It is a part of 8 dashboards that check the environment for optimization opportunities.

A suboptimal configuration might not impact performance or increase complexity, but it can be more expensive.

The dashboard follows the same design consideration with the [Consumer / Correct it?](/dashboards/chapter-4-configuration-dashboards/3.4.7-consumer-correct-it/) dashboard. In fact, the 8 dashboards that form the Optimization Flow is designed as a set. You are meant to use them together as you go through the optimization review process.

## How to Use

The dashboard is just a collection of tables (List View), which can be reviewed independently. There is no flow among them.

Click the object name to navigate to the Object Summary page to view more configurations. There can be valid reasons why specific configurations are not followed. It is recommended that you discuss best practices with VMware.

VM Reservation:

- VM reservation causes a positive impact on the VM, but a negative impact on the cluster. Total reservation cannot exceed cluster capacity. This creates a suboptimal cluster as VMs do not use the entire assigned memory at the same time.
- VM reservation places a constraint on the DRS placement and HA calculation. Avoid using reservation as a means to differentiate performance SLA among all the VMs in the same cluster. It is difficult to correlate CPU Ready with CPU Reservation. A VM CPU Ready does not improve two times because you increase its CPU reservation by two times. There is no direct correlation.

Guest OS visibility:

- Since your workloads are sharing resources and are over-committed, your operations are easier if you know what is running inside. This helps with monitoring and troubleshooting, resulting in more optimal operations.
- For critical VMs, consider logging the Guest OS (e.g. Windows, Linux) to capture errors that do not surface as metrics. These errors typically appears as events in the log files, or Event database it the case of Microsoft Windows. Use Log Insight to parse Windows events into log entries that can be analyzed.

Snapshot:

- Old snapshots tend to be larger. They consume more space and have a higher chance of impacting performance.

## Points to Note

See the [Points to Note](/dashboards/chapter-4-configuration-dashboards/3.4.7-consumer-correct-it/#points-to-note) section of [Consumer / Correct it?](/dashboards/chapter-4-configuration-dashboards/3.4.7-consumer-correct-it/) dashboard. This dashboard follows the same design consideration with the dashboard, hence share the same limitations and customization idea.
