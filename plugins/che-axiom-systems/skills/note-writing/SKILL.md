---
name: note-writing
description: "Markdown 筆記的格式紀律。寫或整理 .md 筆記時使用——標題跳級、標題與列表前後要不要空行、列表標記後的空格、無序列表用哪個符號、縮排不一致、行尾空格與 Tab、連續空行、程式碼區塊前後空行、一份文件該有幾個頂級標題、粗體與數學公式怎麼寫。Use when writing or cleaning up Markdown notes: heading increments and surrounding blank lines, list markers and indentation, trailing spaces, hard tabs, fenced code block spacing, single top-level heading."
argument-hint: "[自然語言 | 章節名]（裸呼叫＝載入本域待命）"
---

# note-writing（公理域的觸發面）

本 skill 是 `note-writing` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="note-writing: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域；之後的搜尋策略、呈現格式、以及「無足夠相關公理時不製造雜訊」都由它的契約決定，本檔不重述（該契約對顯式呼叫與隱式觸發的模板不同，寫死在這裡必然與它分岔）。

## 本域現有條目（供判斷相關性，非權威內容）

本域 `domain.yaml` 宣告 `format: markdown`、`maturity: legacy`，引用時用**章節名**（`axiom-based` 的呈現契約對 markdown 域明訂**嚴禁捏造 ID**）。原始標題帶 emoji 前綴，下表只列文字部分。

| 章節 | 一句話 |
|------|--------|
| 〈關鍵規則（與筆記格式最相關）〉 | markdownlint MD001／MD003／MD004／MD005／MD007／MD009／MD010／MD012／MD022／MD025／MD030／MD031／MD032／MD033 的對照表 |
| 〈標題格式〉 | 層級逐級遞增、前後空行、ATX 樣式一致、整份只有一個頂級標題 |
| 〈列表格式〉 | 前後空行、標記統一、項目縮排一致、標記後一個空格 |
| 〈空行和空格〉 | 無行尾空格、不用 Tab、不超過一個連續空行、程式碼區塊前後空行 |
| 〈其他格式〉 | 粗體、引用區塊、數學公式（`$...$` / `$$...$$`）的寫法 |
| 〈Markdown 規範來源〉 | CommonMark、markdownlint、vscode-markdown 三個來源與其位置 |
| 〈應用於教學筆記〉 | 這套格式落在教學筆記上的用法 |

### 涵蓋（數字由 CI 重算，勿手改）

- `README.md` · h2 · 篩選 `-` — 共 **5** 條，上表 **2** 條，未列 **3** 條
- `README.md` · h3 · 篩選 `-` — 共 **9** 條，上表 **4** 條，未列 **5** 條
- `README.md` · h4 · 篩選 `-` — 共 **2** 條，上表 **1** 條，未列 **1** 條

每行的意思：`路徑` · 條目層級（`id`／`h2`–`h4`）· 篩選正規式（`-` ＝不篩）— 該檔符合條件的條目**共** N 條、**上表**列 M 條、**未列** N−M 條。`.github/workflows/validate.yml` 會重算這三個數並比對：**刪掉表中一列、少算一條、或把某列歸給錯的檔案，都會紅燈**。手寫的計數與省略清單已從下段移除——#29 的 R2 與 R3 各在那裡寫錯過一次（一次算少一條、一次省略清單與表格自相矛盾），這類錯誤靠人維護抓不住。

權威內容以上方涵蓋段所列的 `README.md`（該域 `domain.yaml` 宣告的 entry_point）為準。上表橫跨該檔的三個標題層級，故涵蓋段分三行。〈關鍵規則（與筆記格式最相關）〉一節內含 markdownlint 規則的對照表，本表不逐條列；**那些規則的權威定義指向 `git/markdownlint/doc/` ，該目錄不在本 repo 內**，故只有該節的對照表與檢查清單是自足可引用的。上表不可用於引用。新增內容後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 論文與正式散文的格式與引用 | `apa7-style` |
| 數學陳述該放 theorem 還是 remark | `mathematical-writing` |
| 投影片與講稿 | `academic-presentation` |
