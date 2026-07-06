---
name: axiom-validate
description: 驗證公理化系統的結構完整性（ASBE 合規）和跨領域一致性（無矛盾）。
user_invocable: true
---

# axiom-validate

驗證公理化系統品質。兩個層級的檢查。

## 資料路徑

公理與方法論資料隨 plugin 散布，存放在 `${CLAUDE_PLUGIN_ROOT}/domains/` 與 `${CLAUDE_PLUGIN_ROOT}/foundations/`。`${CLAUDE_PLUGIN_ROOT}` 是 Claude Code 自動提供的 env var（plugin 安裝根目錄），可在 Bash 中以 `echo $CLAUDE_PLUGIN_ROOT` 取得。本檔內所有 `domains/`、`foundations/` 都指 plugin-root-relative 位置，不是使用者 cwd。

**驗證範圍 = plugin 內建 ∪ 本地**：若 cwd 存在 `domains/` 或 `axioms/`（`/axiom-create` 本地模式的產物），也是合法驗證目標；報告標明來源 `[plugin]` / `[local]`。這讓 create → validate 的接力在本地模式也走得通。

## 流程

### Step 1: 選擇驗證範圍

問使用者：
- **單一領域** — 驗證某個 domain 的結構完整性
- **跨領域一致性** — 檢查所有 domain 之間是否有矛盾
- **全部** — 兩者都做

### Step 1.5: 讀取 domain manifest（決定檢查級別）

每個 domain 根目錄有 `domain.yaml` manifest（schema 見 `${CLAUDE_PLUGIN_ROOT}/templates/domain-manifest.yaml`）。**先讀 manifest 再驗證** — 不同 format/maturity 適用的檢查不同，對 legacy domain 硬套 YAML schema 檢查會產生大量誤報 ERROR：

| `format` | `maturity` | 檢查行為 |
|----------|------------|----------|
| `yaml` | `bootstrapped` | 完整 A1–A5 欄位級檢查，嚴重度照下表（ERROR 級生效）|
| `markdown` | `legacy` | A1–A5 改為**結構性掃描**：缺欄位報 WARNING（遷移缺口），不報 ERROR |
| `freeform` | `legacy` | 跳過欄位級檢查，只做 Step 3 跨域一致性掃描 + 一行說明 |

manifest 缺失（使用者本地自建的舊 domain）→ 視同 `markdown/legacy`，並建議補 manifest。

**驗證檔案集**：manifest `entry_points` 所列檔案＋其同層兄弟公理檔（如 `01_core_axioms/*.yaml`）。一律排除 `archive/`、`archived/`、`06_reference/` 等參考資料目錄與 dotdirs — archive 內是被取代的舊公理，納入會產生假重複/假矛盾誤報。`entry_points` 指向不存在的檔案 → WARNING。

### Step 2: 結構驗證（Domain 內）

讀取 `${CLAUDE_PLUGIN_ROOT}/foundations/asbe-methodology.md` 中的 ASBE 5 條公理作為檢查標準。

對目標 domain 中的每條公理/定理，檢查（嚴重度以 Step 1.5 的級別為準；下表為 `bootstrapped` 級）：

| ASBE 公理 | 檢查項目 | 嚴重度 |
|-----------|----------|--------|
| A1 雙層表達 | 有 `statement_natural` 和 `statement_formal`？ | ERROR |
| A2 範例錨定 | 有至少 1 個 `violations` 和 1 個 `compliant`？ | ERROR |
| A3 層級推導 | 非公理的項目有 `derives_from`？DAG 無環？ | ERROR |
| A4 最小公理集 | 公理之間是否獨立？有無冗餘？ | WARNING |
| A5 語意等價 | natural 和 formal 表達同一件事？ | WARNING |

另外檢查：
- ID 命名慣例（A/T/C/R prefix）
- `meta` 欄位完整性（domain, version, author）
- SCD2 合規：與上一版本相比，有無修改或刪除既有公理

輸出格式 — **bootstrapped 級**（欄位級檢查，ERROR 生效）：
```
📋 Domain: mathematical-writing [yaml/bootstrapped]
   ✅ A1 Dual Expression: 1/1 pass
   ❌ A2 Example Grounding: 0/1 — A1_statement_placement missing compliant example
   ✅ A3 Hierarchical Derivation: OK
   ⚠️  A4 Minimal Axiom Set: OK
   ✅ A5 Semantic Equivalence: OK
```

**legacy 級**（結構性掃描，缺欄位是遷移缺口不是錯誤）：
```
📋 Domain: statistics [markdown/legacy]
   ⚠️  A1/A2 structural scan: 散文公理無 statement_formal / violations 欄位 — 遷移缺口（legacy 預期）
   ℹ️  升級路徑：可用 /axiom-create 協助 bootstrap 為 YAML schema
```

圖示紀律：`❌` = ERROR、`⚠️` = WARNING、`ℹ️` = INFO — 三個 Step 統一使用，Step 4 的彙總計數依此分類。

### Step 3: 跨領域一致性檢查

1. 讀取 `${CLAUDE_PLUGIN_ROOT}/foundations/cross-domain-principles.md`
2. 掃描所有 `${CLAUDE_PLUGIN_ROOT}/domains/` 中每個領域的公理摘要
3. 識別**重疊概念** — 不同領域涉及相同概念的公理（例如 statistics 和 decision-making 都涉及 probability）
4. 對重疊的公理對，分析是否存在矛盾
5. Flag 潛在衝突，附上理由，讓使用者 review

輸出格式：
```
🔗 Cross-Domain Consistency Check
   Scanned: 14 domains（實際數字以 INDEX 列數為準，勿照抄範例）

   ℹ️  Potential overlap（相容性觀察 = INFO）:
   - statistics/A3 (probability interpretation) ↔ decision-making/A2 (subjective probability)
     Analysis: Compatible — statistics uses frequentist framing,
     decision-making uses Bayesian framing. No contradiction,
     but consider adding cross-reference annotation.

   ✅ No contradictions detected.（真矛盾才用 ⚠️/❌）
```

### Step 4: 報告

彙總所有發現：
- ERROR: 必須修正
- WARNING: 建議修正
- INFO: 跨域觀察

提示使用者是否要立即修正（遵循 SCD2 — 修正方式是新增澄清，不是修改原文）。
