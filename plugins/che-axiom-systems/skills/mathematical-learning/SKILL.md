---
name: mathematical-learning
description: "數學學習的認知結構。設計數學教材或診斷學習困難時使用——先備知識的依賴結構、學習進程的順序、概念發展的階段、表徵的基礎、認知負荷的上限、程序性與概念性理解的分離。Use when designing mathematics instruction or diagnosing a learning obstacle: prerequisite dependency, learning progression, representation, cognitive load, and the procedural/conceptual split."
argument-hint: "[自然語言 | 章節名]（裸呼叫＝載入本域待命）"
---

# mathematical-learning（公理域的觸發面）

本 skill 是 `mathematical-learning` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="mathematical-learning: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域；之後的搜尋策略、呈現格式、以及「無足夠相關公理時不製造雜訊」都由它的契約決定，本檔不重述（該契約對顯式呼叫與隱式觸發的模板不同，寫死在這裡必然與它分岔）。

## 本域現有條目（供判斷相關性，非權威內容）

| 章節 | 一句話 |
|------|--------|
| 〈Axiom M1: Knowledge Structure Axiom〉 | 數學知識有依賴結構，先備缺口會卡住後續 |
| 〈Axiom M2: Learning Progression Axiom〉 | 學習有順序，跳過會累積債務 |
| 〈Axiom M3: Conceptual Development Axiom〉 | 概念的發展有階段 |
| 〈Axiom M4: Representational Foundation〉 | 表徵是理解的基礎 |
| 〈Axiom M5: Cognitive Load Constraint〉 | 認知資源有上限 |
| 〈Axiom M7: Procedural-Conceptual Separation Principle〉 | 會算不等於懂 |
| 〈Axiom M8: Domain Independence〉 | 一個領域的精熟不自動轉移到另一個 |

### 涵蓋（數字由 CI 重算，勿手改）

- `axiomatization_of_mathematical_learning.md` · h3 · 篩選 `^(Axiom M|P\d|T\d:)` — 共 **33** 條，上表 **7** 條，未列 **26** 條

每行的意思：`路徑` · 條目層級（`id`／`h2`–`h4`）· 篩選正規式（`-` ＝不篩）— 該檔符合條件的條目**共** N 條、**上表**列 M 條、**未列** N−M 條。`.github/workflows/validate.yml` 會重算這三個數並比對：**刪掉表中一列、少算一條、或把某列歸給錯的檔案，都會紅燈**。手寫的計數與省略清單已從下段移除——#29 的 R2 與 R3 各在那裡寫錯過一次（一次算少一條、一次省略清單與表格自相矛盾），這類錯誤靠人維護抓不住。

權威內容以上方涵蓋段所列的 entry_point 為準（公理 M1–M15、原理 P1／P1a／P1b／P2–P12、定理 T1–T4）。同域另有五個未列為 entry_point 的檔案（`information_channel_interference_theory.md`、`humor_in_mathematical_instruction.md`、`mathematical_ability_dependencies.md`、`mathematical_learning_models.md`、`probabilistic_ability_model.md`）。本域為 markdown 格式，引用時用章節名、**不捏造 ID**。新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 學術會議報告的投影片與講稿 | `academic-presentation` |
| 數學論文的陳述擺放 | `mathematical-writing` |
| 語言的習得 | `language-learning` |
