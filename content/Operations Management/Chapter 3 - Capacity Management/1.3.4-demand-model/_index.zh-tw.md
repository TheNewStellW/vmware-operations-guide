---
title: "4. 需求模型"
date: 2021-06-14T10:54:46+10:00
draft: false
weight: 40
---

需求反映了生產中的現實，因為它基於集群和數據存儲中資源的實際需求。它默認啟用，無需任何配置，無法禁用。

需求大於消耗您容量的活動負載。活動負載是可見的需求，您可以使用利用率指標對其進行監控。有不可見的需求，因為它目前沒有使用。

使用 vRealize Operations 中的分配模型和緩衝區設置來滿足這種無形的需求。請注意，緩衝區在可用性之後應用。

#### 突然的需求

這可能會在共享環境中造成嚴重破壞。一組要求很高的 VM 可以共同影響集群或數據存儲的整體性能。這方面的一個例子是年度銷售或股市崩盤。在這種情況下，容量團隊應設置適當的過載比率並通過分配驅動，因為大部分時間需求較低。

#### 潛在需求

許多關鍵虛擬機都受到災難恢復的保護。在 DR 演習或實際災難期間，此負載將“喚醒”並消耗掉。您應該將 Site Recovery Manager 計劃納入您的能力範圍。

#### 潛在需求

許多新配置的 VM 需要時間來滿足其全部預期需求。數據庫達到最大規模，用戶群達到目標，功能完成需要時間。新配置的 VM 往往處於空閒狀態（可能是幾個月）並且可能會突然增長。當這種情況發生時，將導致需求增加。

#### 未滿足的需求

它分為兩部分：VM 內部和 VM 外部。

如果 VM 過小，未滿足的需求將不會對底層基礎架構可見。除非這是有意為之，否則在集群容量監控中包含小型虛擬機是明智之舉。

未滿足需求的可見部分成為 IaaS KPI 和 SLA 的一部分，在性能管理章節中進行了介紹。

------

在容量背景下計算需求時還有另外兩個考慮因素。

- 資源預留
- 資源限制

尚未消耗的預留會影響容量，但不會影響性能。使用餐廳類比，如果您的所有餐桌都已預訂，但只有 20% 出現，則剩餘容量為 0，但可以輕鬆為所有客戶提供服務，實際需求僅為 20%。

CPU 和內存的行為不同，因為當預留持有者不使用 CPU 預留時，它不會生效。

需要考慮限制，因為需求不能超過強制限制。好的部分是需求計數器已經考慮到了這一點。
