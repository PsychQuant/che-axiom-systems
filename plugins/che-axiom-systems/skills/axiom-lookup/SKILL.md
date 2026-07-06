---
name: axiom-lookup
description: 搜尋 plugin 內建 14 個公理化領域（statistics、apa7-style、weight-control、ASBE、japanese-narrative 等）與使用者本地領域的公理、定理與概念。當使用者要查某條公理、問某領域有哪些公理、或問哪個 domain 涵蓋某概念時使用。Search or list axioms across the bundled axiomatization domains.
argument-hint: "[query] | --domain <name> [query] | --list"
---

# axiom-lookup

在所有公理化領域中搜尋。

## 資料路徑

公理資料隨 plugin 散布，存放在 `${CLAUDE_PLUGIN_ROOT}/domains/`。`${CLAUDE_PLUGIN_ROOT}` 是 Claude Code 自動提供的 env var（plugin 安裝根目錄），可在 Bash 中以 `echo $CLAUDE_PLUGIN_ROOT` 取得。本檔內所有 `domains/`、`foundations/`、`templates/` 都指 plugin-root-relative 位置，不是使用者 cwd。

**搜尋範圍 = plugin 內建 ∪ 本地**：若 cwd 存在 `domains/` 或 `axioms/`（`/axiom-create` 本地模式的產物），一併納入搜尋與 `--list`；結果標明來源 `[plugin]` / `[local]`。

## 觸發方式

- `/axiom-lookup [query]` — 搜尋關鍵字
- `/axiom-lookup --domain statistics [query]` — 限定領域搜尋
- `/axiom-lookup --list` — 列出所有領域（format / maturity / entry point）

## 流程

### Step 1: 解析查詢

從使用者輸入判斷：
- **有指定 domain** → 只搜尋該 domain（先在 plugin 內建找，再找本地來源）
- **沒有指定 domain** → 搜尋所有 `${CLAUDE_PLUGIN_ROOT}/domains/` 下的領域 + 本地來源（見「資料路徑」）
- **`--list`** → 列出總覽（plugin 內建讀 INDEX；本地來源即時掃描，標 `[local]`）

### Step 2: 搜尋

**先讀目標 domain 的 `domain.yaml` manifest**（`format` 欄位）決定搜尋策略：

| `format` | 策略 |
|----------|------|
| `yaml` | 欄位感知搜尋：`id`、`name`、`one_liner`、`statement_natural`、`statement_formal` |
| `markdown` | 全文搜尋：標題 + 內文，以 `entry_points` 列的檔案優先 |
| `freeform` | 全文搜尋，從 `entry_points`（如 `公理/INDEX.md`）進入該域自訂體系 |

使用 Grep 在 `${CLAUDE_PLUGIN_ROOT}/domains/`（+ 本地來源）中執行上述策略。

**排除規則（一律套用）**：排除 `**/archive/**`、`**/archived/**`、`06_reference/` 等參考資料目錄、dotdirs（`.claude/`、`.vscode/`）與非文字資產（圖檔、PDF、網頁存檔）。archive 內是被取代的舊版公理，混入結果會讓使用者拿到新舊並列且無標記的答案。`yaml` domain 的欄位感知搜尋以該域公理 YAML 檔為目標（`entry_points` 所列檔案＋同層兄弟 `*.yaml`，例如 apa7-style 的 `01_core_axioms/*.yaml`）。

### Step 3: 呈現結果（依 format 選模板）

**yaml domain** — 完整卡片（欄位真實存在才能這樣顯示）：
```
📍 weight-control [yaml/bootstrapped]
   A5_mass_conservation — Mass Conservation Axiom
   "Body mass change equals net mass flux"
   ΔM = Σ(mass_in) - Σ(mass_out)
   File: domains/weight-control/weight_control_axioms.yaml:42
```

**markdown domain** — 標題 + 摘錄 + 位置：
```
📍 statistics [markdown/legacy]
   § 最大概似原則
   「…估計量的選擇以概似函數最大化為準…」
   File: domains/statistics/00_principles.md:57
```

**freeform domain** — entry-point 相對路徑 + 摘錄：
```
📍 japanese-narrative [freeform/legacy]
   公理/J04_物の哀れ.md — 「…無常の美意識を物語の緊張構造に…」
```

如果結果跨多個領域，按 domain 分組顯示。**嚴禁為 legacy domain 捏造 `id`／`one_liner`／formal statement 欄位** — 該 format 沒有的欄位就用對應模板呈現。

### Step 4: 深入查看

依結果的 format 提供選項：
- `yaml` 結果 → 展開完整內容（violations/compliant 範例）、推導鏈（`derives_from` 向上追溯）、相關跨域公理
- `markdown` / `freeform` 結果 → 開啟該檔案的完整段落（這些 format 沒有 violations/derives_from 欄位，不提供該選項）

## 錯誤處理

| 情況 | 行為 |
|------|------|
| 無參數裸呼叫 | 問使用者要搜尋什麼，或建議 `--list` 看領域總覽 |
| `--domain` 名稱不存在 | 列出 INDEX 中可用領域（含本地來源），不猜測、不模糊匹配後逕自執行 |
| 查無結果 | 輸出 `0 results for "<query>"` + 建議：放寬關鍵字／`--list`／移除 `--domain` 限定 |
| `domain.yaml` 缺失（本地域常見） | 視同 `markdown/legacy` 全文搜尋，並建議補 manifest（與 axiom-validate 同措辭） |

## 特殊查詢

### `--list` 模式

**直接讀 `${CLAUDE_PLUGIN_ROOT}/domains/INDEX.md`** 作為輸出來源（決定性）；領域總數由 INDEX 列數推導，範例中的 14 只是示意。另以一次 `ls domains/` 交叉核對目錄與 INDEX 是否漂移（這不是輸出來源，只是 drift 檢查）。輸出格式：

```
📚 Axiomatization Systems — 14 domains

   statistics           — 統計與資料科學            [markdown/legacy]
   mathematical-writing — 數學寫作                  [yaml/bootstrapped]
   weight-control       — 體重控制                  [yaml/bootstrapped]
   japanese-narrative   — 日本文學敘事              [freeform/legacy]
   ...
```

若發現 `domains/` 下有目錄不在 INDEX 中（或反之），提示使用者 INDEX 與 manifest 需要同步。
