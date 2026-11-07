---
name: mathematical-teaching
description: "數學教學的編排。準備一堂數學課、排複習課或總複習、決定一堂課從哪裡開始時使用——還沒學過的概念從動機開始、已經學過的從提取開始、複習課為什麼不該照第一次上課的流程走、提取時拿不出來的部分怎麼處理。Use when planning a mathematics lesson or a review session: where the lesson should start, how a review differs from a first lesson, and what to do with what students cannot retrieve."
argument-hint: "[自然語言 | 條目 id]（裸呼叫＝載入本域待命）"
---

# mathematical-teaching（公理域的觸發面）

本 skill 是 `mathematical-teaching` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

本域是 `mathematical-education` 的子領域，兄弟領域是 `mathematical-learning`。條目可以從兄弟領域的條目推導（cross-domain-principles.md 第 7 條）。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="mathematical-teaching: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域；之後的搜尋策略、呈現格式、以及「無足夠相關公理時不製造雜訊」都由它的契約決定，本檔不重述。

## 本域現有條目（供判斷相關性，非權威內容）

| ID | 一句話 |
|----|--------|
| `T1_starting_point_by_learner_state` | 教學序列的第一個事件依學生狀態而定：沒學過從動機開始，學過從提取開始，提取不出來的當成沒學過 |

### 涵蓋（數字由 CI 重算，勿手改）

- `mathematical_teaching_axioms.yaml` · id · 篩選 `-` — 共 **1** 條，上表 **1** 條，未列 **0** 條

每行的意思同其他領域的觸發面：`路徑` · 條目層級 · 篩選正規式 — 該檔符合條件的條目共 N 條、上表列 M 條、未列 N−M 條，由 `.github/workflows/validate.yml` 重算比對。

權威內容以上方涵蓋段所列的 entry_point 為準。本域還沒有自己的公理：T1 是從 `mathematical-learning` 的 Axiom M10、Axiom M14、P11 推出的定理。分出本域之前寫的教學條目（M10、P8、P10–P12）仍在 `mathematical-learning`，那裡的標題下有註記。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 學生怎麼學、卡在哪（先備結構、認知負荷、程序與概念的分離） | `mathematical-learning` |
| 問題同時牽涉學與教，或不確定該查哪一邊 | `mathematical-education` |
| 數學論文的陳述擺放 | `mathematical-writing` |
| 學術會議報告的投影片與講稿 | `academic-presentation` |
