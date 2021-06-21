---
title: "1. Complaint-Based Operations"
date: 2021-06-11T11:31:22+10:00
draft: false
---

How do you know that the Infrastructure as a Service (IaaS) Platform (be it on-prem or in the cloud) is serving its workload *well*? If you depend on complaints, then you run a complaint-based operation.

Changing from reactive to proactive is unfortunately a complex undertaking, especially in large organizations where there are many roles and personas. It requires [operations transformation](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/files/pdf/services/vmware-operations-transformation-services.pdf) and a paradigm shift. It is not easy to get customers to agree on a [Service Level Agreement](/operations-management/chapter-1-overview/1.1.7-service-level-agreement/) (SLA) when you’ve promised them “good” for years already. This book aims to provide practical guidance, something you can implement with the current version of vRealize products.

The litmus test below helps you assess the maturity of your IaaS.

### Do your customers blame your infrastructure?

If the answer is yes, take a moment to ponder why. There is a high chance you are relying on complaints in your operations so you actually encourage them. No complaint, no problem. That’s why it’s aptly named Complaint-based Operations.

The reason why you rely on complaint is the operations have no other means by which to measure success. You have not defined the performance of your IaaS.

That’s the goal of this book.

A sign of matured operations is that you have complete, correct and accurate [Service Level Agreements](/operations-management/chapter-1-overview/1.1.7-service-level-agreement/). Complete means you have Performance SLAs and Compliance SLAs, not just Availability SLAs. Correct means the SLA is measured on each paying VM, and not at the infrastructure level. It also means you use the right metric. Accurate means the measurement has to be measured every 5 minutes, as any longer intervals than this can miss the problem.

### Is your IaaS cheaper than public cloud or hybrid cloud?

The commoditization of infrastructure means your IaaS is being compared with similar platforms such as VMware Cloud on AWS and Amazon Web Services.

If not, your CIO may question your business value. The reason for having an in-house architect is so you can bring lower cost, after taking into account your salary.

### Does Help Desk provide a good first level defence?

If Help Desk simply passes issues through to the next level, you need to look at why.

Help Desk is your first line of defence. They are not as technical as you are. Equip them with a simple dashboard so that they can handle VM Owner complaints by discovering:

- Is the problem caused by IaaS not serving the VM well?
- If yes, which part of the Infra: CPU, RAM, Disk, Network?
- If not, how to prove it convincingly?

### Can you justify new infrastructure when utilization is _not_ high?

This is not referring to additional money that comes with new projects. This is referring to existing workload on existing clusters/storage.

Capacity is measured on utilization and performance. A cluster capacity is full if it can’t serve its VMs well. Since it takes time to buy hardware, you need to have an **early warning** system to detect this performance degradation.

### Do you struggle with many over-provisioned VMs?

This is an indicator that you are operating as a System Builder as opposed to a Service Provider. As a System Builder, you are meddling with each System (read: Application). You size them and argue with the application team, who are actually your customers. You are busy as there are many applications and you are outnumbered.

If you are operating as an internal [Cloud Service Provider](https://itlaw.wikia.org/wiki/Cloud_service_provider), You are not “in the way” of the business. You use an effective pricing model to drive the right behaviour. Does a public cloud provider block application teams when they buy 40 CPU [AWS EC2](https://aws.amazon.com/ec2/?ec2-whats-new.sort-by=item.additionalFields.postDateTime&ec2-whats-new.sort-order=desc) VMs when they only need 2 CPU? They don’t, hence neither should you.

### Does Troubleshooting mean all hands on deck?

Do you have a process that is followed by all teams (network, storage, server, OS, application)? Does that process end with Root Cause Analysis?

As part of RCA, do you set up alerts so the same issue can be detected faster if it happens again? Without an alert configured, the RCA is not closed. The alert is also critical as it will trigger the RCA process.