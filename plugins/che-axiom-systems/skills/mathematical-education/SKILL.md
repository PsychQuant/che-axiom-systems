---
name: mathematical-education
description: "數學教育的範圍與兩個子領域。問題同時牽涉學生怎麼學與老師怎麼教、不確定該查學習還是教學、或要從學習的公理推導教學條目時使用——數學教育分成學習（mathematical-learning）與教學（mathematical-teaching），兩者之間用 <domain>:<entry> 互相引用。Use when a question about mathematics education spans how students learn and how a lesson is taught, when unsure which of the two applies, or when deriving a teaching entry from a learning one."
argument-hint: "[自然語言 | 章節名]（裸呼叫＝載入本域待命）"
---

# mathematical-education（公理域的觸發面）

本 skill 是 `mathematical-education` 的**自動觸發面**，不是它的內容。路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

本域是父領域（cross-domain-principles.md 第 7 條）：只寫範圍與子領域之間的引用規則，不放公理。公理在兩個子領域裡。

## 做法

用父領域名稱當 hint 時，`axiom-based` 會在本域和兩個子領域一起解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="mathematical-education: <查詢>")
```

已經知道問題屬於哪一邊時，直接用子領域的名稱（`mathematical-learning:`、`mathematical-teaching:`）。

## 本域現有條目（供判斷相關性，非權威內容）

| 章節 | 一句話 |
|------|--------|
| 〈範圍〉 | 數學教育問學生怎麼學、老師怎麼教；寫給同儕的數學論文不在這裡 |
| 〈子領域〉 | 學習與教學各管什麼，以及既有教學條目為什麼留在學習那邊 |
| 〈子領域之間的引用〉 | `<domain>:<entry>` 的寫法、CI 檢查什麼、跨父領域不能推導 |

### 涵蓋（數字由 CI 重算，勿手改）

- `README.md` · h2 · 篩選 `-` — 共 **3** 條，上表 **3** 條，未列 **0** 條

每行的意思同其他領域的觸發面：`路徑` · 條目層級 · 篩選正規式 — 該檔符合條件的條目共 N 條、上表列 M 條、未列 N−M 條，由 `.github/workflows/validate.yml` 重算比對。

權威內容以上方涵蓋段所列的 `README.md` 為準；一級標題是篇名，不列。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 學生怎麼學、卡在哪 | `mathematical-learning` |
| 一堂課怎麼排、從哪裡開始 | `mathematical-teaching` |
| 寫給同儕讀者的數學論文 | `mathematical-writing` |
