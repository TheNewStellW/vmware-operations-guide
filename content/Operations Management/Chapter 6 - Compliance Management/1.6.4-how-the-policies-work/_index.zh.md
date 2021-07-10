---
title: "4. 政策如何运作"
date: 2021-06-14T13:53:48+10:00
draft: false
weight: 40
---

在介绍了 vRealize Operations 中提供的内容之后，让我们讨论这些策略的工作原理。他们在做什么？所有这些策略的基础是某些配置和警报设置。根据官方文档，“vRealize Operations 中的所有合规性标准，包括您定义的任何标准，都基于警报定义。仅计算合规性子类型的警报定义。自定义记分卡可以监控用户定义的警报。” [^1]。

例如，“ISO 安全标准”以许多其他方式检查以下内容：

- 在 ESXi 主机上配置 SSH 服务以实现合规性
- 通过禁用SSH服务和shell服务并启用锁定模式来限制对主机的远程访问
- 在 vCenter Server 中提供复杂的密码
- 在 vCenter Server 中配置锁定

所有这些配置都在环境中检查。根据环境中的这些检查定义症状，并最终为这些症状设置警报。

如果有任何警报，则表示设置策略中存在错误配置，需要更正。

这也导致定义您自己的自定义症状的范围 -> 警报 -> 基准.

[^1]: 来源：[VMware 文档](https://docs.vmware.com/en/vRealize-Operations-Manager/8.3/com.vmware.vcom.config.doc/GUID-A4FBC2C3-6F43-4C45-BD19-72A11110745E.html)