---
name: logic-and-language
description: "邏輯系統與後設邏輯。處理形式推論、或談論形式系統本身時使用——等式的遞移性與同餘、部分與整體的量關係、命題與述詞邏輯的公理（同一律、矛盾律、排中律、modus ponens、量詞否定）、形式系統的一致性與健全性與完備性與可決定性，以及後設邏輯結果：Gödel 不完備、Tarski 真值不可定義（真值謂詞、T-schema）、對象語言與後設語言的區分、Löwenheim–Skolem、緊緻性。Use when working with formal inference or reasoning about formal systems: equality and propositional/predicate axioms, the part-whole relation, consistency/soundness/completeness/decidability, and the metalogical results — Godel incompleteness, Tarski undefinability, truth definitions, the object-language vs metalanguage distinction."
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
| 〈Axioms of Equality〉 | 遞移性、加法與減法的同餘、重合對象的同一性（Axiom 1–4）|
| 〈Axioms of Magnitude〉 | 部分與整體的量關係（Axiom 5）|
| 〈Propositional Logic Axioms〉 | 同一律、矛盾律、排中律、modus ponens（P1–P4）|
| 〈Predicate Logic Axioms〉 | 全稱例化、存在概化、量詞否定（Q1–Q3）|
| 〈Classical Logical Systems〉 | 命題邏輯、一階邏輯、高階邏輯 |
| 〈Non-Classical Logical Systems〉 | 直覺主義、模態、多值、相干邏輯 |
| 〈Formal Properties of Logical Systems〉 | 一致性、健全性、完備性、可決定性、表達力 |
| 〈Metalogical Results〉 | Gödel 不完備、Tarski 真值不可定義、Löwenheim–Skolem、緊緻性 |
| 〈Applications to Language and Mathematics〉 | 形式文法與語言理論、數學基礎 |

權威內容以 `domains/logic-and-language/` 下的兩個 entry_point（`axioms_of_logic.md`、`logical_systems_and_metalogic.md`）為準。上表是這兩檔的**全部二級章節**（封閉列舉）；個別公理（Axiom 1–5、P1–P4、Q1–Q3）與個別後設邏輯定理在各節之內，不另列。本域為 markdown 格式，引用時用**章節名**、**不捏造 ID**——上表的章節名逐字取自檔內標題，可直接引用。新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 數學陳述該放 theorem 還是 remark | `mathematical-writing`（其 Altitude 是本域 object/metalanguage 區分在寫作工藝上的類比，非等同）|
| 統計推論 | `statistics` |
| 語言習得 | `language-learning` |
