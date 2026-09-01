---
name: musical-composition
description: "音楽作曲と理論の公理化。作曲、編曲或分析音樂時使用——音響物理的基礎、音樂時間與韻律、音高結構與階層、緊張與解決的力學、以及偶像音樂的情感喚起原則。Use when composing, arranging, or analysing music: acoustic foundations, musical time and meter, pitch hierarchy, tension-resolution dynamics, and emotion-first principles for idol music."
argument-hint: "[自然語言 | 章節名]（裸呼叫＝載入本域待命）"
---

# musical-composition（公理域的觸發面）

本 skill 是 `musical-composition` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="musical-composition: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域；之後的搜尋策略、呈現格式、以及「無足夠相關公理時不製造雜訊」都由它的契約決定，本檔不重述（該契約對顯式呼叫與隱式觸發的模板不同，寫死在這裡必然與它分岔）。

## 本域現有條目（供判斷相關性，非權威內容）

| 章節 | 一句話 |
|------|--------|
| 〈公理M1: 音響物理学の基礎〉 | 音響物理作為一切音樂結構的底層 |
| 〈公理M2: 音楽的時間と韻律〉 | 音樂時間與韻律 |
| 〈公理M3: 音高構造と階層〉 | 音高的結構與階層 |
| 〈公理M4: 緊張と解決の力学〉 | 緊張與解決的力學 |
| 〈アイドル原理A1: 感情喚起最優先原則〉 | 偶像音樂以情感喚起為最優先 |

權威內容以 `domains/musical-composition/` 下的公理檔為準；上表只是章節摘要，不可用於引用。本域用自訂體系、非 ASBE schema，故上表列**章節名**而非 ID——引用時同樣以章節名稱呼，**嚴禁捏造 ID**。 新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 歌詞的敘事構成 | `japanese-narrative` |
| Suno / SynthV 的歌詞格式慣例 | 全域 rules（非公理域）|
