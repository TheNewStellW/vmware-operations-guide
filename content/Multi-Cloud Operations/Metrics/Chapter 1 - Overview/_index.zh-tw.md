---
title: "第 1 - 章概述"
date: 2021-06-11T11:31:22+10:00
draft: false
chapter: true
---

### 第1章

# 概述

vSphere 計數器比物理機計數器更複雜，因為有許多組件以及由虛擬化引起的不一致。虛擬化後，基礎架構的 4 個元素（CPU、RAM、磁盤、網絡）的行為 ***不同***。

新層造成的複雜性，因為它會影響其下方和上方的相鄰層。所以淨效應你需要學習三層。 T這就是為什麼從監控和故障排除的角度來看, [容器](https://en.wikipedia.org/wiki/OS-level_virtualization) 技術需要更深入的知識，因為邊界更不嚴格。想想所有的 [問題](https://www.settlersoman.com/ftf-012-resource-pools-in-practice/) 您擁有 vSphere 資源池性能故障排除功能，現在可以在進程級別進行細化！
