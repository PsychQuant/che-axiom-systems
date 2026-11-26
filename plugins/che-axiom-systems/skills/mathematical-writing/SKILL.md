---
name: mathematical-writing
description: "數學寫作的擺放與陳述紀律。動筆或修訂正式數學散文時使用——這段該放 theorem 還是 remark、命題陳述太長想精簡、修訂幾輪後但書越積越多、搬段落前要不要先查引用、「這條假設不給什麼」該寫在哪、counterexample 該擺哪裡、remark 引用了後面才出現的命題或數字、引言一開頭就丟出具體例子讀起來突兀、一般情況與簡單情況誰先講、能不能直接寫「不失一般性」。Use when writing or revising theorem/proposition/lemma/remark structure, trimming an overgrown statement, or relocating material in a manuscript. Covers statement placement by altitude, repair-driven altitude drift, the citation-set precondition for re-placement, backward-only dependence in reading order, and the rule that each element (especially a worked example) appears only after the question it answers (generalized to articles in any discipline by academic-writing)."
argument-hint: "[自然語言 | axiom-ID]（裸呼叫＝載入本域待命）"
---

# mathematical-writing（公理域的觸發面）

本 skill 是 `mathematical-writing` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="mathematical-writing: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域；之後的搜尋策略、呈現格式、以及「無足夠相關公理時不製造雜訊」都由它的契約決定，本檔不重述（該契約對顯式呼叫與隱式觸發的模板不同，寫死在這裡必然與它分岔）。

## 本域現有條目（供判斷相關性，非權威內容）

| ID | 一句話 |
|----|--------|
| `A1_altitude_placement` | object-level 關係進 theorem、meta-level 框架性質進 remark，同一內容不兩處重複 |
| `A2_repair_accretion` | 修訂會把 meta-level 但書堆進陳述裡；按輪數重查高度，且remedy 是搬移不是刪除 |
| `A3_replacement_precondition` | 搬動之前必須先知道引用集；引用定址容器而非內容，編譯器兩者都不檢查 |
| `A4_reading_order_dependence` | 陳述只能依賴前文；往後指只能說「在哪」、不能用「什麼」；修法是重排不是刪除（任何學科論文的推廣版：`academic-writing` 的 `A1_no_forward_dependence`）|
| `A5_motivated_by_prefix` | 文章依序閱讀，不只是對錯：例子、定義、結果要在讀者已經有它回答的問題之後才出現；突然冒出的例子會破壞 flow，修法是重排或補承接句（A4 管用什麼、A5 管何時出現；任何學科論文的推廣版：`academic-writing` 的 `A2_motivated_by_prefix`）|
| `A6_prior_result_attribution` | 五項義務：(1) 把結果寫成自己的之前先查文獻（教科書與綜述談這個題目的章節、已引用的文獻與其來源、一個也收預印本的書目索引），並留下查了什麼的紀錄；(2) 把來源換成本文的符號再比，拿不準算不算相關時當作相關；(3) 來源有這個結果、它的一部分、離它只差一段論證、或只陳述而沒有證明，就在陳述處引用並附定位，寫明對方有什麼、符號怎麼對應、本文加了什麼；(4) 只把超出全部來源的部分寫成新的，已被證明的結果與只差一段論證的結果都不列為貢獻；(5) 沒有證明的來源不能拿來代替證明 |
| `A7_general_case_first` | 適用於兩種情形（封閉列舉）：一般形式與簡單形式各有一段處理，或文字寫了「不失一般性」之類的限制。逐個量判定能不能化約（變換與規則都要事先寫得出來，規則不能用到要求的那個值）；能化約的量：先寫一般形式，以命題陳述並證明化約，之後只談簡單形式。不能化約的量才先寫簡單的，並在一般情況開頭說差在假設、論證還是結論的形式。沒有化約命題、或命題不涵蓋的量，不能說「不失一般性」 |
| `T1_negative_space_is_meta` | 「這條假設不給什麼」的主語是假設，故為 meta-level，連它的反例見證也進 remark |

### 涵蓋（數字由 CI 重算，勿手改）

- `mathematical_writing_axioms.yaml` · id · 篩選 `-` — 共 **8** 條，上表 **8** 條，未列 **0** 條

每行的意思：`路徑` · 條目層級（`id`／`h2`–`h4`）· 篩選正規式（`-` ＝不篩）— 該檔符合條件的條目**共** N 條、**上表**列 M 條、**未列** N−M 條。`.github/workflows/validate.yml` 會重算這三個數並比對：**刪掉表中一列、少算一條、或把某列歸給錯的檔案，都會紅燈**。手寫的計數與省略清單已從下段移除——#29 的 R2 與 R3 各在那裡寫錯過一次（一次算少一條、一次省略清單與表格自相矛盾），這類錯誤靠人維護抓不住。

權威內容以上方涵蓋段所列的檔案為準；上表已完整收錄，但只是 one-liner 摘要，不可用於引用。新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 學習數學（認知、先備結構） | `mathematical-learning` |
| 非數學的論文散文（哲學、實證論文）的前向依賴 | `academic-writing`（其 A1 推廣本域 A4）|
| 整篇論文 flow 的紀律：分情況的框架、一個主題一次講完、提出的問題不留著、重排的合法操作、貢獻清單與圖表附錄、預告後文的完整實例 | `academic-writing`（A5–A9 與 A1 的範例）|
| 私人筆記 | `note-writing` |
| APA 引用格式 | `apa7-style` |
| object-language / metalanguage 的**形式**區分 | `logic-and-language`（本域的 Altitude 是它在寫作工藝上的類比，非等同） |
