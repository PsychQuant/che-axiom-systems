---
name: japanese-narrative
description: "日本文学における物語構成の公理。日本文學的敘事分析或創作時使用——物語構成、起承転結、余情、物の哀れ、視點與時間、制度層（出版・讀者）對敘事形式的約束。Use when analysing or composing Japanese-tradition narrative: story construction, ki-shō-ten-ketsu, yojō, mono no aware, and the institutional constraints on narrative form."
argument-hint: "[自然語言 | 章節名]（裸呼叫＝載入本域待命）"
---

# japanese-narrative（公理域的觸發面）

本 skill 是 `japanese-narrative` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="japanese-narrative: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域；之後的搜尋策略、呈現格式、以及「無足夠相關公理時不製造雜訊」都由它的契約決定，本檔不重述（該契約對顯式呼叫與隱式觸發的模板不同，寫死在這裡必然與它分岔）。

## 本域現有條目（供判斷相關性，非權威內容）

| 章節 | 一句話 |
|------|--------|
| 〈核心層公理 (Core Axioms: J0-J22)〉 | 物語構成的核心公理群 |
| 〈制度層公理 (Institutional Layer: M1-M11)〉 | 出版・讀者・媒體對敘事形式的制度性約束 |
| 〈導出原理 (Derived Principles)〉 | 由核心層與制度層導出的原理 |
| 〈公理分類〉 | 依主題把公理分組的索引 |

完整索引在 `domains/japanese-narrative/公理/INDEX.md`（本域為日文目錄體系）。

### 涵蓋（數字由 CI 重算，勿手改）

- `公理/INDEX.md` · h2 · 篩選 `-` — 共 **7** 條，上表 **4** 條，未列 **3** 條

每行的意思：`路徑` · 條目層級（`id`／`h2`–`h4`）· 篩選正規式（`-` ＝不篩）— 該檔符合條件的條目**共** N 條、**上表**列 M 條、**未列** N−M 條。`.github/workflows/validate.yml` 會重算這三個數並比對：**刪掉表中一列、少算一條、或把某列歸給錯的檔案，都會紅燈**。手寫的計數與省略清單已從下段移除——#29 的 R2 與 R3 各在那裡寫錯過一次（一次算少一條、一次省略清單與表格自相矛盾），這類錯誤靠人維護抓不住。

權威內容以上方涵蓋段所列的 `公理/INDEX.md` 為準。上表是該索引中**收錄公理的章節**，章節名逐字取自檔內標題；未列的是編務資訊章節（〈使用說明〉〈完成狀況〉〈統計〉）。個別公理（J0–J22、M1–M11）在各節之內、也在 `公理/` 目錄的獨立檔案中，本表不逐條列。本域用自訂體系、非 ASBE schema，引用時以章節名稱呼，**嚴禁捏造 ID**。新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 音樂與歌詞 | `musical-composition` |
| 學術散文寫作 | `apa7-style` |
| 語言習得 | `language-learning` |
