---
title: "1. Roles & Responsibilities"
date: 2021-06-16T22:45:58+10:00
draft: false
weight: 10
---

We covered the various roles required in cloud operations earlier, so let's dive into the roles specific for DaaS operations. Depending on the size & complexity of the VDI architecture, there can be many roles involved in operations.

| Role | Responsibility |
| --- | --- |
| **Level 1 Ops** | **Reactive**: respond to user complaint or alerts and perform simple remediation. Typically does not require reading logs. **Proactive** health check of the environment, as part of the SOP. Look at availability, performance and compliance.| 
| **Level 2 Ops** | **Reactive**: Perform advance troubleshooting. Likely require reading logs and Windows Events. **Proactive**: Analyse the overall environment, especially from performance and availability. Should do this at least once a week. |
| **Capacity** | Review the pool and farm capacity. Depending on the volatility, this could be done monthly.|
| **Compliance** | Set the compliance settings to agreed internal and industry standard. Verify that non-compliance alert was addressed timely and correctly by the operations team. Report the comp. |
| **IT Management** | Weekly report, focusing on the overall health and not individual users or pools. Monthly presentation and review, supported for live dashboard for an interactive discussion. |

The responsibilities cover the 7 pillar of operations. As Horizon requires vSphere, Microsoft ADAM Database, Microsoft Active Directory (MS AD) and other components, you need to manage all of them as a system.

| Pillar |   |
| -------| ---|
| **Availability** | Any desktops that are in bad state? Any availability problems in vSAN, NSX, vSphere, DC network switches, WAN network? |
| **Performance** | There are 2 sides of performance: a single user and the whole DaaS.<br />A single user troubleshooting may require going deep into the user’s desktop and user’s specific settings (e.g. MS AD group policy, MS Outlook plugins). Tools such as [SysInternals](https://docs.microsoft.com/en-us/sysinternals/) and Windows Event analyser can come in handy. This may involve disable settings as you eliminate possibilities.<br />DaaS-wide troubleshooting requires going broad into all the users (affected and not affected with the issue). It requires analyses across the stacks. You likely need various adapters of vRealize Operations and Log Insights, and develop your own custom dashboard that’s specific to your architecture. |
| **Capacity** | There are many parts of DaaS capacity.<br />The 1st part is the desktop, pools and farms. Make sure the desktop is rightsized, and the pools & farms can meet the load.<br />The 2nd part is Horizon servers and infrastructure. This covers Horizon servers (Connection Servers, Universal Access Gateway and App Volume Managers), non Horizon servers (Microsoft SQL Servers, MS AD, Load Balancers, AV servers, single sign on servers, security servers).<br />The 3rd part is the network. This excludes the data center network, but includes the client network and the Wide Area Network (WAN). The client network can be in the form of shared office, café or mall, airport or home. The WAN can be a mixed of mobile, wireless or leased lines.<br />The 4th part is the underlying SDDC where the EUC is running. |
| **Cost** | VDI has a direct comparison to a physical laptop or desktop. One reason why VDI does not dominate End User Computing market is their cost is comparable with laptop or desktop, and laptop provides the offline capability. One way to keep the cost down is the consolidation ratio. How many desktops or users can you pack into a single cluster? |
| **Compliance** | Different users may require different compliance. How do you prove that you’ve delivered continuous compliance? |
| **Configuration** | Any misconfiguration, outdated configuration, incompatible configuration or suboptimal configuration? This needs to be checked across the entire stack, especially the lower stack as problem in a stack will impact the stack above it.|

From the brief summary above, you can see that VDI operations management is complex. It's much more than waiting for user to complain and then troubleshoot a single desktop.