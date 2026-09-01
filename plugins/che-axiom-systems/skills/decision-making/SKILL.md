---
name: decision-making
description: "決策理論：偏好、效用與悖論。分析選擇行為或設計決策規則時使用——偏好結構、效用表示、不確定性下的期望效用、資訊的價值、風險態度、以及 Allais 這類違反公理的悖論。Use when analysing choice behaviour or designing a decision rule: preference structure, utility representation, expected utility under uncertainty, information value, risk attitude, and the classic paradoxes."
argument-hint: "[自然語言 | 章節名]（裸呼叫＝載入本域待命）"
---

# decision-making（公理域的觸發面）

本 skill 是 `decision-making` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="decision-making: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域；之後的搜尋策略、呈現格式、以及「無足夠相關公理時不製造雜訊」都由它的契約決定，本檔不重述（該契約對顯式呼叫與隱式觸發的模板不同，寫死在這裡必然與它分岔）。

## 本域現有條目（供判斷相關性，非權威內容）

| 章節 | 一句話 |
|------|--------|
| 〈Axiom D1: Preference Structure〉 | 偏好的結構條件 |
| 〈Axiom D2: Utility Representation〉 | 偏好何時可用效用函數表示 |
| 〈Axiom D3: Uncertainty〉 | 不確定性的表述 |
| 〈Axiom D4: Expected Utility〉 | 期望效用準則 |
| 〈Axiom D5: Information〉 | 資訊在決策中的位置 |
| 〈P1: Rationality Principle〉 | 理性的操作定義 |
| 〈P2: Risk Attitude Principle〉 | 風險態度 |
| 〈P3: Value of Information Principle〉 | 資訊的價值：取得資訊值不值得付代價 |
| 〈Allais Paradox〉 | 實際選擇違反獨立性公理的經典反例（在第二個 entry_point）|

權威內容以該域 `domain.yaml` 宣告的兩個 entry_point 為準。`axiomatization_of_decision_making.md` 共 **15 條**（公理 D1–D5、原理 P1–P5、定理 D1–D5）；上表未列的是 P4、P5 與 Theorem D1–D5。`decision_models_and_paradoxes.md` 收各決策模型（期望值、期望效用、主觀期望效用、展望理論、累積展望理論、後悔理論）與四個悖論（St. Petersburg、Allais、Ellsberg、Newcomb），上表只列 Allais。本域為 markdown 格式，引用時用章節名、**不捏造 ID**。 新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 熵與資訊測度的形式性質 | `information-theory` |
| 估計與假設檢定 | `statistics` |
