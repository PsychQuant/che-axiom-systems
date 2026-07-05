# che-axiom-systems

Claude Code marketplace，散發 **跨領域形式化公理體系** plugin。

目前只裝一個 plugin：`che-axiom-systems`。將不同知識領域以**公理化**的形式統一表達、可查、可驗證、可累積。基於 **ASBE (Axiomatic Specification by Example)** 方法論。

## 安裝

```bash
/plugin marketplace add PsychQuant/che-axiom-systems
/plugin install che-axiom-systems@che-axiom-systems
```

安裝後即可使用三個 skill：

| Skill | 用途 |
|-------|------|
| `/axiom-lookup` | 全域搜尋公理 |
| `/axiom-validate` | 驗證結構完整性 + 跨域一致性 |
| `/axiom-create` | 建立新領域或在既有領域新增公理 |

## Repo 結構

```
.
├── .claude-plugin/
│   └── marketplace.json     # marketplace manifest
├── plugins/
│   └── che-axiom-systems/   # 唯一的 plugin
│       ├── .claude-plugin/
│       │   └── plugin.json
│       ├── skills/          # 三個 skill
│       ├── domains/         # 12+ 個內建公理化領域
│       ├── foundations/     # 跨領域原則 + ASBE 方法論
│       ├── templates/       # YAML 模板
│       ├── README.md        # plugin 使用說明
│       └── CLAUDE.md        # plugin internal guide
├── README.md                # 本檔案：marketplace 說明
├── LICENSE                  # MIT
└── .gitignore
```

## 內建領域（plugin 自帶）

14 個公理化領域，完整清單見 [`plugins/che-axiom-systems/domains/INDEX.md`](plugins/che-axiom-systems/domains/INDEX.md)（含各領域的 format / maturity / entry point）。

## 核心原則

1. **SCD2 (Add Only)** — 公理只能新增，不能修改或刪除
2. **Domain Independence** — 各領域自成體系
3. **Consistency Requirement** — 跨領域不得矛盾
4. **ASBE Compliance** — 每條公理需雙層表達 + 範例錨定

## 來源

從 [`PsychQuant/psychquant-claude-plugins`](https://github.com/PsychQuant/psychquant-claude-plugins) 的 `plugins/che-axiom-systems/` 抽離為獨立 marketplace，便於版本管理與外部協作。

## 授權

MIT — 見 [LICENSE](LICENSE)。Plugin 內含的 `plugins/che-axiom-systems/domains/apa7-style/06_reference/biblatex-apa/` 保留其原本的 LPPL 1.3c 授權。

維護者：Che Cheng
