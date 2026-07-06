---
name: axiom-create
description: 建立新的公理化領域，或在既有領域新增公理/定理/範例。當使用者要求「公理化某領域」、「新增公理」、「加定理」、「建立 axiom domain」時使用。遵循 ASBE 方法論與 SCD2（只增不改）原則。Create or extend axiomatization domains following the ASBE methodology.
---

# axiom-create

建立或擴充公理化系統。

## 資料路徑與寫入策略

**讀取**：方法論與既有 domain 從 `${CLAUDE_PLUGIN_ROOT}/foundations/`、`${CLAUDE_PLUGIN_ROOT}/domains/`、`${CLAUDE_PLUGIN_ROOT}/templates/` 載入（plugin 自帶的 reference data）。`${CLAUDE_PLUGIN_ROOT}` 是 Claude Code 自動提供的 env var（plugin 安裝根目錄），可在 Bash 中以 `echo $CLAUDE_PLUGIN_ROOT` 取得；路徑慣例的 canonical 描述見 plugin CLAUDE.md「Skill 路徑慣例」。

**寫入**：分兩種情境

| 情境 | 判斷 | 寫入位置 |
|------|------|---------|
| **Maintainer 模式** | **結構偵測**：`ROOT=$(git rev-parse --show-toplevel)` 成功，且 `$ROOT/plugins/che-axiom-systems/.claude-plugin/plugin.json` 存在（repo 改名、fork、remote 別名都不影響判定）| 寫入 `$ROOT/plugins/che-axiom-systems/domains/<new-domain>/`，使用者後續可 commit/PR |
| **使用者本地模式** | 非 maintainer repo；偵測失敗（含非 git cwd）一律 **fail-closed** 到此模式 | 寫入 cwd 的 `axioms/<new-domain>/`（使用者私有目錄），並在最後提示「想 contribute 回 plugin，請 fork repo 後重跑」|

skill 開始前先檢查 cwd 判斷模式，並告知使用者目前是哪個模式。

## 流程

### Step 1: 確認操作

問使用者要做什麼：
- **建立新領域** — 從零開始一個新的公理化領域
- **擴充既有領域** — 在已有的領域中新增公理或定理

### Step 2: 如果是新領域

1. 詢問領域名稱和範圍描述；**名稱碰撞檢查**：已存在於 plugin 內建 domains、maintainer repo、或本地 `axioms/` → 建議改走 Step 3 擴充或換名；目標目錄已存在 → 停下確認，不覆寫
2. 讀取 `${CLAUDE_PLUGIN_ROOT}/foundations/asbe-methodology.md` 載入 ASBE 方法論
3. 讀取 `${CLAUDE_PLUGIN_ROOT}/templates/domain-template.yaml` 作為起點
4. 引導使用者定義：
   - **Primitive terms** — 此領域的基本未定義概念
   - **第一批公理** — 遵循 ASBE A1-A5：
     - 每條公理要有 `statement_natural` + `statement_formal` (A1)
     - 每條公理要有 `violations` + `compliant` 範例 (A2)
     - 公理之間要獨立、一致、充分 (A4)
5. 依「資料路徑與寫入策略」判斷寫入位置：maintainer 模式寫 `$ROOT/plugins/che-axiom-systems/domains/<domain-name>/`、使用者本地模式寫 `<cwd>/axioms/<domain-name>/`
6. **一併產生 domain manifest**：從 `${CLAUDE_PLUGIN_ROOT}/templates/domain-manifest.yaml` 複製為新領域的 `domain.yaml`，填入 `domain` / `description` / `format`（新領域一律 `yaml` + `bootstrapped`）/ `entry_points`；maintainer 模式下同步在 `$ROOT/plugins/che-axiom-systems/domains/INDEX.md` 加一列
7. 讀取 `${CLAUDE_PLUGIN_ROOT}/foundations/cross-domain-principles.md`，檢查新公理是否與 plugin 內建領域矛盾

### Step 3: 如果是擴充既有領域

0. **先讀該域的 `domain.yaml` manifest**（缺失 → 視同 `markdown/legacy`，建議補 manifest），依 `format` 分流：
   - `yaml` → 依 ASBE schema 新增（下方 3–4 照舊）
   - `markdown` → 在 `entry_points` 所列檔案以散文附加，沿用該文件既有的標題／編號慣例；可主動提議 bootstrap 一份平行的 `*_bootstrapped.yaml`（參照 asbe 域先例），**不要**在散文檔內混入 YAML 欄位
   - `freeform` → 從 `entry_points` 進入該域自訂體系（如 japanese-narrative 的 `公理/`），依其組織方式新增；不強加 ASBE 欄位
1. **寫入位置**：maintainer 模式 → 直接改 `$ROOT/plugins/che-axiom-systems/domains/<domain>/`；**非 maintainer 模式擴充 plugin 內建域** → 寫 `<cwd>/axioms/<domain>/extensions.md|yaml` overlay（**絕不寫入 `${CLAUDE_PLUGIN_ROOT}` — 那是 plugin cache，下次更新即被清除**），lookup/validate 會以 `[local]` 來源顯示
2. 列出 `${CLAUDE_PLUGIN_ROOT}/domains/`（plugin 內建）+ cwd 的 `domains/` 或 `axioms/`（本地）中的所有領域讓使用者選擇，然後讀取該領域的現有公理
3. 引導使用者新增：
   - **新公理** — 必須與既有公理獨立（A4）
   - **新定理** — 必須標明 `derives_from` 指向父公理（A3；僅 yaml format）
   - **新範例** — 可以為既有公理補充 violations/compliant（僅 yaml format）
4. 遵循 SCD2 原則：只新增，不修改既有公理
5. 檢查跨域一致性：讀取 `${CLAUDE_PLUGIN_ROOT}/foundations/cross-domain-principles.md` 比對
6. **同步 manifest 與 INDEX**：若本次擴充新增了檔案、或改變了該域的 format/maturity 實態，更新該域 `domain.yaml`（`entry_points` 等）；maintainer 模式下同步檢查 `domains/INDEX.md` 該列

### Step 4: 品質檢查（委派給 axiom-validate）

建立完成後，讀取 `${CLAUDE_PLUGIN_ROOT}/skills/axiom-validate/SKILL.md`，依其 Step 1.5–2 流程對**本次新增的項目**執行單一領域驗證 — 檢查方式與嚴重度由該域 manifest 的 format/maturity 決定，不在此複製檢查清單（凍結的副本必然 drift）。

有問題提示使用者修正；修正**尚未發布**的草稿不受 SCD2 限制（SCD2 約束的是已發布公理）。

## 完成後提示

> 新增完成。建議執行 `/axiom-validate` 做完整驗證。
