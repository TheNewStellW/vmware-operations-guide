---
title: "7. Consumer \\ Correct It?"
date: 2021-06-15T21:49:56+10:00
draft: true
weight: 70
---

The “**Consumer \ Correct It?**” dashboard complements the main VM configuration dashboard by displaying the actual VMs, with their relevant information. It is designed for vSphere administrator and platform team, to facilitate the follow-up action with the VM owners. It is a part of 8 dashboards that check the environment for optimization opportunities.

The dashboard is designed to focus on VMs that need attention. A list is used to keep it simple, and show actual objects. The list is easy to be tailored by filter and custom group. The list can also be exported for an offline discussion.

It’s also designed to be extendable, reflecting the reality that different customers will have a different set of settings to verify. Since the dashboard layout is just a collection of tables (View List), you can extend it by simply adding more tables. Simply add more View List widget to check the VM configuration that your operations require.

## How to Use

The dashboard is just a collection of tables (List View), which can be reviewed independently. There is no flow among them.

Click the object name to navigate to the Object Summary page to view more configurations. There can be valid reasons why specific configurations are not followed. It is recommended that you discuss best practices with VMware.

About the Tools tables
- Using VMware Tools has multiple benefits. For the list of benefits, refer to [KB 340](https://kb.vmware.com/s/article/340).
- vRealize Operations uses VMware Tools to retrieve Guest OS metrics. Without this, right-sizing VM memory can be inaccurate, because the hypervisor metrics (VM Memory Consumed and VM Memory Active) are not designed to measure Windows or Linux memory utilization. ESXi VMkernel does not have visibility into the Guest OS for security reasons.
- Independent software vendor (ISV) support is the most common reason that VMware Tools is not installed. The ISV vendor may claim that no additional software is installed in their appliance unless they have certified it. For more information about VMware Tools, see the [VMware Tools documentation](https://docs.vmware.com/en/VMware-Tools/index.html).
- If VMware Tools is installed, there might be reasons why the application team disables it. The Infrastructure team should inform and educate their application team, and document the technical recommendations on why VMware Tools is strongly recommended to run all the time.

About the Memory and CPU Limits table
- It is recommended that you do not use memory and CPU limits as it can result in unpredictable performance. The Guest OS is not aware of this restriction as it is at the hypervisor level. It is recommended that you shrink the VM instead.

About No Guest OS counters table
- There is no visibility into the Guest OS performance counters because the requirements are not met. Memory counter is especially important as VM Consumed and the VM Active are not replacements for Guest OS counters. See this [KB](https://kb.vmware.com/s/article/55675) for details. 

About the Old Snapshot table
- Ensure that the snapshot is removed within one day after the change request. If not, it might result in a large snapshot and impact the performance of the VM. 

Points to Note
- Add a banner summary at the top of this dashboard, so that you can verify if there is an incorrect confirmation. Add a scoreboard and select the World object and then collapse all the tables below. Create a super metric for each summary and apply it to the World object.
- In a very large environment, create a filter for this dashboard to enable you to focus on a segment of the environment. Group it by a class of service such as, Gold, silver, and bronze. Default the selection to Gold, your most important environment. In this way, your monitoring is not cluttered with less critical workloads.
- There are other VM configuration that maybe relevant to your environment. Review the list of VM settings that you may want to add to this dashboard here. 
- For a quick context, add a property widget that lists the selected VM properties. In this way you can check the property of your interest without the need to leave the screen. Note that multiple View List widget can drive the same property widget, so you do not have to create 1 property widget for each View List. 
- If your operations required it, add list VMs that do not have these three key performance counters: CPU Run Queue, CPU Context Switch, and Disk Queue Length. 