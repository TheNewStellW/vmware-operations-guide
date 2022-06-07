---
title: "4. 政策如何運作"
date: 2021-06-14T13:53:48+10:00
draft: false
weight: 40
---

在介紹了 vRealize Operations 中提供的內容之後，讓我們討論這些策略的工作原理。他們在做什麼？所有這些策略的基礎是某些配置和警報設置。根據官方文檔，“vRealize Operations 中的所有合規性標準，包括您定義的任何標準，都基於警報定義。僅計算合規性子類型的警報定義。自定義記分卡可以監控用戶定義的警報。” [ ^1]。

例如，“ISO 安全標準”以許多其他方式檢查以下內容：

- 在 ESXi 主機上配置 SSH 服務以實現合規性
- 通過禁用SSH服務和shell服務並啟用鎖定模式來限制對主機的遠程訪問
- 在 vCenter Server 中提供複雜的密碼
- 在 vCenter Server 中配置鎖定

所有這些配置都在環境中檢查。根據環境中的這些檢查定義症狀，並最終為這些症狀設置警報。

如果有任何警報，則表示設置策略中存在錯誤配置，需要更正。

這也導致定義您自己的自定義症狀的範圍 -> 警報 -> 基準.

[^1]: 來源：[VMware 文檔](https://docs.vmware.com/en/vRealize-Operations-Manager/8.3/com.vmware.vcom.config.doc/GUID-A4FBC2C3-6F43-4C45-BD19-72A11110745E.html)