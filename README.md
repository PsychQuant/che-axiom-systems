# che-axiom-systems

跨領域形式化公理體系。目標：將不同知識領域以**公理化（axiomatization）**的形式統一表達、可查、可驗證、可累積。

基於 **ASBE (Axiomatic Specification by Example)** 方法論 — 每條公理同時具備形式化定義 + 範例錨定 + 跨域一致性保證。

## 結構

```
.
├── foundations/    # 元層級：跨領域原則 + ASBE 方法論
├── domains/        # 各知識領域的公理化系統
├── templates/      # 建立新領域的 YAML 模板
├── skills/         # Claude Code skills（axiom-lookup / -validate / -create）
└── plugin.json     # 作為 Claude Code plugin 安裝時的 manifest
```

## 已涵蓋領域

掃描 `domains/` 取最新清單。撰寫時涵蓋：

- `statistics/` — 統計與資料科學公理化
- `asbe/` — ASBE 方法論自身的公理（self-bootstrap）
- `apa7-style/` — APA 第七版格式規範的公理化
- `musical-composition/` — 音樂創作的公理化
- 其他陸續加入

## 作為 Claude Code Plugin 使用

```bash
/plugin marketplace add PsychQuant/che-axiom-systems
/plugin install che-axiom-systems@PsychQuant/che-axiom-systems
```

提供三個 skill：

| Skill | 用途 |
|-------|------|
| `axiom-create` | 建立新領域，或在既有領域新增公理 |
| `axiom-validate` | 驗證結構完整性 + 跨域一致性 |
| `axiom-lookup` | 全域搜尋公理 |

## 核心原則

1. **SCD2 (Add Only)** — 公理只能新增，不能修改或刪除（保留歷史）
2. **Domain Independence** — 各領域自成體系
3. **Consistency Requirement** — 跨領域不得矛盾
4. **ASBE Compliance** — 每條公理需雙層表達（形式 + 自然語言）+ 範例錨定

## 第三方參考材料注意事項

`domains/apa7-style/06_reference/` 內含兩類資產：

- **`biblatex-apa/`** — LaTeX 套件，[LPPL 1.3c](http://www.latex-project.org/lppl.txt) 授權，© Philip Kime。可隨本 repo 一同散布。
- **`download_apastyle.py` / `split_manual.py`** — 取得 APA 官方 reference 的腳本，由本 repo 作者撰寫。

**已從 repo 移除（並在 `.gitignore` 中封鎖）**：APA 第七版手冊的 OCR、APA Style 網站鏡像、相關圖檔等 — 全部屬於 American Psychological Association 版權所有。需要在本地工作時，請自行使用上述腳本重新取得（並僅限自用，勿散布）。

同理，過往 `musical-composition/logic-pro/` 下的 Apple Logic Pro 手冊、`statistics/SAS_manuals/` 下的 SAS PROC 手冊也已移除。需要時請至原廠官網下載。

## 來源

從 [`PsychQuant/psychquant-claude-plugins`](https://github.com/PsychQuant/psychquant-claude-plugins) 的 `plugins/che-axiom-systems/` 抽離為獨立 repo，便於版本管理與外部協作。

## 授權

MIT — 見 [LICENSE](LICENSE)。本 repo 內含的 biblatex-apa 子目錄保留其原本的 LPPL 1.3c 授權。

維護者：Che Cheng
