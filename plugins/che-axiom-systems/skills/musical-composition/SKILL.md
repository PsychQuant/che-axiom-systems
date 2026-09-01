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

### 涵蓋（數字由 CI 重算，勿手改）

- `音楽作曲と理論の公理化.md` · h3 · 篩選 `-` — 共 **29** 條，上表 **5** 條，未列 **24** 條

每行的意思：`路徑` · 條目層級（`id`／`h2`–`h4`）· 篩選正規式（`-` ＝不篩）— 該檔符合條件的條目**共** N 條、**上表**列 M 條、**未列** N−M 條。`.github/workflows/validate.yml` 會重算這三個數並比對：**刪掉表中一列、少算一條、或把某列歸給錯的檔案，都會紅燈**。手寫的計數與省略清單已從下段移除——#29 的 R2 與 R3 各在那裡寫錯過一次（一次算少一條、一次省略清單與表格自相矛盾），這類錯誤靠人維護抓不住。

權威內容以上方涵蓋段所列的 entry_point 為準。涵蓋段數的是 `###` 層條目；該檔另有 `##` 層的分組標題（領域定義、アイドル音楽の根本原理、基本公理、導出原理、多次元技術複合体、文化的・歴史的コンテキスト、応用と拡張、限界と考察、今後の理論的発展、特殊応用ケース），兩層都可引用，但本表與涵蓋段都只處理 `###`。本域用自訂體系、非 ASBE schema，引用時以章節名稱呼，**嚴禁捏造 ID**。新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 歌詞的敘事構成 | `japanese-narrative` |
| Suno / SynthV 的歌詞格式慣例 | 全域 rules（非公理域）|
