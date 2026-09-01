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
| 〈核心層公理 J0–J22〉 | 物語構成的核心公理群（22 條）|
| 〈制度層公理 M1–M11〉 | 出版・讀者・媒體對敘事形式的制度性約束 |
| 〈導出原理〉 | 由核心層與制度層導出的原理 |

完整索引在 `domains/japanese-narrative/公理/INDEX.md`（本域為日文目錄體系）。

權威內容以 `domains/japanese-narrative/` 下的公理檔為準；上表只是章節摘要，不可用於引用。本域用自訂體系、非 ASBE schema，故上表列**章節名**而非 ID——引用時同樣以章節名稱呼，**嚴禁捏造 ID**。 新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 音樂與歌詞 | `musical-composition` |
| 學術散文寫作 | `apa7-style` |
| 語言習得 | `language-learning` |
