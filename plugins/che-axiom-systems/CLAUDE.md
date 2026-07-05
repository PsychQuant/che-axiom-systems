# che-axiom-systems (plugin)

此目錄是 `che-axiom-systems` plugin 本體。跨領域形式化公理體系。

## 內部結構

- `.claude-plugin/plugin.json` — plugin manifest
- `skills/` — 3 個 skill：`axiom-create`、`axiom-validate`、`axiom-lookup`
- `domains/` — 各領域公理化系統（plugin 自帶 reference data）
- `foundations/` — 元層級：跨領域原則 + ASBE 方法論
- `templates/` — 建立新領域的 YAML 模板

## Skill 路徑慣例

Skills 讀取 plugin 自帶資料時使用 `${CLAUDE_PLUGIN_ROOT}/` 前綴（Claude Code 自動提供的 env var）。寫入時依 cwd 判斷 maintainer / 使用者本地模式。詳見各 SKILL.md 開頭的「資料路徑」段落。

## 核心原則

1. **SCD2 (Add Only)** — 公理只能新增，不能修改或刪除
2. **Domain Independence** — 各領域自成體系
3. **Consistency Requirement** — 跨領域不得矛盾
4. **ASBE Compliance** — 每條公理需雙層表達 + 範例錨定

## 領域清單

讀 `${CLAUDE_PLUGIN_ROOT}/domains/INDEX.md`（人讀）或各 domain 的 `domain.yaml` manifest（機器讀）。新增/修改領域時兩者都要同步更新。manifest 的 `format`/`maturity` 決定 axiom-validate 的檢查級別與 axiom-lookup 的搜尋策略。
