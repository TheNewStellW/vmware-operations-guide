---
title: "5. 监管基准"
date: 2021-06-14T13:57:58+10:00
draft: false
weight: 50
---

让我们谈谈开箱即用的监管基准。如前所述，vRealize Operations 提供了下面提到的基准测试：

- 互联网安全中心 (CIS) 安全标准
- 国防信息系统局 (DISA) 安全标准
- 联邦信息安全管理法案 (FISMA) 安全标准
- 1996 年健康保险流通与责任法案 (HIPAA) 合规性
- ISO网络安全标准
- 支付卡行业 (PCI) 安全标准

需要注意的有趣一点是，所有这些基准测试都适用于同一组对象，主要是 vCenter、ESXi、VM、分布式端口组和分布式虚拟交换机。你可能会问，如果它们在相同的环境中工作，安全设置相似，它们有什么不同？

这些监管基准由监管机构针对特定用例开发和认证。假设 ESXi 主机有 100 个配置要进行。其中一个基准可能需要配置其中的 60 个，另一个可能需要 60 个要求的另一种组合。例如，假设一个基准测试只需要“root”密码需要设置一个到期时间。但另一个要求还需要根据定义的标准设置密码复杂性。

您可以应用所有基准的所有建议并遵守所有这些建议。合规性检查的目的是根据监管基准进行认证，以便每个人都可以确保满足要求。如果没有合规性和认证，只需要信任口耳相传。对基准的遵守提供了信任和真实性。

## CIS网络安全标准

Internet 安全中心 (CIS) 控制和 CIS 基准提供 Internet 安全的全球标准，并且是保护 IT 系统和数据免受攻击的公认全球标准。 vRealize Operations 提供警报、策略和报告以根据 CIS 强化指南 [^1] 验证 vSphere 资源。使用此内容验证以下资源：

- ESXi 主机
- 虚拟机

CIS 标准提供了两种不同的推荐区域，手动和自动。以下是可以自动化的 CIS 安全标准检查的配置示例：

- 确保为每个 VM 配置单个盐的默认值。默认情况下，salting 处于启用状态（Mem.ShareForceSalting = 2）并且每个 VM 都有不同的 salt。这意味着页面共享不会发生在 VM 之间（VM 间 TPS），而只会发生在 VM 内（VM 内）。
- 确保NTP时间同步配置正确。
- 确保 ESXi 主机防火墙配置为限制对主机上运行的服务的访问。
- 确保禁用托管对象浏览器 (MOB)：MOB 主要用于调试 vSphere SDK。由于没有访问控制，MOB 也可以用作获取有关作为未授权访问目标的主机的信息的方法。
- 确保不要使用默认的自签名证书进行 ESXi 通信。
- 确保 SNMP 配置正确：如果 SNMP 配置不正确，包含敏感信息的监控数据可能会被发送到恶意主机，用于帮助利用该主机。
- 如果未使用，请确保未配置 dvfilter API：如果 dvfilter 网络 API 已启用并在将来配置，攻击者可能会尝试将 VM 连接到它，这可能会提供对主机上其他 VM 网络的访问。
- 确保在将主机添加到 Active Directory 时使用 vSphere Authentication Proxy：如果您将主机配置为使用主机配置文件加入 Active Directory 域，则 Active Directory 凭据将保存在主机配置文件中并通过网络传输。为避免在主机配置文件中保存 Active Directory 凭据并避免通过网络传输 Active Directory 凭据，请使用 vSphere Authentication Proxy。
- 确保禁用 VDS 运行状况检查：一旦启用了 vSphere Distributed Switch 运行状况检查，它就会收集包含有关 host#、vds#port# 的信息的数据包，攻击者会发现此信息很有用。

CIS 安全标准执行更多此类检查，有关详细列表，请从其 下载基准 [网站](https://www.cisecurity.org/benchmark/vmware/).

## DISA网络安全标准

DISA 隶属于国防部 (DoD)，是一个作战支援组织。不遵守 DISA 发布的指南可能会导致组织被拒绝访问 DoD 网络。此合规性包验证以下资源的合规性：

- vCenter
- ESXi 主机
- 虚拟机
- 分布式端口组
- 分布式虚拟交换机

来源: [VMware 虚拟市场](https://marketplace.cloud.vmware.com/services/details/vrealize-operations-compliance-pack-for-disa?slug=true)

## FISMA网络安全标准

FISMA 是美国立法，它定义了保护政府信息、运营和资产免受自然或人为威胁的综合框架。此合规性包验证以下资源的合规性：

- vCenter
- ESXi 主机
- 虚拟机
- 分布式端口组
- 分布式虚拟交换机

来源: [VMware 虚拟市场](https://marketplace.cloud.vmware.com/services/details/vrealize-operations-compliance-pack-for-fisma?slug=true)

## HIPAA 合规性

HIPAA 提供数据隐私和安全条款以保护医疗信息。适用于 HIPAA 的 vRealize Operations 合规性软件包扩展了 vRealize Operations 的 SDDC 合规性功能。此合规性包验证以下资源的合规性：

- vCenter
- ESXi 主机
- 虚拟机
- 分布式端口组
- 分布式虚拟交换机

来源: [VMware 虚拟市场](https://marketplace.cloud.vmware.com/services/details/vrealize-operations-compliance-pack-for-hipaa?slug=true)

## ISO网络安全标准

ISO/IEC 27001 是 ISO/IEC 27000 系列标准中最著名的标准，为信息安全管理系统 (ISMS) 提供了要求。此合规性包验证以下资源的合规性：

- vCenter
- ESXi 主机
- 虚拟机
- 分布式端口组
- 分布式虚拟交换机

来源: [VMware 虚拟市场](https://marketplace.cloud.vmware.com/services/details/vrealize-operations-compliance-pack-for-iso?slug=true)

## PCI 网络安全标准

PCI 安全标准强化指南解决了对消费者支付信息日益增长的威胁。 PCI 对于接受、处理或接收付款以预防、检测和响应可能导致违规的网络攻击的公司非常重要。此合规性包验证以下资源的合规性：

- vCenter
- ESXi 主机
- 虚拟机
- 分布式端口组
- 分布式虚拟交换机

来源: [VMware 虚拟市场](https://marketplace.cloud.vmware.com/services/details/vrealize-operations-compliance-pack-for-pci?slug=true)

[^1]: 来源: [VMware 虚拟市场](https://marketplace.cloud.vmware.com/services/details/vrealize-operations-compliance-pack-for-cis/?slug=true#compliance)