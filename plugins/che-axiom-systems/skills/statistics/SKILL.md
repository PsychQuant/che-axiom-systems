---
name: statistics
description: "統計與資料科學的推導紀律。做統計推導或審查統計主張時使用——迴歸係數在尺度變換下怎麼變、估計量是否無偏、MSE 與偏誤變異數拆解、最大概似、假設檢定的解讀、模型近似的邊界。Use when deriving or reviewing statistical claims: rescaling invariance, estimator properties, bias-variance decomposition, likelihood, hypothesis testing, and the limits of model approximation."
argument-hint: "[自然語言 | 章節名]（裸呼叫＝載入本域待命）"
---

# statistics（公理域的觸發面）

本 skill 是 `statistics` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="statistics: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域；之後的搜尋策略、呈現格式、以及「無足夠相關公理時不製造雜訊」都由它的契約決定，本檔不重述（該契約對顯式呼叫與隱式觸發的模板不同，寫死在這裡必然與它分岔）。

## 本域現有條目（供判斷相關性，非權威內容）

| 章節 | 一句話 |
|------|--------|
| 〈Axiom S1: Probability Foundation〉 | 機率論作為統計推論的基礎 |
| 〈Axiom DS2: Statistical Uncertainty〉 | 資料帶有不可消除的不確定性 |
| 〈Axiom DS3: Model Approximation〉 | 模型是近似，不是真相 |
| 〈Axiom DS4: Inductive Inference〉 | 從樣本到母體是歸納，非演繹 |
| 〈P3: Bias-Variance Principle〉 | 偏誤與變異數的取捨 |
| 〈Principle R1: Invariance of Fit Quality〉 | 尺度變換不改變擬合品質 |
| 〈Theorem RT1: General Linear Transformation〉 | 線性變換下的參數轉換規則 |
| 〈Theorem SLR-T2: Gauss-Markov〉 | 最小平方估計的最佳線性無偏性 |
| 〈P1: Statistical Estimation Principle〉 | 估計量以偏誤、變異、一致性、效率評價；最大概似與動差法、貝氏法都在此節 |
| 〈P2: Hypothesis Testing Principle〉 | 檢定衡量對虛無假設的證據，並權衡型一與型二錯誤 |

權威內容以 `domains/statistics/axiomatization_of_statistics_and_data_science.md` 為準，該檔共 **23 條**：公理 S1–S2 與 DS1–DS5、原理 P1–P8、定理 S1–S3 與 DS1–DS5。上表取其中 6 列，**未列**的是 S2、DS1、DS5、P4–P8、Theorem S1–S3 與 Theorem DS1–DS5。另三列（Principle R1、Theorem RT1、Theorem SLR-T2）出自同域的 `SM00_1_rescaling_of_simple_linear_regression.md`，該檔未被列為 entry_point、只靠全文搜尋觸及。宣告的第二個 entry_point `00_principles.md`（MP1–MP3、P1–P5、R1–R5）談的是公理化方法論本身、不是統計，該錯配另案處理（#31）。本域為 markdown 格式，引用時用章節名、**不捏造 ID**。 新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 學術論文的引用格式 | `apa7-style` |
| 定理該放 theorem 還是 remark | `mathematical-writing` |
| 效用與偏好的決策公理 | `decision-making` |
| 熵與資訊測度 | `information-theory` |
