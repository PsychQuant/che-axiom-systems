---
name: apa7-style
description: "APA 第七版的寫作與引用規範。寫學術稿件或審稿時使用——in-text citation 與參考文獻格式、各段落該用什麼時態、主動被動語態、first person 能不能用、singular they、去冗詞、person-first 用語、避免擬人化（表格不會 show）。Use when writing or reviewing scholarly manuscripts under APA 7th: citation format, tense per section, voice, bias-free language, and conciseness rules."
argument-hint: "[自然語言 | axiom-ID]（裸呼叫＝載入本域待命）"
---

# apa7-style（公理域的觸發面）

本 skill 是 `apa7-style` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="apa7-style: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域；之後的搜尋策略、呈現格式、以及「無足夠相關公理時不製造雜訊」都由它的契約決定，本檔不重述（該契約對顯式呼叫與隱式觸發的模板不同，寫死在這裡必然與它分岔）。

## 本域現有條目（供判斷相關性，非權威內容）

| ID | 一句話 |
|----|--------|
| `A1_clarity` | 學術寫作必須清楚 |
| `A3_economy` | 用最少的字達到最大的清晰 |
| `A5_tense_consistency` | 每個章節維持一致的主要時態 |
| `A7_paragraph_unity` | 一段一個主要概念 |
| `A9_parallel_structure` | 條列項目須有平行的語法結構 |
| `T1_known_new` | 從已知開始、以新資訊結尾 |
| `R_T2_method_past_tense` | Method 章節用過去式 |
| `R_P2_singular_they` | 未指名的個人用 they |
| `R_B1_people_first` | 人在前、狀況在後 |
| `R_A2_table_references` | 表格是 present／display，不是 show／demonstrate |
| `A6_replicability` | 量化研究必須可複製 |
| `T1_mixed_methods_dual_standards` | 混合方法須同時滿足量化與質性標準 |
| 〈Citation Commands〉 | in-text citation 的各種形式與特殊指令 |
| 〈Entry Types and Fields〉 | 參考文獻條目的類型與 APA 專用欄位 |

### 涵蓋（數字由 CI 重算，勿手改）

- `01_core_axioms/writing_style.yaml` · id · 篩選 `-` — 共 **15** 條，上表 **6** 條，未列 **9** 條
- `01_core_axioms/writing_guidelines.yaml` · id · 篩選 `-` — 共 **15** 條，上表 **4** 條，未列 **11** 條
- `01_core_axioms/jars_standards.yaml` · id · 篩選 `-` — 共 **11** 條，上表 **2** 條，未列 **9** 條
- `03_citation_system/apa_citation_guide.md` · h2 · 篩選 `-` — 共 **12** 條，上表 **2** 條，未列 **10** 條

每行的意思：`路徑` · 條目層級（`id`／`h2`–`h4`）· 篩選正規式（`-` ＝不篩）— 該檔符合條件的條目**共** N 條、**上表**列 M 條、**未列** N−M 條。`.github/workflows/validate.yml` 會重算這三個數並比對：**刪掉表中一列、少算一條、或把某列歸給錯的檔案，都會紅燈**。手寫的計數與省略清單已從下段移除——#29 的 R2 與 R3 各在那裡寫錯過一次（一次算少一條、一次省略清單與表格自相矛盾），這類錯誤靠人維護抓不住。

本域的權威內容分兩塊，都列在上方涵蓋段。**寫作規範**在三個 yaml entry_point；**引用格式**（description 的第一個主題）**不在那些公理裡**——三個 yaml 沒有任何一條談 in-text citation 或參考文獻格式，它在 `03_citation_system/apa_citation_guide.md`，已補列為 entry_point。上表不可用於引用。新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 數學陳述的擺放 | `mathematical-writing` |
| 投影片上引用的正確歸屬與可溯源性 | `academic-presentation`（A3 來源忠實、A7 術語與出處）|
| 私人筆記 | `note-writing` |
