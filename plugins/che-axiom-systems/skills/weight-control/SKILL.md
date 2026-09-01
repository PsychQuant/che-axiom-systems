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

| ID | 一句話 |
|----|--------|
| `IC_foundation` | 間接測熱作為基礎：7700 kcal/kg 由脂肪分子燃燒熱推導、BMR 與體重的關係都在此節 |
| `A0_mass_conservation` | 物質不會憑空消失，減重是質量的去向問題 |
| `A1_carbon_conservation` | 脂肪主要以 CO₂ 經呼吸離開身體 |
| `A2_hydrogen_conservation` | 氫的去向與水的生成 |
| `A3_oxygen_conservation` | 氧化過程的氧收支 |
| `A4_nitrogen_conservation` | 氮的收支（CHONNa 的 N）|
| `A5_sodium_conservation` | 鈉的收支（CHONNa 的 Na）|
| `A6_CO2_immediate_excretion` | CO₂ 產生後即刻排出，不在體內累積 |
| `T1_macronutrient_composition` | 三大營養素的元素組成——氧化的化學計量由此而來 |
| `T2_glycogen_water_binding` | 肝醣結合水，故短期體重變化不等於脂肪變化 |
| `T3_sodium_water_coupling` | 鈉與水的耦合 |
| `T5_storage_hierarchy` | 儲存的層次順序 |
| `T6_time_scale_separation` | 不同機制的時間尺度分離 |
| `T7_fat_compartment_hierarchy` | 脂肪區隔的層次 |
| `T8_nitrogen_balance_protection` | 氮平衡的保護作用 |
| `D1_weight_loss_target` | 減重目標的定義 |
| `R1_weight_decomposition` | 體重變化的分解規則 |
| `R2_input_inference` | 從觀測反推控制輸入 |

權威內容以 `domains/weight-control/weight_control_axioms.yaml` 為準。本域 `domain.yaml` 宣告 `format: yaml`，引用時用 **ID**——上表列的就是檔內 `id` 欄位的逐字值（`axiom-based` 自己的 yaml 範例用的正是本域的 `A0_mass_conservation`），可直接引用。該檔的頂層條目共 **23 個**：上表 18 個，**未列**的是 `B1_bayesian_personalization`（貝氏個人化）、`S1_weight_curve_structure`（體重曲線結構）、`FL1_body_composition_hierarchy`（體組成層次）、`MLP_comprehensive_inventory`（質量流失路徑清單）、`EP_chonna_tracking`（CHONNa 追蹤）；這五者各自另有巢狀子結構，也不在表內。**兩點誠實記錄**：(1) `weight_control_axioms.yaml` 目前無法被嚴格 parser 解析（見 #31），但 `axiom-based` 做的是欄位感知**搜尋**而非 parse，ID 仍可命中；(2) 並行的 `.md` 是第二個 entry_point，其中的 `T4. Respiratory Exchange Theorem` **只存在於 .md、yaml 沒有對應 id**，引用該條時只能用章節名。 新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 統計推導與估計 | `statistics` |
| 決策與風險偏好 | `decision-making` |
