---
name: asbe
description: "ASBE（Axiomatic Specification by Example）方法論本身。建立或審查任何公理化系統時使用——一條規則要不要同時有自然語言與形式表達、要不要附違反與合規範例、公理之間是否獨立、規則的推導層級（Axiom → Theorem → Corollary → Rule）、自然語言與形式表達是否等價。Use when authoring or reviewing an axiomatization: dual expression, example grounding, hierarchical derivation, minimal axiom set, semantic equivalence."
argument-hint: "[自然語言 | axiom-ID]（裸呼叫＝載入本域待命）"
---

# asbe（公理域的觸發面）

本 skill 是 `asbe` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="asbe: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域；之後的搜尋策略、呈現格式、以及「無足夠相關公理時不製造雜訊」都由它的契約決定，本檔不重述（該契約對顯式呼叫與隱式觸發的模板不同，寫死在這裡必然與它分岔）。

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

本域另含四條 meta-principle（`M1_llm_optimization`、`M2_human_readability`、`M3_incremental_elaboration`、`M4_dual_format`）——它們屬於方法論自身、只是不在上表；以及**示範用**公理集：writing 那組（`A1_purpose` 等）在現行的 `writing_style_asbe.yaml`；code review 那組（`A1_correctness` 等）**只存在於 `archive/test_output_code_review.yaml`**，而本 repo 的 entry-table CI 刻意跳過 `archive/`，故不可引用。兩組都是 ASBE 的應用範例而非方法論自身的公理。

權威內容以 `domains/asbe/asbe_axioms_bootstrapped.yaml`（該域 `domain.yaml` 宣告的 entry_point）為準；上表列方法論自身的公理與定理共 7 條（A1–A5、T1–T2）；方法論自身的完整內容還要加上上一段的 4 條 meta-principle，合計 11 條。不可用於引用。新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 建立或擴充某個領域的公理 | `axiom-create`（skill，非公理域）|
| 驗證公理系統的結構合規 | `axiom-validate`（skill）|
| 數學陳述的擺放 | `mathematical-writing` |
