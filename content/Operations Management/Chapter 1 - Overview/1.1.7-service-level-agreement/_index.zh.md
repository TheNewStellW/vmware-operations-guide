---
title: "7. 服务水平协议"
date: 2021-06-11T11:31:22+10:00
draft: false
---

企业级云和非企业级云之间的区别在于 SLA。云提供商可以声明他们拥有最好的技术、最有经验的专业人员、最具创新性的流程、行业认证等，以证明他们是最好的。如果他们害怕在他们的合同中用 SLA 来支持它，那么所有这些都将无济于事。 SLA 使客户能够追究云提供商的责任，因为它会带来经济损失。

一旦定义了 SLA，客户就想知道它将如何交付。这就是流程、架构、认证等的用武之地。什么总是在如何之前。

## IaaS 的 4 个 SLA

IaaS 企业应提供三个 SLA，因为客户需要全面覆盖。

| SLA | 描述 |
| ------ | ----- |
| 可用性 | 这是最基本的SLA。它是最古老和最知名的。事实上，这在很大程度上是给定的。事实上，商定的数字是多少并不重要。如果这该死的事情失败了，你最好在有人抱怨或事情变得更糟之前迅速提出来！ |
| 性能 SLA | 仅仅因为发生了一些事情并不意味着它会很快。虚拟机是可以启动的，但是如果服务太慢，那就关掉就好了。 性能 SLA 涵盖了这一点并解决了基于投诉的操作 [CBO](/zh/operations-management/chapter-1-overview/1.1.1-complaint-based-operations/) 通过定义什么是快速的。 它涵盖了CPU、内存、磁盘和网络，因此使用了四个指标。 |
| 遵守 | 这为行业法规或认证提供了安全合规性。 |
| 服务 | 以上三个SLA是由技术提供的。它们需要得到人类提供的服务的补充。这应该涵盖主动和被动服务。两个流行的例子是响应时间和解决时间。 |

## KPI vs. SLA

KPI 和 SLA 齐头并进。

| 首字母缩略词 | 描述 |
| :-------: | ----------- |
| SLA | 您与客户签订的正式商业合同。通常，这是在 IaaS 提供商（基础架构团队）和 IaaS 消费者（应用程序团队或业务部门）之间进行的。 正式的 SLA 需要运营转型 [OT](https://blogs.vmware.com/services-education-insights/services/operations-transformation-services). 它需要的不仅仅是技术更改，因为您需要查看合同、价格（不仅仅是成本）流程、人员等。如果违反 SLA，它往往会受到经济处罚，例如下一个计费周期的信用。|
| KPI | 这包括 SLA 指标，以及在违反 SLA 指标之前提供预警的相关附加指标。一个给定的 SLA 有很多 KPI，而 KPI 是 SLA 的先决条件。如果您没有适当的 SLA，那么在提交 SLA 之前先从内部 KPI 开始。 首先了解并[分析](/zh/operations-management/chapter-2-performance-management/1.2.10-baseline-profiling/) 你的IaaS的实际性能。 使用 [此处](/zh/operations-management/chapter-2-performance-management/1.2.10-baseline-profiling/) 中描述的分析技术，我分析了超过一百万个数据点。 | 

SLA 是 **每月** 计数器，而不是每天或每年。您使用整个月的数据来计算它。

The timeline matters. In the following table, notice 99.999% in a year is actually easier than 99.95% in a week. Your customers would not accept a yearly counter as they can be exposed to a long downtime. You would not accept a daily counter as there is no room for error. The monthly counter provides a balance between service quality and cost to deliver the service. It also makes reporting easier as you simply follow the calendar month.

![SLA downtime duration comparison](1.1.7-fig-1.png)

Each additional "9" shrinks your downtime window by 10x. That's why each decimal can cost a lot more money, as a different architecture may be required.

Even if you measure the SLA once a month, it can still be very difficult to meet. Take a look at the following table. For simplicity, we will use Availability SLA and not Performance SLA, because up or down is a simple binary.

![SLA downtime in minutes comparison](1.1.7-fig-2.png)

If you promise 99.99%, you only have 4.0 minutes - 4.5 minutes of downtime per calendar month. That means your architecture must be able to detect the issue and then complete proper remediation in just a few minutes. That's a tight space to manoeuvre.

A unique saving grace that applies to Availability but not Performance is scheduled downtime. There is no such thing as scheduled downtime in performance. Specific to IaaS, you can propose that scheduled downtime is not included in the SLA, so long it's done quickly and rarely. Planned activities such as VM hardware upgrade, Tools upgrade and Windows upgrade can be included in scheduled downtime activities. Downtime caused by customer is not included, be it intentional or not. This is why you need two counters: one for SLA and one for actual. The actual will record every downtime, be it a part of SLA or not.

A challenge that impact Availability but not Performance is recovery time. Your system may detect the VM is down within 1 minute, but the reboot process until the entire OS is properly up and running takes 5 minutes, as it needs to perform filesystem consistency check.

KPI complements SLA as it tracks at much higher intensity and it covers more counters and events. Use vRealize Log Insight for more time sensitive event, as vRealize Operations measures every 5 minutes.

![explaination of availability and performance SLAs and KPIs](1.1.7-fig-3.png)

From the preceding table, note that Guest OS counters are not included as that's part of "application KPI" or VM KPI, not IaaS KPI. They impact the VM performance, but nothing the IaaS can do, meaning the remediation is at the Guest OS layer.

KPI also complements SLA by providing the stepping stone in your operations transformation. It is a necessary step towards operations with real business SLA.

![complaint, KPI and SLA steps](1.1.7-fig-4.png)

You walk from where you stand. Adopt KPI first. Baseline your actual availability, performance, and compliance over time. Remember these counters are VM level, not infrastructure. Therefore, you need to profile all the VMs.

## Class of Service

The following table shows a basic and generic guideline to a class of service. The actual model that you will implement will certainly differ, taking into account technology and business demand. In the [capacity management section](/zh/operations-management/chapter-3-capacity-management/1.3.3-capacity-planning/), we walk through an actual example.

![class of service positioning breakdown](1.1.7-fig-5.png)

The table above is further defined by their SLA, because you need to quantify what 10% penalty exactly means.

A Gold class has higher SLA than Silver. For that to happens, that means they are measured against the same benchmark.

- For availability, you measure all classes against the ideal, which is no downtime.
- For performance, you measure them against the same threshold, which is a stringent (read: fast) number.
- For compliance, you measure them against the ideal, which is perfect compliance.
- For service, you measure them against the ideal, which is the best possible service.

![VM health measured against SLA diagram](1.1.7-fig-6.png)

### Performance SLA

Let's elaborate Performance SLA a bit, as it is more complex than the other two.

Following the above, diagram, you offer 99.9% for Gold, and 99% for Silver as the respective SLA.

For Gold to be higher than Silver, that means both are measured against the _same raw threshold_. In other words, a VM in Silver environment will expect that it does not get what it demands as often as a VM in Gold. If the VM Owner wants to have more _consistent_ service in performance, then simply pay more and upgrade to the Gold cluster.

This approach is easier than setting up a different performance threshold for each tier. Say you set the following:

- **Gold**: VM Memory Contention: 0.5%
- **Silver**: VM Memory Contention: 1.5%

You notice the problem already?

It is hard to explain the delta or gaps between the class of services. Why is Silver 3x the value if it is only half the price? Shouldn't it be proportionate?

There is a 2nd problem. If you set _different_ standards, it is possible that Silver will perform better than Gold, because it has lower standard. This can create confusion.

Operationally, having a single threshold is easier to set up. No need to play with vRealize Operations policy. You can also have mixed classes of VM in the same cluster or datastore, as the SLA threshold is the same.

We will cover the counters used in Performance SLA in more details [here](/zh/operations-management/chapter-2-performance-management/1.2.6-performance-sla/).

### Differentiated Service

IaaS is built on commodity hardware and provided as a utility. Having said that, there are many ways to differentiate your service vs your competitors. Use class of service to distinguish premium service. The following table lists some examples.

| Service | Description |
| ------- | ----------- |
| Backup | Gold Tier provides application-level back up. It also provides more frequent full back up, and customers are provided with self-service individual file restore. |
| High Availability | Gold Tier provides application- level monitoring. Customers can also ask for specific boot up sequence of their VMs, and ask for VM-Host affinity rules to minimize risk. |
| Disaster Recovery | Gold Tier provides lower [RPO and RTO](https://en.wikipedia.org/wiki/Disaster_recovery). Customers are also entitled to annual real test, where the production workload are run from the DR site. |
| Snapshot | Gold Tier provides longer snapshot and larger snapshot. |
| OS Management | Gold Tier provides flexibility in patching. Customers can specify delay in patching and request for custom patch package, where not all patches from Microsoft or Red Hat is applied. |
| VM Management | Gold Tier provides flexibility in updating Tools and VM Hardware. Customers are allowed to defer the update |
| Monitoring Service | Gold Tier VMs will be proactively monitored, not just relying on alerts. Gold Tier provides deeper visibility into the underlying physical infrastructure where customers VM are running. Customers are entitled for lower internal metrics such as vMotion stun time and VMkernel latency. Gold tier provides self-service monitoring. Customers are given their own login to a portal where they can monitor their own VMs. They can initiate scheduled downtime. Customers will be alerted over email and messaging network. |
| Support | Gold Tier provides faster response time, longer business hours, and faster resolution time. |
| Network | Gold Tier provides priority network. Customers can opt for periodic ping service to ensure network latency between their applications remain within the agreed threshold. |
| TAM | Gold Tier comes with a Technical Account Manager, acting as single point of contact for customers |