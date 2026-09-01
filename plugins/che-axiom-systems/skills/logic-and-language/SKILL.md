---
name: logic-and-language
description: "邏輯系統與後設邏輯。處理形式推論時使用——等式的遞移性與同餘、部分與整體的量關係、命題邏輯的同一律、以及後設邏輯這一層本身（談論形式系統的層次）。Use when working with formal inference: equality axioms, propositional-logic axioms, the part-whole relation, and the metalogical layer that talks about formal systems."
argument-hint: "[自然語言 | 章節名]（裸呼叫＝載入本域待命）"
---

# logic-and-language（公理域的觸發面）

本 skill 是 `logic-and-language` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="logic-and-language: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域；之後的搜尋策略、呈現格式、以及「無足夠相關公理時不製造雜訊」都由它的契約決定，本檔不重述（該契約對顯式呼叫與隱式觸發的模板不同，寫死在這裡必然與它分岔）。

## 本域現有條目（供判斷相關性，非權威內容）

| 章節 | 一句話 |
|------|--------|
| 〈Axiom 1: Transitivity〉 | 等式的遞移性 |
| 〈Axiom 4: Identity of Coincident Objects〉 | 重合對象的同一性 |
| 〈Axiom 5: Part-Whole Relation〉 | 部分與整體的量關係 |
| 〈Axiom P1: Law of Identity〉 | 同一律 |
| 〈Propositional Logic Axioms〉 | 命題邏輯的公理集 |
| 〈Metalogic〉 | 後設邏輯：談論形式系統本身的層次 |

權威內容以 `domains/logic-and-language/` 下的公理檔為準；上表只是章節摘要，不可用於引用。本域為 markdown 格式，引用時用章節名、**不捏造 ID**。 新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 數學陳述該放 theorem 還是 remark | `mathematical-writing`（其 Altitude 是本域 object/metalanguage 區分在寫作工藝上的類比，非等同）|
| 統計推論 | `statistics` |
| 語言習得 | `language-learning` |
