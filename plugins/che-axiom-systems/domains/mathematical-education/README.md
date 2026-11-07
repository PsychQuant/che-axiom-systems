# Mathematical Education（數學教育）

父領域（cross-domain-principles.md 第 7 條）。本檔只寫範圍與子領域之間的引用規則，不放公理。

## 範圍

數學教育問兩件事：學生怎麼把數學學起來，以及老師怎麼安排教學讓學生學得起來。前者是 `mathematical-learning`，後者是 `mathematical-teaching`。

寫給同儕讀者的數學論文不在這裡：那是 `mathematical-writing`，讀者是同儕，不是學生。

## 子領域

| 子領域 | 管什麼 | 例子 |
|--------|--------|------|
| `mathematical-learning` | 學生怎麼學、卡在哪：知識的依賴結構、學習進程、表徵、認知負荷、程序與概念的分離 | 先備缺口為什麼會卡住後面的單元 |
| `mathematical-teaching` | 老師怎麼排一堂課：第一個事件放什麼、複習課和新課有什麼不同 | 複習課該從開場情境還是從提取開始 |

分出兩個子領域之前寫的教學條目（M10、P8、P10–P12）留在 `mathematical-learning`，標題下加了註記，指向 `mathematical-teaching`。依 SCD2，既有條目不搬。

## 子領域之間的引用

兩個子領域的 `derives_from` 可以引用彼此的條目，寫法是 `<domain>:<entry>`，從第一個 `:` 切開：

- 對方是 yaml 領域：`entry` 寫條目 id。
- 對方是 markdown 領域：`entry` 寫完整標題，例如 `mathematical-learning:Axiom M10: Instructional Event Organization Axiom`。只寫「Axiom M10」對不到。

CI 會檢查兩件事：前段是同一個父領域底下的兄弟領域，後段在對方解析得到。和這兩個子領域不同父領域的領域（例如 `mathematical-writing`）不能用這個寫法推導，只能在散文裡提及。

引用兄弟領域的條目，不等於繼承它的能力（第 1 條 Domain Independence）。教學條目從學習條目推導時，推導的理由要寫在自己的 `rationale` 裡。
