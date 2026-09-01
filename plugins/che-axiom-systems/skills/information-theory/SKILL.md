---
name: information-theory
description: "資訊理論：測度與不等式。處理資訊量或編碼問題時使用——熵的公理刻畫、通道容量、編碼定理、data processing 不等式、最大熵原理、互資訊與 KL divergence。Use when reasoning about information measures: the axiomatic characterisation of entropy, channel capacity, coding, the data-processing inequality, and maximum entropy."
argument-hint: "[自然語言 | 章節名]（裸呼叫＝載入本域待命）"
---

# information-theory（公理域的觸發面）

本 skill 是 `information-theory` 公理域的**自動觸發面**，不是它的內容。公理本體、路由、呈現契約、data-guard 全部由 `axiom-based` 負責——本檔刻意不複製那些規則，因為凍結的副本必然 drift。

## 做法

碰到本域主題時，載入 `axiom-based` 並限定在本域內解析：

```
Skill(skill="che-axiom-systems:axiom-based", args="information-theory: <查詢>")
```

`axiom-based` 的 domain-hint shape 會直接命中本域；之後的搜尋策略、呈現格式、以及「無足夠相關公理時不製造雜訊」都由它的契約決定，本檔不重述（該契約對顯式呼叫與隱式觸發的模板不同，寫死在這裡必然與它分岔）。

## 本域現有條目（供判斷相關性，非權威內容）

| 章節 | 一句話 |
|------|--------|
| 〈A1: Information Space Axiom〉 | 資訊空間的界定 |
| 〈A2: Entropy Axiom〉 | 熵的公理刻畫 |
| 〈A3: Channel Axiom〉 | 通道的形式化 |
| 〈A4: Coding Axiom〉 | 編碼的基本約束 |
| 〈A5: Data Processing Axiom〉 | 處理不會增加資訊 |
| 〈P1: Maximum Entropy Principle〉 | 最大熵原理 |
| 〈P2: Channel Coding Principle〉 | 通道編碼原理 |
| 〈T1: Source Coding Theorem〉 | 源編碼定理 |
| 〈T2: Channel Coding Theorem〉 | 通道編碼定理 |
| 〈P3: Rate-Distortion Principle〉 | 容許失真時所需的最小位元率 |
| 〈P4: Information Bottleneck Principle〉 | 壓縮與保留相關資訊之間的取捨 |
| 〈P5: Sufficient Statistic Principle〉 | 充分統計量不丟失關於參數的資訊 |
| 〈T3: Rate-Distortion Theorem〉 | 率失真函數即該取捨的可達邊界 |
| 〈T4: Asymptotic Equipartition Property〉 | 長序列幾乎都落在典型集內 |
| 〈4. Mutual Information〉 | 互資訊的定義與性質（在第二個 entry_point）|
| 〈5. Relative Entropy (Kullback-Leibler Divergence)〉 | KL divergence 的定義與性質（同上）|

### 涵蓋（數字由 CI 重算，勿手改）

- `axiomatization_of_information_theory.md` · h3 · 篩選 `^(A|P|T)\d+:` — 共 **14** 條，上表 **14** 條，未列 **0** 條
- `information_measures_and_inequalities.md` · h3 · 篩選 `-` — 共 **23** 條，上表 **2** 條，未列 **21** 條

每行的意思：`路徑` · 條目層級（`id`／`h2`–`h4`）· 篩選正規式（`-` ＝不篩）— 該檔符合條件的條目**共** N 條、**上表**列 M 條、**未列** N−M 條。`.github/workflows/validate.yml` 會重算這三個數並比對：**刪掉表中一列、少算一條、或把某列歸給錯的檔案，都會紅燈**。手寫的計數與省略清單已從下段移除——#29 的 R2 與 R3 各在那裡寫錯過一次（一次算少一條、一次省略清單與表格自相矛盾），這類錯誤靠人維護抓不住。

權威內容以上方涵蓋段所列的兩個 entry_point 為準。第一檔是公理化本體（A1–A5、P1–P5、T1–T4），上表已完整收錄；第二檔收各測度的定義與不等式，上表只列 description 明確廣告的互資訊與 KL divergence。本域為 markdown 格式，引用時用章節名、**不捏造 ID**。新增公理後**本表要同步**（與 INDEX、TOPICS、domain.yaml 同批）。

## 邊界

| 不屬於本域 | 去處 |
|-----------|------|
| 統計估計與檢定 | `statistics` |
| 效用與偏好 | `decision-making` |
| 教學情境的通道干擾 | `mathematical-learning` |
