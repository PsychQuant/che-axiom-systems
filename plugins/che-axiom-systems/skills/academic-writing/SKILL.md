---
name: academic-writing
description: "學術論文寫作的順序與結構紀律，適用任何學科（哲學、實證科學、數學）。寫或修訂期刊論文時使用——這句用到的術語、符號、原則後面才定義、「見第六節」到底算預告還是前向引用、引言最後的導覽段可不可以指向後文、先陳述主張再把論證放到後面行不行、定義寫在前面但內容要到後面才給、要把段落搬前搬後。Use when writing or revising a scholarly article in any discipline and a sentence leans on a term, symbol, principle, number or quotation given only later, or when deciding whether a forward pointer is a roadmap, a promissory note, or a defect. Covers no forward dependence and the rule that each element (an example, a finding, a quotation) appears only after the question it answers (generalizing mathematical-writing's A4 and A5 beyond formal mathematics). 也用於：開場就丟出案例或結果讀起來突兀、例子擺在哪裡、段落之間缺承接；引用文獻放在哪裡、介紹一個估計量或方法時要不要順便交代出處與性質、文獻回顧要不要獨立成節；引言裡可不可以先講自己的結果、結果會不會太早揭露、研究問題之前可以放什麼；整篇的 flow：分情況討論要不要先列出全部情況、同一個主題在兩處講、讀者讀到這裡有沒有問題沒被回答、為了順而搬動或合併段落哪些做法合法、後文的完整實例能不能先預告、貢獻清單與圖表附錄怎麼跟著 flow 規劃。"
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
| `A4_own_results_after_question` | 引言在提出研究問題之前，只寫已知的事（附引用）、定義與情境、還不知道的事；文章自己證明、算出或發現的結果放在問題之後。兩種不算（封閉列舉）：只呈現情境、不說答案方向的示例數值，以及只說在哪裡處理的導覽。引言沒有研究問題句（開頭就陳述主要定理的寫法）時不適用 |
| `A5_case_frame` | 分情況討論要有框架：第一個情況之前先說問題、範圍、全部情況與順序；之後照這個順序討論，每個情況一次講完；列出的情況合起來涵蓋整個範圍。沒有在自己的位置討論的情況只有兩種處置（封閉列舉）：延後並說在哪裡、排除並說理由。只討論一個情況並指向例外在哪裡處理的結果不算分情況討論 |
| `A6_topic_once` | 一個主題在一處講完：為同一主題增加內容的 idea 要相連，離開之後不回頭補。三種不算回頭（封閉列舉）：向後引用、離開時已說明剩下哪一部分在哪裡處理、框架性的章節（摘要、引言、A3 的文獻回顧節、結尾的討論或結論）。修法是搬過去合併，不是刪掉 |
| `A7_no_open_question` | 文字讓讀者產生的問題不留著：提出問題的 idea 或下一個 idea 要回答它、說在哪裡回答、或說本文不回答（封閉列舉）。文字提出問題的方式有四種（封閉列舉）：直接問、沒有根據的主張、沒有理由的選擇、與前文看似衝突。A2 的反方向：A2 管答案之前要有問題，這條管問題之後要有答案 |
| `A8_rearrangement_operations` | flow 為了順可以重排，合法的操作是封閉列舉：對調、往前移、往後移、合併、拆開，各有條件（以 A1、A2、A6 表述）；重排前後主張的集合不變。刪除、重複、插入新句子都不是重排。這份清單是提案，等作者刪改 |
| `A9_contributions_displays_appendix` | 貢獻清單、圖表、附錄跟著 flow 規劃：每項貢獻至少有一個 idea 承載；每個圖表有一個歸屬的 idea；每一節寫明哪些內容放附錄（可以是沒有），每個附錄項目在正文有歸屬的 idea |

### 涵蓋（數字由 CI 重算，勿手改）

- `academic_writing_axioms.yaml` · id · 篩選 `-` — 共 **9** 條，上表 **9** 條，未列 **0** 條

每行的意思：`路徑` · 條目層級（`id`／`h2`–`h4`）· 篩選正規式（`-` ＝不篩）— 該檔符合條件的條目**共** N 條、**上表**列 M 條、**未列** N−M 條。`.github/workflows/validate.yml` 會重算這三個數並比對：**刪掉表中一列、少算一條、或把某列歸給錯的檔案，都會紅燈**。

權威內容以上方涵蓋段所列的檔案為準；上表已完整收錄，但只是 one-liner 摘要，不可用於引用。新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 數學陳述該放 theorem 還是 remark、正式數學散文的定理架構（本域 A1 的母公理 A4 也在這裡） | `mathematical-writing` |
| 一般情況與簡單情況誰先講：先講一般情況、以命題化約到簡單情況、之後只談簡單情況（`A7_general_case_first`） | `mathematical-writing` |
| APA 引用與格式 | `apa7-style` |
| 口頭報告、投影片、講稿 | `academic-presentation` |
| 專案資料夾怎麼管：references 放哪些全文、數字的來源紀錄、原始資料、什麼不能推上 remote | `academic-project` |
| 私人筆記 | `note-writing` |
