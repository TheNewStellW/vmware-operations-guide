---
title: "5. 監管基準"
date: 2021-06-14T13:57:58+10:00
draft: false
weight: 50
---

讓我們談談開箱即用的監管基準。如前所述，vRealize Operations 提供了下面提到的基準測試：

- 互聯網安全中心 (CIS) 安全標準
- 國防信息系統局 (DISA) 安全標準
- 聯邦信息安全管理法案 (FISMA) 安全標準
- 1996 年健康保險流通與責任法案 (HIPAA) 合規性
- ISO網絡安全標準
- 支付卡行業 (PCI) 安全標準

需要注意的有趣一點是，所有這些基準測試都適用於同一組對象，主要是 vCenter、ESXi、VM、分佈式端口組和分佈式虛擬交換機。你可能會問，如果它們在相同的環境中工作，安全設置相似，它們有什麼不同？

這些監管基準由監管機構針對特定用例開發和認證。假設 ESXi 主機有 100 個配置要進行。其中一個基準可能需要配置其中的 60 個，另一個可能需要 60 個要求的另一種組合。例如，假設一個基準測試只需要“root”密碼需要設置一個到期時間。但另一個要求還需要根據定義的標准設置密碼複雜性。

您可以應用所有基準的所有建議並遵守所有這些建議。合規性檢查的目的是根據監管基准進行認證，以便每個人都可以確保滿足要求。如果沒有合規性和認證，只需要信任口耳相傳。對基準的遵守提供了信任和真實性。

## CIS網絡安全標準

Internet 安全中心 (CIS) 控制和 CIS 基準提供 Internet 安全的全球標準，並且是保護 IT 系統和數據免受攻擊的公認全球標準。 vRealize Operations 提供警報、策略和報告以根據 CIS 強化指南 [^1] 驗證 vSphere 資源。使用此內容驗證以下資源：

- ESXi 主機
- 虛擬機

CIS 標準提供了兩種不同的推薦區域，手動和自動。以下是可以自動化的 CIS 安全標準檢查的配置示例：

- 確保為每個 VM 配置單個鹽的默認值。默認情況下，salting 處於啟用狀態（Mem.ShareForceSalting = 2）並且每個 VM 都有不同的 salt。這意味著頁面共享不會發生在 VM 之間（VM 間 TPS），而只會發生在 VM 內（VM 內）。
- 確保NTP時間同步配置正確。
- 確保 ESXi 主機防火牆配置為限制對主機上運行的服務的訪問。
- 確保禁用託管對象瀏覽器 (MOB)：MOB 主要用於調試 vSphere SDK。由於沒有訪問控制，MOB 也可以用作獲取有關作為未授權訪問目標的主機的信息的方法。
- 確保不要使用默認的自簽名證書進行 ESXi 通信。
- 確保 SNMP 配置正確：如果 SNMP 配置不正確，包含敏感信息的監控數據可能會被發送到惡意主機，用於幫助利用該主機。
- 如果未使用，請確保未配置 dvfilter API：如果 dvfilter 網絡 API 已啟用並在將來配置，攻擊者可能會嘗試將 VM 連接到它，這可能會提供對主機上其他 VM 網絡的訪問。
- 確保在將主機添加到 Active Directory 時使用 vSphere Authentication Proxy：如果您將主機配置為使用主機配置文件加入 Active Directory 域，則 Active Directory 憑據將保存在主機配置文件中並通過網絡傳輸。為避免在主機配置文件中保存 Active Directory 憑據並避免通過網絡傳輸 Active Directory 憑據，請使用 vSphere Authentication Proxy。
- 確保禁用 VDS 運行狀況檢查：一旦啟用了 vSphere Distributed Switch 運行狀況檢查，它就會收集包含有關 host#、vds#port# 的信息的數據包，攻擊者會發現此信息很有用。

CIS 安全標準執行更多此類檢查，有關詳細列表，請從其 下載基準 [網站](https://www.cisecurity.org/benchmark/vmware/).

## DISA網絡安全標準

DISA 隸屬於國防部 (DoD)，是一個作戰支援組織。不遵守 DISA 發布的指南可能會導致組織被拒絕訪問 DoD 網絡。此合規性包驗證以下資源的合規性：

- vCenter
- ESXi 主機
- 虛擬機
- 分佈式端口組
- 分佈式虛擬交換機

來源: [VMware 虛擬市場](https://marketplace.cloud.vmware.com/services/details/vrealize-operations-compliance-pack-for-disa?slug=true)

## FISMA网络安全标准

FISMA 是美國立法，它定義了保護政府信息、運營和資產免受自然或人為威脅的綜合框架。此合規性包驗證以下資源的合規性：

- vCenter
- ESXi 主機
- 虛擬機
- 分佈式端口組
- 分佈式虛擬交換機

來源: [VMware 虛擬市場](https://marketplace.cloud.vmware.com/services/details/vrealize-operations-compliance-pack-for-fisma?slug=true)

## HIPAA 合規性

HIPAA 提供數據隱私和安​​全條款以保護醫療信息。適用於 HIPAA 的 vRealize Operations 合規性軟件包擴展了 vRealize Operations 的 SDDC 合規性功能。此合規性包驗證以下資源的合規性：

- vCenter
- ESXi 主機
- 虛擬機
- 分佈式端口組
- 分佈式虛擬交換機

來源: [VMware 虛擬市場](https://marketplace.cloud.vmware.com/services/details/vrealize-operations-compliance-pack-for-hipaa?slug=true)

## ISO網絡安全標準

ISO/IEC 27001 是 ISO/IEC 27000 系列標準中最著名的標準，為信息安全管理系統 (ISMS) 提供了要求。此合規性包驗證以下資源的合規性：

- vCenter
- ESXi 主機
- 虛擬機
- 分佈式端口組
- 分佈式虛擬交換機

來源: [VMware 虛擬市場](https://marketplace.cloud.vmware.com/services/details/vrealize-operations-compliance-pack-for-iso?slug=true)

## PCI 網絡安全標準

PCI 安全標準強化指南解決了對消費者支付信息日益增長的威脅。 PCI 對於接受、處理或接收付款以預防、檢測和響應可能導致違規的網絡攻擊的公司非常重要。此合規性包驗證以下資源的合規性：

- vCenter
- ESXi 主機
- 虛擬機
- 分佈式端口組
- 分佈式虛擬交換機

來源: [VMware 虛擬市場](https://marketplace.cloud.vmware.com/services/details/vrealize-operations-compliance-pack-for-pci?slug=true)

[^1]: 來源: [VMware 虛擬市場](https://marketplace.cloud.vmware.com/services/details/vrealize-operations-compliance-pack-for-cis/?slug=true#compliance)