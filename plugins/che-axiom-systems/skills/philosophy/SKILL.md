---
name: philosophy
description: "他者作為起點的存在論立場。討論主體與他者、倫理責任的來源、或歐陸哲學的既有立場時使用——為什麼起點不是自我也不是語言而是他者、黑格爾的止揚為何不是唯一出路、他人是否必然是地獄、對他者的回應是否只能是倫理上的降服、他者的有機性作為存在論基礎。Use when discussing subjectivity and the other, where ethical responsibility comes from, or the standard continental positions: why the starting point is the other rather than the self or language, and the critiques of sublation, of the other as hell, and of infinite responsibility."
argument-hint: "[自然語言 | 章節名]（裸呼叫＝載入本域待命）"
---

# philosophy（公理域的觸發面）

本 skill 是 `philosophy` 公理域的**自動觸發面**，不是它的內容。內容本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="philosophy: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域；之後的搜尋策略、呈現格式、以及「無足夠相關內容時不製造雜訊」都由它的契約決定，本檔不重述（該契約對顯式呼叫與隱式觸發的模板不同，寫死在這裡必然與它分岔）。

## 本域現有條目（供判斷相關性，非權威內容）

**誠實記錄本域的性質**：這是一篇 30 行的單篇隨筆，`domain.yaml` 宣告 `format: freeform`、`maturity: legacy`。它**沒有公理 id、沒有 ASBE 結構**，只有一個立場與其論證。引用時用**章節名**，`axiom-based` 對 freeform 域的模板本來就是「entry-point 相對路徑 ＋ 摘錄」，不需要也不得捏造 ID。

| 章節 | 一句話 |
|------|--------|
| 〈序論〉 | 起點不是自我也不是語言，而是他者；只有一個人時倫理與制度無從建立 |
| 〈既有立場的反省〉 | 對黑格爾的止揚、薩特的「他人即地獄」、列維納斯的無限責任逐一提問 |
| 〈自我立場的提出〉 | 本文自己的主張 |
| 〈他者的有機性作為存在論基礎〉 | 以他者的有機性取代封閉的主體性作為存在論起點 |
| 〈批判與宣言〉 | 對既有框架的批判與立場宣告 |
| 〈結語〉 | 收束 |

### 涵蓋（數字由 CI 重算，勿手改）

- `My Essey/他者作為一切的起點 —— 對歐陸哲學的批判與重構.md` · h2 · 篩選 `-` — 共 **6** 條，上表 **6** 條，未列 **0** 條

每行的意思：`路徑` · 條目層級（`id`／`h2`–`h4`）· 篩選正規式（`-` ＝不篩）— 該檔符合條件的條目**共** N 條、**上表**列 M 條、**未列** N−M 條。`.github/workflows/validate.yml` 會重算這三個數並比對：**刪掉表中一列、少算一條、或把某列歸給錯的檔案，都會紅燈**。手寫的計數與省略清單已從下段移除——#29 的 R2 與 R3 各在那裡寫錯過一次（一次算少一條、一次省略清單與表格自相矛盾），這類錯誤靠人維護抓不住。

權威內容以上方涵蓋段所列的 entry_point 為準；上表已收錄該檔的全部二級章節（一級標題是篇名，不列）。不可用於引用。內容增修後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 形式系統、真值、後設邏輯 | `logic-and-language` |
| 決策與偏好的形式理論 | `decision-making` |
| 學術散文的寫作格式 | `apa7-style` |
