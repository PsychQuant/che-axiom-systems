---
name: weight-control
description: 體重控制的物理與生化約束。討論減重或體組成時使用——質量守恆、碳平衡、元素層級的守恆（CHONNa）、脂肪氧化的化學計量、7700 kcal/kg 從何而來、BMR 與體重的關係、能量赤字的解讀。Use when reasoning about weight change under conservation constraints: mass and carbon balance, element-level bookkeeping, oxidation stoichiometry, and why common rules of thumb take the values they do.
argument-hint: "[自然語言 | 章節名]（裸呼叫＝載入本域待命）"
---

# weight-control（公理域的觸發面）

本 skill 是 `weight-control` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="weight-control: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域，之後的搜尋、引用上限（inline 最多 3 條）、`📎 相關公理` 清單格式、以及「無足夠相關公理 → 靜默 no-op」都照它的契約走。

## 本域現有條目（供判斷相關性，非權威內容）

| 章節 | 一句話 |
|------|--------|
| 〈A0. Conservation of Mass 質量守恆公理〉 | 物質不會憑空消失，減重是質量的去向問題 |
| 〈A1. Carbon Conservation 碳守恆公理〉 | 脂肪主要以 CO₂ 經呼吸離開身體 |
| 〈A2. Hydrogen Conservation 氫守恆公理〉 | 氫的去向與水的生成 |
| 〈A3. Oxygen Conservation 氧守恆公理〉 | 氧化過程的氧收支 |
| 〈Level 0: Physics Axioms〉 | 物理層：守恆先於一切代謝敘述 |
| 〈Level 1: Element Axioms (CHONNa)〉 | 元素層：以元素而非「熱量」記帳 |

權威內容以 `domains/weight-control/` 下的公理檔為準；上表只是章節摘要，不可用於引用。本域為 markdown 格式，引用時用章節名、**不捏造 ID**。 **注意**：本域的 `weight_control_axioms.yaml` 目前無法解析（見 #31），實際可搜到的內容來自並行的 `.md`。新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 統計推導與估計 | `statistics` |
| 決策與風險偏好 | `decision-making` |
