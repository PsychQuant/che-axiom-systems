---
name: language-learning
description: 語言習得的模型與現象。討論學外語或設計語言教材時使用——輸入的角色、習得機制、語言表徵、溝通功能、發展階段的限制、可學習性與輸入充分性。Use when reasoning about second-language acquisition: the role of input, acquisition mechanisms, linguistic representation, communicative function, and developmental constraints.
argument-hint: "[自然語言 | 章節名]（裸呼叫＝載入本域待命）"
---

# language-learning（公理域的觸發面）

本 skill 是 `language-learning` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="language-learning: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域，之後的搜尋、引用上限（inline 最多 3 條）、`📎 相關公理` 清單格式、以及「無足夠相關公理 → 靜默 no-op」都照它的契約走。

## 本域現有條目（供判斷相關性，非權威內容）

| 章節 | 一句話 |
|------|--------|
| 〈Axiom L1: Linguistic Input〉 | 輸入是習得的必要條件 |
| 〈Axiom L2: Learning Mechanisms〉 | 習得機制 |
| 〈Axiom L3: Linguistic Representation〉 | 語言的心理表徵 |
| 〈Axiom L4: Communicative Function〉 | 語言的溝通功能 |
| 〈Axiom L5: Developmental Constraints〉 | 發展階段的限制 |
| 〈P2: Input Sufficiency Principle〉 | 輸入充分性 |

權威內容以 `domains/language-learning/` 下的公理檔為準；上表只是章節摘要，不可用於引用。本域為 markdown 格式，引用時用章節名、**不捏造 ID**。 新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 邏輯與語意的形式問題 | `logic-and-language` |
| 數學能力的學習依賴 | `mathematical-learning` |
| 日本文學的敘事構成 | `japanese-narrative` |
