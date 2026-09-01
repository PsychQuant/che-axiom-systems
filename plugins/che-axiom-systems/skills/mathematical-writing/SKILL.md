---
name: mathematical-writing
description: "數學寫作的擺放與陳述紀律。動筆或修訂正式數學散文時使用——這段該放 theorem 還是 remark、命題陳述太長想精簡、修訂幾輪後但書越積越多、搬段落前要不要先查引用、「這條假設不給什麼」該寫在哪、counterexample 該擺哪裡。Use when writing or revising theorem/proposition/lemma/remark structure, trimming an overgrown statement, or relocating material in a manuscript. Covers statement placement by altitude, repair-driven altitude drift, and the citation-set precondition for re-placement."
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
| `T1_negative_space_is_meta` | 「這條假設不給什麼」的主語是假設，故為 meta-level，連它的反例見證也進 remark |

### 涵蓋（數字由 CI 重算，勿手改）

- `mathematical_writing_axioms.yaml` · id · 篩選 `-` — 共 **4** 條，上表 **4** 條，未列 **0** 條

每行的意思：`路徑` · 條目層級（`id`／`h2`–`h4`）· 篩選正規式（`-` ＝不篩）— 該檔符合條件的條目**共** N 條、**上表**列 M 條、**未列** N−M 條。`.github/workflows/validate.yml` 會重算這三個數並比對：**刪掉表中一列、少算一條、或把某列歸給錯的檔案，都會紅燈**。手寫的計數與省略清單已從下段移除——#29 的 R2 與 R3 各在那裡寫錯過一次（一次算少一條、一次省略清單與表格自相矛盾），這類錯誤靠人維護抓不住。

權威內容以上方涵蓋段所列的檔案為準；上表已完整收錄，但只是 one-liner 摘要，不可用於引用。新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 學習數學（認知、先備結構） | `mathematical-learning` |
| 私人筆記 | `note-writing` |
| APA 引用格式 | `apa7-style` |
| object-language / metalanguage 的**形式**區分 | `logic-and-language`（本域的 Altitude 是它在寫作工藝上的類比，非等同） |
