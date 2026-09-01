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

本域的權威內容分兩塊。**寫作規範**在三個 yaml entry_point，合計 **41 條**：`writing_style.yaml` 15 條（A1–A9、T1–T3、R1–R3）、`writing_guidelines.yaml` 15 條（R_T1–R_T4、R_V1–R_V2、R_P1–R_P2、R_C1–R_C3、R_B1–R_B2、R_A1–R_A2）、`jars_standards.yaml` 11 條（A1–A6、T1–T3、R1–R2）。上表前 12 列取自這 41 條，其餘 29 條未列——這是計數上的封閉陳述，不是「等」。

**引用格式**（description 的第一個主題）**不在那 41 條裡**：三個 yaml 沒有任何一條談 in-text citation 或參考文獻格式。它在 `03_citation_system/apa_citation_guide.md`，已補列為 entry_point，上表最後 2 列即出自該檔（該檔另有 Setup Requirements、Entry Types and Fields、Date Formatting 等節，本表不列）。不可用於引用。新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 數學陳述的擺放 | `mathematical-writing` |
| 投影片上引用的正確歸屬與可溯源性 | `academic-presentation`（A3 來源忠實、A7 術語與出處）|
| 私人筆記 | `note-writing` |
