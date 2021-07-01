---
title: "1. Gap Analysis"
date: 2021-06-16T15:01:44+10:00
draft: false
weight: 10
---

For each issue/question below, the ideal answer is provided in light grey so you know what it should be. Replace it with your own so the gap can be addressed.

## Performance

| Business Question | Ideal Answer |
|---|---|
| Do your business units (your customers) blame the infrastructure first? If yes, why? | Business Units (Apps Team) do not blame us because there is transparency on how each of their VM is being served. |
| Is that because you have not defined the performance they can expect? | There is a formal SLA on both Performance and Availability, which is applied to each VM based on the class of service they buy. Both SLA are clearly defined and measured every 5 minutes. For Performance SLA, we check CPU, RAM, Disk and network. |
| How do you know when your IaaS is **not** serving the VM well? Do you depend on complaint to know if your IaaS isn't performing? | Our operations do not depend on complain. SLA enables us to be proactive and provide early warning to CIO. We track the threshold and act before complaint is made.|
| How can you move toward proactive operations? What metrics do you use to measure IaaS performance? |  |
| Does Help Desk provide a good first level defense? Or does it simply pass through to the next level? | Help Desk uses the SLA, with a custom dashboard given to them. They encourage App Team to self-service as the same dashboard is provided. Our operations is VM-centric and application-centric, even though we are the infrastructure team.| Yes. We maximize utilization without compromising performance. Performance is at the heart of our capacity management. We also consider concentration risk, and do not exceed the limit set in business continuity policy. 

## Capacity / Hardware Justification

| Business Question | Ideal Answer |
| --- | --- |
| Can you justify new infrastructure when utilization is _not yet high_? This is not referring to additional money that comes with a new project, this is referring to existing clusters/storage. | Yes. We maximize utilization without compromising performance. Performance is at the heart of our capacity management. We also consider concentration risk, and do not exceed the limit set in business continuity policy. |
| It takes time to buy hardware. Do you have an early warning in place? Other than utilization, what other metrics do you consider? | As it takes time to buy hardware, Performance SLA breach serves as early warning as they happen before VM Owner complains. |

## VM Right-Sizing

| Business Question | Ideal Answer |
| --- | --- |
| Do you have many over-provisioned VMs? Do you know how much to reclaim, and from which VMs? | No. We do not interfere with application team business. They are paying for each vCPU, vRAM and vDisk. |
| Are the VM Owners convinced on your recommendation? If not, why? | There is progressive pricing and a discount for a small VM. These 2 factors make larger VMs much more expensive, hence encouraging right sizing right from the start. If an LOB wants to waste their money, that's certainly their right. We do highlight how much they can save if they right-size |
| How do you right-size without impacting performance? | We may advise, but never dictate VM size, as it all depends on the applications. |

## Configuration

| Business Question | Ideal Answer |
| --- | --- |
| Do you know who changed what in your infrastructure? Does the Auditor ask for such information? | Yes. We mine vCenter logs, tasks and events. We provide the Auditor with a custom portal using Log Insight.|
| Do you need to implement the vSphere Hardening Guide? | Yes. We implement the vSphere Hardening Guide. The compliance dashboard is made available for customers to see, demonstrating transparency in our IaaS platform.|
| Do you have to comply with industry specific security (e.g. PCI DSS, HIPAA)? |  |

## Troubleshooting

| Business Question | Ideal Answer |
| --- | --- |
| On issue that spans multiple team, do you use a set of common tools to perform joint analysis? Or each team use their own, working in silo?| Yes. The Storage and Network teams have custom access to both vCenter and vRealize. For vRealize Operations and Log Insight, we created custom dashboards so they are not overwhelmed with unnecessary information. |
| Does Network Team and Storage Team have good visibility into the VMware environment? Do you have good visibility into Network and Storage? | Yes. Storage, Network, and Compute have access to one another's tools. We use the True Visibility Suite to correlate with Network and Storage, so everyone is looking at the same information. |
| As part of Root Cause Analysis, do you setup alert so issue can be detected faster if it happens again? | Yes. Alerts are mandatory as exit criteria in RCA. |

## Availability

| Business Question | Ideal Answer |
| --- | --- |
| Guest OS Availability differs from VM Availability and Infra Availability. How do you report Guest OS Availability for each VM? | We use VMware Tools for heartbeat. If Tools are not reporting, we check for signs of life (e.g. disk and network activity) |
| What is your Availability SLA for Guest OS? How often is this tracked? | We deliver 99.99% per month for each Tier 1 VM, tracked every 5 minutes. We do not track lower tiers as developers may reboot their VMs. |

## Application

| Business Question | Ideal Answer |
| --- | --- |
| Do you have visibility into what applications are running on each VMs? | To some extent, as our policy is not to install agents on each VM. Agents create maintenance, and at times interferes with VM performance. We use network analysis to detect common applications. |
| Can you map the Business Units and their Applications into each VM in vSphere? Can you report performance by applications? | Yes, we can. We organize our vCenter folders to reflect the BU, applications and tiers within the apps. |

## Business Management

| Business Question | Ideal Answer |
| --- | --- |
| Is your chargeback or billing operationalized? Do your customers see your billing model as fair & competitive? | Yes. Our pricing model is much simpler than AWS/Azure pricing. The model is simpler, and we have less choice versus public cloud. |
| Can you justify the pricing of each service tier to your customers? How does it compare with the public cloud? | We publish the comparison for our internal customers to see. |
| Do you have challenges ensuring predictable billing for your cloud? | We bill by allocation (what is configured to each VM), not by actual utilization. This is in-line with AWS billing model. This helps to make billing more predictable. Coupled with annual billing, we can predict revenue and plan our break-even accordingly. |

## Public Cloud

| Business Question | Ideal Answer |
| --- | --- |
| Does App Team use AWS/Azure, bypassing IT? Why? | As Enterprise IT, we are in the business of being a multi-cloud broker. We have both our on-prem cloud, and public cloud (VMware on Amazon, Azure and Amazon). |
| Is your IaaS cheaper and better than public cloud, especially VMware on AWS? If yes, quantify it. | Our on-prem is 25% cheaper than VMware on AWS and 40% cheaper than Amazon. This is in-line with other industry, where owning is cheaper than renting. |
| If you use public cloud, do you know when VMs are not performing? If yes, what metrics do you track since AWS/Azure has limited metrics? | AWS and Azure do not provide visibility on how our VM compete with other VMs. This prevents applications from making the right scaling decision. |

## Network Operations Center (NOC)

| Business Question | Ideal Answer |
| --- | --- |
| Do you have a set of big screen dashboards that provides live information into the environment?  | Yes. We rotate a few screens showing critical information such as Availability, Performance, Security (compliance), Capacity.
| What information is provided? How useful is the information? | We look at Applications, VMs and IaaS. |