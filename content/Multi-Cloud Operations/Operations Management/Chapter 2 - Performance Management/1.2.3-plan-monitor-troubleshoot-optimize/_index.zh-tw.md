---
title: "3. 計劃 監視器 故障排除 優化"
date: 2021-06-12T23:58:38+10:00
draft: false
weight: 30
---

績效管理有四個不同的過程：

#### 計劃

這是您設定績效目標的地方。確保目標與業務可交付成果一致。

當您設計該 vSAN 時，您考慮過多少毫秒的磁盤延遲？例如，您將目標設置為在 VM 級別（不是 vSAN 級別和單個虛擬磁盤級別）測量的 10 毫秒。

#### 監視器

這是您比較計劃與實際的地方。這就是為什麼必須明確定義目標的原因。現實是否與您的架構應該提供的內容相匹配？如果沒有，那麼你需要修復它。

#### 故障排除

當現實比計劃更糟或出現問題時，您會這樣做，而不是在有投訴時。您想花時間進行故障排除，因此最好主動進行。並且悄悄地，沒有人催促你獲得結果。

#### 優化

作為監控的一部分，您可能不會發現問題，但您會發現使性能更好的機會。新版本提供性能改進是很常見的。同樣，您要主動這樣做，而不是等待投訴發生。
------

監視器 是 **什麼**，故障排除 是 **為什麼**。監視器是 [標準操作程序](https://en.wikipedia.org/wiki/Standard_operating_procedure) (SOP) 的一部分，故障排除是一個臨時的、按需的過程。借助預定義的儀表板和警報，可以由 1 級團隊執行監控，而故障排除則需要專家團隊。專家組也是設定Level 1 團隊使用門檻的團隊。故障排除涉及日誌分析，因為許多系統不會生成完整的指標，並且一個常見問題背後可能有許多不同的原因。最後，實際的根本原因甚至可能與問題沒有密切關係。

![健康/不健康概覽](1.2.3-fig-1.png)

當您區分監控和故障排除時，日常操作就會變得更加系統化。下表顯示了差異：

|       | 监视器 | 故障排除 |
|-------|---------|--------------|
| **問題** |問題是什麼？ |為什麼會發生？問題的真正原因是什麼？ |
| **自然** |主動 |反應式 |
| **櫃檯** |一般1個櫃檯。而這個計數器也是SLA。這是您或您的客戶檢查的第一個櫃檯。 |總是有很多櫃檯。有多層計數器，一個影響另一個。
| **SLA** |是的，這意味著 SLA 適用 |是的。如果違反 SLA，事情就變得很緊急。 |
| **關鍵績效指標** |是的，這意味著您在監控中使用 KPI 而不是單個指標。 |是的，但作為起點。然後深入研究支持指標，這些指標通常是原始指標。 |
| **指標** |初級計數器。作為 SOP 的一部分，您主動檢查它 |二級計數器。您只檢查主要是否達到閾值。 |
| **頻率** |每天執行。作為 SLA 的一部分，黃金級將比青銅級具有更高的定期監控頻率。 |一經請求。 |
| **時間線** |現在和未來。您考慮未來的負載並進行預測。 |現在。未來無關緊要。你的重點是撲滅火災或潛在的火災。 |

在大多數情況下，最好使用 5 分鐘的間隔進行監控，因為 1 分鐘的不良指標可能不會對業務產生影響。另一方面，故障排除可能需要每秒粒度。但是，如果您的補救措施相同，這並不總是意味著您需要查看每個計數器。