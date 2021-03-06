---
title: "3. 成本"
date: 2021-06-14T13:23:33+10:00
draft: false
weight: 30
---

計算單位成本很重要，儘管它實際上並不存在。當您購買集群時，您沒有為每 GHz CPU 支付 1 美元。您為整個設備（包括安裝）支付了 100,000 美元。 1 美元僅用於計算目的，因此您不會以虧損告終。

![成本投入和單位定價](1.5.3-fig-1.png)

每個 VM 的單位成本取決於 過度承諾 比率, 因為硬件成本是一樣的. 如果集群 A 有 2x 過度承諾 比率, 那麼在相同的其他條件下，每個 VM 的成本要便宜 2 倍。

過度承諾比率是您解釋更高價格的方式，因此必須提前向您的客戶披露。

單位成本必須與 VM 相關聯，而不是與 ESXi 相關聯。它以 vCPU 表示，而不是以物理內核或 GHz 表示。您計劃打包多少個 vCPU 決定了每個 vCPU 的成本。

單位成本取決於硬件和軟件。由於更大的硬件，新集群的成本應該更低。

在相同的服務水平內，單價應保持不變。回到航空業的例子，價格不取決於飛機的類型。

## 節約成本

從財務的角度來看，只有推遲新採購才能實現真正的成本節約。你不能節省你已經花費的，會計明智的。成本節約實際上是成本避免。

我們舉一個簡單的例子：

- 3 年前，您在超融合基礎設施 (HCI) 解決方案上花費了 200 萬美元。
- 已經很好用了，現在剩餘容量為0%，需要購買新的HCI。這只會花費您 100 萬美元，因為 HCI 解決方案的成本在過去 3 年中下降了一半。
- 通過勤奮而艱鉅的回收過程，您設法釋放了產能。因此，您不需要花費 100 萬美元。您可以將此購買推遲到下一個財政年度。
- 您從這次填海中節省了多少：200 萬美元或 100 萬美元？

在會計方面，它只有100萬美元。儘管三年前 HCI 花費了您 200 萬美元，但具有相同容量的全新設備只需花費您 100 萬美元。在會計規則中，您不應該混合來自不同日期的數字，更不用說來自不同會計年度的數字。折舊在這裡不相關，因為成本基於重置成本。

一百萬美元當然是 ***估計***。避免或花費的實際成本取決於供應商的報價和您的談判技巧。請注意，實際成本遠高於 HCI 成本。額外的成本可能會超過硬件成本。您需要包括所有加載成本，例如數據中心設施、實施服務、備份存儲、管理服務、軟件許可、管理等。

僅開墾就可以 ***不是*** 降低成本. 刪除筆記本中的文件可以節省多少錢？

正確的。零。

只有當它幫助您推遲購買新硬盤時，您才能真正節省成本。

服務怎麼樣？我們喜歡將提高生產力稱為成本節約。儘管這提供了商業價值，但這並不是一項硬成本節約。這是一種沒有會計價值的軟收入。只有在推遲購買額外資源/員工的需要，或管理服務合同的價值下降時，才會發生硬性儲蓄。

您可以通過關閉硬件電源來節省電力和冷卻。

對於擁有大量基礎設施足蹟的大型組織，技術更新是降低成本的好方法。從 100 個機架減少到 50 個機架肯定會降低資本和運營成本。

![成本節約公式](1.5.3-fig-2.png)

IT 需要領先於業務。在計算成本節省時，包括承諾的項目和未來的增長。您還應該考慮太小的 VM，因為應用程序團隊可能需要擴大它們。

計算 CPU、RAM 和磁盤。如果可能，還包括網絡。計算起來比較困難，因為它本質上只是互連。對於這三個 IaaS 資源中的每一個，計算需求和恢復。對於要求，不要忘記包括所有成本。當 VM 需要 100 GB 時，它會轉化為更多，因為您將 DR、備份、快照等考慮在內。

下表提供了一個示例。

![所需的基礎設施和節省](1.5.3-fig-3.png)

您需要為每個物理位置準備上表。僅僅因為您在新加坡擁有 10 TB 的 RAM 並不意味著亞美尼亞虛擬機可以使用它。

## 優化成本

上述練習將有助於優化成本。當然，還有其他方法可以優化成本，因為成本涵蓋的不僅僅是容量。它涵蓋了人員、流程和架構。您可以通過提高流程效率來降低成本，通常是通過業務流程再造練習。您可以通過自動化提高流程效率來降低成本。例如。使用批准工作流刪除關閉的 VM。

下表總結了您可以執行以優化成本的活動。

![為消費者和供應商節省成本](1.5.3-fig-4.png)

小型集群具有更高的 HA 開銷，因此您可以通過整合它們來優化成本。

複雜性是有代價的，但很難量化。例如，人為錯誤可能代價高昂，但您如何對其進行量化？

請注意，標準化將降低複雜性。但這也意味著配置不夠靈活，會增加成本。

簡化操作，例如不在同一集群中混合具有不同服務類別的 VM，將降低複雜性。但這也以更大的基礎設施為代價。 T 卹尺寸也是如此。