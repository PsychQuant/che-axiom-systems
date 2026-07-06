# che-axiom-systems

跨領域形式化公理體系 plugin。將不同知識領域以**公理化（axiomatization）**形式統一表達、可查、可驗證、可累積。

基於 **ASBE (Axiomatic Specification by Example)** 方法論 — 每條公理同時具備形式化定義 + 範例錨定 + 跨域一致性保證。

## 安裝

```bash
/plugin marketplace add PsychQuant/che-axiom-systems
/plugin install che-axiom-systems@che-axiom-systems
```

## Skills

| Skill | 用途 | 副作用 |
|-------|------|------|
| `/axiom-lookup` | 全域搜尋公理、定理、概念 | 唯讀 |
| `/axiom-validate` | 驗證 ASBE 結構合規 + 跨域一致性 | 唯讀 |
| `/axiom-create` | 建立新領域或在既有領域新增公理 | 寫入（見「寫入位置」）|
| `/axiom-capture` | 對話中偵測公理候選並詢問（auto-trigger）；快速記入 `candidates.md` 或委派 create | 寫入（同 create 模式規則）|

## 內建領域

Plugin 自帶 **14 個**已公理化的領域，安裝後可直接 `/axiom-lookup` 查詢。完整清單（含 format / maturity / entry point）見 [`domains/INDEX.md`](domains/INDEX.md)，或跑 `/axiom-lookup --list`：

| Maturity | 領域 |
|----------|------|
| `bootstrapped`（ASBE YAML schema）| `apa7-style`、`asbe`、`mathematical-writing`、`weight-control` |
| `legacy`（markdown / freeform）| `statistics`、`decision-making`、`information-theory`、`japanese-narrative`、`language-learning`、`logic-and-language`、`mathematical-learning`、`musical-composition`、`note-writing`、`philosophy` |

每個領域根目錄的 `domain.yaml` manifest 宣告其格式與成熟度，決定 `/axiom-validate` 的檢查級別。

## 寫入位置（axiom-create）

- **Maintainer 模式**（結構偵測：repo root 存在 `plugins/che-axiom-systems/.claude-plugin/plugin.json`）→ 寫到 `<repo-root>/plugins/che-axiom-systems/domains/<new>/`，方便後續 commit/PR
- **本地模式**（其他 cwd；偵測失敗一律 fail-closed 到此）→ 寫到 cwd 的 `axioms/<new>/`（私有領域）；擴充 plugin 內建域時寫 `axioms/<domain>/extensions.*` overlay，絕不寫入 plugin cache

## 核心原則

1. **SCD2 (Add Only)** — 公理只能新增，不能修改或刪除（保留歷史）
2. **Domain Independence** — 各領域自成體系
3. **Consistency Requirement** — 跨領域不得矛盾
4. **ASBE Compliance** — 每條公理需雙層表達（形式 + 自然語言）+ 範例錨定

## 第三方參考材料注意事項

`domains/apa7-style/06_reference/` 內含兩類資產：

- **`biblatex-apa/`** — LaTeX 套件，[LPPL 1.3c](http://www.latex-project.org/lppl.txt) 授權，© Philip Kime。可隨本 plugin 一同散布。
- **`download_apastyle.py` / `split_manual.py`** — 取得 APA 官方 reference 的腳本，本 repo 作者撰寫。

**已從 plugin 移除（並在 `.gitignore` 封鎖）**：APA 第七版手冊 OCR、APA Style 網站鏡像、相關圖檔等 — 全部屬 American Psychological Association 版權。本地需要請自行使用上述腳本重新取得（僅限自用，勿散布）。

同理，過往 `musical-composition/logic-pro/` 下的 Apple Logic Pro 手冊、`statistics/SAS_manuals/` 下的 SAS PROC 手冊也已移除。需要時請至原廠官網下載。

## 授權

MIT — 見 marketplace 根目錄 [LICENSE](../../LICENSE)。本 plugin 內含的 `domains/apa7-style/06_reference/biblatex-apa/` 子目錄保留其原本的 LPPL 1.3c 授權。

維護者：Che Cheng
