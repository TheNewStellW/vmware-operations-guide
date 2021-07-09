---
title: "4. 灾难避免和恢复"
date: 2021-06-14T14:34:24+10:00
draft: false
weight: 40
---

{{% notice 信息 %}}
本页出租。这意味着我们需要一位贡献作者！
{{% /notice %}}

There are operational impact when you add capability to handle disaster. There are 3 primary use cases:

#### 避灾

您可以通过在延伸的 vSphere 集群上执行远程 vMotion 来避免灾难。

- Do you have enough WAN bandwidth?
- Does the vMotion complete within the expected time? - If not, what's causing it?
- What's the performance impact during the vMotion? As the pipe is shared, this can impact other VMs too.

#### DR Test

You are doing a test, as required by regulator or internal Business Continuity Plan. Your production VM is still running, so you need to buble the network.

- Do you have enough capacity on the recovery site?
- Did it complete within the expected time? If not, what's causing it?

#### DR Actual

You are doing the actual recovery. This can be planned or unplanned.

- 你有足够的资源吗？
- 对目标集群和数据存储有什么性能影响？

在大型环境中，您可以让多个集群参与主动/主动 DR，相互保护。这会创建复杂的关系，尤其是当您有数百个业务应用程序并且它们跨集群时。