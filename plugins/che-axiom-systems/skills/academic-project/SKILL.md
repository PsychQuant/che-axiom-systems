---
name: academic-project
description: "學術研究專案的管理紀律：一篇稿件的資料夾裡要放什麼、各種材料放哪裡、什麼不能離開本機、交出稿件前要做什麼。開新的研究專案、整理專案資料夾時使用——references 資料夾要放哪些文獻、引用的文獻沒有全文怎麼辦、PDF 從哪裡複製過來、稿件裡的數字從哪裡來、原始資料可不可以直接改、data/raw 與 data/processed 怎麼分、逐字稿或付費論文的 PDF 能不能推到 GitHub、archive 資料夾裡的舊檔能不能刪、專案裡的外部 repo 要放在哪個資料夾、量測工具要不要升到最新版、改完 tex 要不要先編譯再 commit。Use when setting up or tidying a research project folder: what the references folder must hold, where full-text PDFs come from, how reported numbers are traced to programs, raw versus processed data, what must stay off git remotes, the append-only archive, naming folders for nested repositories, pinning measuring instruments, and compiling the manuscript after every edit."
argument-hint: "[自然語言 | axiom-ID]（裸呼叫＝載入本域待命）"
---

# academic-project（公理域的觸發面）

本 skill 是 `academic-project` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="academic-project: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域；之後的搜尋策略、呈現格式、以及「無足夠相關公理時不製造雜訊」都由它的契約決定，本檔不重述（該契約對顯式呼叫與隱式觸發的模板不同，寫死在這裡必然與它分岔）。

## 本域現有條目（供判斷相關性，非權威內容）

| ID | 一句話 |
|----|--------|
| `A1_references_hold_every_cited_work` | 稿件引用的每一篇文獻（文章、書、章、報告），全文（PDF 與可搜尋的文字檔）都在專案的 references 資料夾；缺的先換管道取得、存進文獻庫再匯出，真的拿不到才換文獻 |
| `A2_one_original_per_full_text` | references 資料夾裡的每篇文獻在文獻庫有一份全文正本；專案裡的 PDF 是從正本匯出的副本，文字檔記下來源 PDF 的 digest；副本不改，正本換了就重新匯出 |
| `A3_every_number_traceable` | 研究算出來、稿件報告的每個值（與由它們做成的表、圖）都有紀錄：程式、輸入、版本、重現指令、種子與機器（需要時）；封閉三類免紀錄：引自文獻的值、設計常數、書目數字 |
| `A4_raw_data_immutable` | 分析根目錄下的資料與輸出分三類（封閉）：data/raw 不改、data/processed 由程式產生可重跑、output 另放；路徑從分析的根目錄寫起 |
| `A5_third_party_and_copyrighted_off_remote` | 三類材料不進任何 remote（私有的也算）：第三方原始話語、他人有著作權的全文、不能轉給別人的資料（它們的轉檔與加工版仍屬同類）；自己的稿件、程式與整理過的逐字稿可以 |
| `A6_archive_append_only` | archive/ 只增不改：不刪、不搬、不覆寫、不編輯，要改先明確解鎖；遇到 archived/ 就在解鎖後改名 archive/ |
| `A7_nested_repos_named_by_role` | 專案裡的別的 repo 依角色命名（封閉五類：references/repos、deps、data、instruments、自己的程式），不只寫 repos/ |
| `A8_frozen_instruments` | 研究量測或比較的工具（不是一般統計軟體）在研究期間固定版本；要升級先寫 deviation note，前後是不同條件，結果記下版本 |
| `A9_compile_after_every_edit` | LaTeX 稿件的原始碼（封閉列舉：主檔與它引入的檔、書目、樣式、圖）改完就跑完整編譯，五個計數（未定義、重複 label、重複目的地、錯誤、書目警告）都是 0 才 commit |

### 涵蓋（數字由 CI 重算，勿手改）

- `academic_project_axioms.yaml` · id · 篩選 `-` — 共 **9** 條，上表 **9** 條，未列 **0** 條

每行的意思：`路徑` · 條目層級（`id`／`h2`–`h4`）· 篩選正規式（`-` ＝不篩）— 該檔符合條件的條目**共** N 條、**上表**列 M 條、**未列** N−M 條。`.github/workflows/validate.yml` 會重算這三個數並比對：**刪掉表中一列、少算一條、或把某列歸給錯的檔案，都會紅燈**。

權威內容以上方涵蓋段所列的檔案為準；上表已完整收錄，但只是 one-liner 摘要，不可用於引用。新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 稿件正文本身的順序與結構（前向依賴、例子擺放、文獻第一次介紹時附什麼） | `academic-writing` |
| 引用與參考文獻的格式 | `apa7-style` |
| 口頭報告、投影片、講稿 | `academic-presentation` |
| 私人筆記 | `note-writing` |
| 統計方法本身 | `statistics` |
