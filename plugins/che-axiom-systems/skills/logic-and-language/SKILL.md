---
name: logic-and-language
description: 邏輯系統與後設邏輯。處理形式推論或語意問題時使用——等式公理、命題邏輯、真值定義、object language 與 metalanguage 的區分、T-schema、形式系統的界限。Use when working with formal inference or semantics: equality and propositional axioms, truth definitions, the object-language / metalanguage distinction, T-schema, and the limits of formal systems.
argument-hint: "[自然語言 | 章節名]（裸呼叫＝載入本域待命）"
---

# logic-and-language（公理域的觸發面）

本 skill 是 `logic-and-language` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="logic-and-language: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域，之後的搜尋、引用上限（inline 最多 3 條）、`📎 相關公理` 清單格式、以及「無足夠相關公理 → 靜默 no-op」都照它的契約走。

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
