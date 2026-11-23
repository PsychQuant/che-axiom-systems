---
name: academic-writing
description: "學術論文寫作的順序與結構紀律，適用任何學科（哲學、實證科學、數學）。寫或修訂期刊論文時使用——這句用到的術語、符號、原則後面才定義、「見第六節」到底算預告還是前向引用、引言最後的導覽段可不可以指向後文、先陳述主張再把論證放到後面行不行、定義寫在前面但內容要到後面才給、要把段落搬前搬後。Use when writing or revising a scholarly article in any discipline and a sentence leans on a term, symbol, principle, number or quotation given only later, or when deciding whether a forward pointer is a roadmap, a promissory note, or a defect. Covers no forward dependence and the rule that each element (an example, a finding, a quotation) appears only after the question it answers (generalizing mathematical-writing's A4 and A5 beyond formal mathematics). 也用於：開場就丟出案例或結果讀起來突兀、例子擺在哪裡、段落之間缺承接；引用文獻放在哪裡、介紹一個估計量或方法時要不要順便交代出處與性質、文獻回顧要不要獨立成節。"
argument-hint: "[自然語言 | axiom-ID]（裸呼叫＝載入本域待命）"
---

# academic-writing（公理域的觸發面）

本 skill 是 `academic-writing` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="academic-writing: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域；之後的搜尋策略、呈現格式、以及「無足夠相關公理時不製造雜訊」都由它的契約決定，本檔不重述（該契約對顯式呼叫與隱式觸發的模板不同，寫死在這裡必然與它分岔）。

## 本域現有條目（供判斷相關性，非權威內容）

| ID | 一句話 |
|----|--------|
| `A1_no_forward_dependence` | 一句話只能依賴讀者已讀過的術語、符號、定義、原則、結果、數字、引文；往後指只有兩種合法情形（導覽、預告後證），封閉列舉；修法是重排不是刪除。推廣 `mathematical-writing` 的 `A4_reading_order_dependence` |
| `A2_motivated_by_prefix` | 文章依序閱讀，不只是對錯：例子、定義、圖表、結果、引文要在讀者已經有它回答的問題之後才出現；開場就丟出案例或結果會破壞 flow，修法是重排或補承接句（A1 管依賴什麼、A2 管何時出現）。推廣 `mathematical-writing` 的 `A5_motivated_by_prefix` |
| `A3_literature_at_introduction` | 從文獻借來的對象（估計量、方法、模型、量表、資料集、定理）第一次介紹時，同一處附一兩句文獻：出處與文章依賴的性質（關鍵性質第一次就交代）；大範圍回顧放在後面專門的章節；這一兩句只能寫原文說過的話 |

### 涵蓋（數字由 CI 重算，勿手改）

- `academic_writing_axioms.yaml` · id · 篩選 `-` — 共 **3** 條，上表 **3** 條，未列 **0** 條

每行的意思：`路徑` · 條目層級（`id`／`h2`–`h4`）· 篩選正規式（`-` ＝不篩）— 該檔符合條件的條目**共** N 條、**上表**列 M 條、**未列** N−M 條。`.github/workflows/validate.yml` 會重算這三個數並比對：**刪掉表中一列、少算一條、或把某列歸給錯的檔案，都會紅燈**。

權威內容以上方涵蓋段所列的檔案為準；上表已完整收錄，但只是 one-liner 摘要，不可用於引用。新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 數學陳述該放 theorem 還是 remark、正式數學散文的定理架構（本域 A1 的母公理 A4 也在這裡） | `mathematical-writing` |
| APA 引用與格式 | `apa7-style` |
| 口頭報告、投影片、講稿 | `academic-presentation` |
| 私人筆記 | `note-writing` |
