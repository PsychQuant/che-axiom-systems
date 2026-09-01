---
name: weight-control
description: "體重控制的物理與生化約束。討論減重或體組成時使用——質量守恆、碳平衡、元素層級的守恆（CHONNa）、脂肪氧化的化學計量、7700 kcal/kg 從何而來、BMR 與體重的關係、能量赤字的解讀。Use when reasoning about weight change under conservation constraints: mass and carbon balance, element-level bookkeeping, oxidation stoichiometry, and why common rules of thumb take the values they do."
argument-hint: "[自然語言 | axiom-ID]（裸呼叫＝載入本域待命）"
---

# weight-control（公理域的觸發面）

本 skill 是 `weight-control` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="weight-control: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域；之後的搜尋策略、呈現格式、以及「無足夠相關公理時不製造雜訊」都由它的契約決定，本檔不重述（該契約對顯式呼叫與隱式觸發的模板不同，寫死在這裡必然與它分岔）。

## 本域現有條目（供判斷相關性，非權威內容）

| 章節 | 一句話 |
|------|--------|
| 〈A0. Conservation of Mass 質量守恆公理〉 | 物質不會憑空消失，減重是質量的去向問題 |
| 〈A1. Carbon Conservation 碳守恆公理〉 | 脂肪主要以 CO₂ 經呼吸離開身體 |
| 〈A2. Hydrogen Conservation 氫守恆公理〉 | 氫的去向與水的生成 |
| 〈A3. Oxygen Conservation 氧守恆公理〉 | 氧化過程的氧收支 |
| 〈A4. Nitrogen Conservation 氮守恆公理〉 | 氮的收支（CHONNa 的 N）|
| 〈A5. Sodium Conservation 鈉守恆公理〉 | 鈉的收支（CHONNa 的 Na）|
| 〈Level 0: Physics Axioms〉 | 物理層：守恆先於一切代謝敘述 |
| 〈Level 1: Element Axioms (CHONNa)〉 | 元素層：以元素而非「熱量」記帳 |

權威內容以 `domains/weight-control/` 下的公理檔為準；上表只是章節摘要，不可用於引用。本域 `domain.yaml` 宣告 `format: yaml`，引用時用 ID（`axiom-based` 自己的 yaml 範例用的正是本域的 `A0_mass_conservation`）。**注意**：`weight_control_axioms.yaml` 目前無法被嚴格 parser 解析（見 #31），但 `axiom-based` 做的是欄位感知**搜尋**而非 parse，ID 仍可命中；並行的 `.md` 是第二個 entry_point。 新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 統計推導與估計 | `statistics` |
| 決策與風險偏好 | `decision-making` |
