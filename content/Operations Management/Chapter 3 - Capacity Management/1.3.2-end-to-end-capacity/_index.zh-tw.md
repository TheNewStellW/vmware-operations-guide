---
title: "2. 端到端容量"
date: 2021-06-14T10:46:13+10:00
draft: false
weight: 20
---

如果從規劃階段開始，容量管理將變得更加容易。您可以在此處定義產品、設定價格和性能預期。如果您不設定預期，您的客戶將需要您當前的基礎架構無法滿足的高性能。

容量管理需要端到端的規劃和調整，因為歸根結底，它會將您面臨的現實與您設定的計劃進行比較。平衡供需需要您查看以下 6 個組成部分。步驟1和2一起完成，剩下的4個步驟可以並行完成。

![需求和供應](1.3.2-fig-1.png)

與績效管理不同，這一運營支柱不需要深厚的技術知識。如果您不信任我，讓我們檢查您的技術技能。

- 您能否構建一個性能與物理性能匹配的集群？
  - 簡單，只是不要過度使用或為 VM 保留 100%。
- 你能建立一個可以處理巨大虛擬機的集群嗎？
  - 簡單，只需為每個插槽獲取大量內核。
  - 很簡單，在盒子裡放很多核就行了。
- 你能構建一個可用性非常高的架構嗎？
  - 很簡單，只要有更多的 HA 主機，更多的 vSAN FTT，並且容錯域分佈在不同的機架上。
  - 簡單，只要有更多的 HA 主機。
- 能不能搭建一個可以運行大量虛擬機的集群？
  - 很簡單，只要得到很多大主機。
- 你能優化性能嗎？
  - 當然，請遵循性能最佳實踐並針對性能進行配置。
- 你能降低成本嗎？
  - 當然，盡量減少硬件和軟件的成本，選擇性價比最高的。您了解所有供應商及其技術。你知道每個人的優點和缺點。

如果從一開始就做好以上這些事情並不難，這就是為什麼我們需要從計劃階段開始。如果從第 6 步開始而忽略第 1 步和第 2 步，您將扮演 [Mission Impossible](https://en.wikipedia.org/wiki/Mission:_Impossible_(film_series)) 電影中的主角。