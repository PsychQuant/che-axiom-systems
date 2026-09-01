---
name: academic-presentation
description: "學術會議報告的建構與交付紀律。做投影片或寫講稿時使用——開場要不要先給例子、一張投影片塞多少字、時間 slot 抓不準、要不要逐字稿、聽眾跟不上進度、投影片上的數字與引用是否可信、結果講得太滿。Use when building or reviewing conference slides and talk scripts, budgeting a talk to its time slot, or checking claims and citations on a deck. Covers example-first opening, single-channel load, source fidelity, plain register, navigation, and honest framing."
argument-hint: "[自然語言 | axiom-ID]（裸呼叫＝載入本域待命）"
---

# academic-presentation（公理域的觸發面）

本 skill 是 `academic-presentation` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="academic-presentation: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域；之後的搜尋策略、呈現格式、以及「無足夠相關公理時不製造雜訊」都由它的契約決定，本檔不重述（該契約對顯式呼叫與隱式觸發的模板不同，寫死在這裡必然與它分岔）。

## 本域現有條目（供判斷相關性，非權威內容）

| ID | 一句話 |
|----|--------|
| `A1_example_first` | 先給一個聽眾進得去的具體實例，再進抽象 |
| `A2_single_channel` | 不要逼聽眾同時讀密集文字與解析口說 |
| `A3_source_fidelity` | 投影片上每個主張、數字、術語、引用都追溯到權威來源，查證而非憑記憶 |
| `A4_plain_register` | 平實的名詞片語標題與完整平實句；不加裝飾、不留 AI 痕跡 |
| `A5_navigation` | 聽眾要隨時知道自己在哪：開場 outline ＋ 每張投影片的位置標記 |
| `A6_figure_over_dense_table` | 關係能畫就畫，圖或流程圖優於密集表格 |
| `A7_term_grounding` | 對混合聽眾就地定義領域術語，並依主張引正確的原始出處 |
| `A8_honest_framing` | 如實報告結果；講清楚一個結果能顯示什麼、不能顯示什麼，不誇大 |
| `A9_time_budget` | 講稿依 slot 編列並留 buffer，長度用量的、不用猜的 |
| `T1_question_after_hook` | 研究問題接在 hook 之後，不在它之前（由 A1 導出）|
| `T2_verbatim_crutch` | 逐字投影片是條件性的，不是預設（由 A2 導出）|
| `T3_recurring_anchor` | 重複出現的錨定投影片（由 A5 導出）|

權威內容以 `domains/academic-presentation/01_core_axioms/presentation_axioms.yaml` 為準；上表是該檔的**全部 12 條**（公理 A1–A9、定理 T1–T3），封閉列舉、無省略，但只是 one-liner 摘要，不可用於引用。該域另兩個 entry_point（`CLAUDE.md`、`references.md`）是說明與參考資料，不含公理 id。新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 論文與正式散文的寫作格式 | `apa7-style`（引用格式）|
| 數學陳述該放 theorem 還是 remark | `mathematical-writing` |
| 私人筆記 | `note-writing` |
| 教學情境的認知負荷（非會議報告） | `mathematical-learning` |
