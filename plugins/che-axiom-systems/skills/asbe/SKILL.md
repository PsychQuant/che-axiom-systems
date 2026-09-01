---
name: asbe
description: ASBE（Axiomatic Specification by Example）方法論本身。建立或審查任何公理化系統時使用——一條規則要不要同時有自然語言與形式表達、要不要附違反與合規範例、公理之間是否獨立、規則的推導層級（Axiom → Theorem → Corollary → Rule）、自然語言與形式表達是否等價。Use when authoring or reviewing an axiomatization: dual expression, example grounding, hierarchical derivation, minimal axiom set, semantic equivalence.
argument-hint: "[自然語言 | axiom-ID]（裸呼叫＝載入本域待命）"
---

# asbe（公理域的觸發面）

本 skill 是 `asbe` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="asbe: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域，之後的搜尋、引用上限（inline 最多 3 條）、`📎 相關公理` 清單格式、以及「無足夠相關公理 → 靜默 no-op」都照它的契約走。

## 本域現有條目（供判斷相關性，非權威內容）

| ID | 一句話 |
|----|--------|
| `A1_dual_expression` | 每條規則都要有自然語言與形式兩種表達 |
| `A2_example_grounding` | 每條規則都要有違反與合規範例各至少一個 |
| `A3_hierarchical_derivation` | 規則構成 DAG：公理 → 定理 → 推論 → 規則 |
| `A4_minimal_axiom_set` | 公理須獨立、一致、充分 |
| `A5_semantic_equivalence` | 自然語言與形式表達必須語意等價 |
| `T1_counterexample_power` | 一個好的反例勝過數頁說明 |
| `T2_layer_complementarity` | 自然層與形式層互相救援 |

本域另含兩組**示範用**公理集（code review 的 `A1_correctness` 等、writing 的 `A1_purpose` 等），是 ASBE 的應用範例而非方法論自身的公理。

權威內容以 `domains/asbe/` 下的公理檔為準；上表只是one-liner摘要，不可用於引用。新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 建立或擴充某個領域的公理 | `axiom-create`（skill，非公理域）|
| 驗證公理系統的結構合規 | `axiom-validate`（skill）|
| 數學陳述的擺放 | `mathematical-writing` |
