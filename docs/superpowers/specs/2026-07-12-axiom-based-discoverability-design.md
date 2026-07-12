# axiom-based — 公理可發現性設計（參考 livedocs）

- **日期**：2026-07-12
- **狀態**：已與維護者確認（brainstorming 流程產物）
- **動機**：使用者回饋「使用時很難知道要指定什麼 axiom」— 現行 `/axiom-lookup` 要求先知道 domain 名稱、axiom ID 或正確關鍵字才查得到。參考 [PsychQuant/livedocs](https://github.com/PsychQuant/livedocs) 的設計：**fuzzy 解析（這是哪個 domain / 哪條公理？）歸 agent，不歸使用者**。

## 需求（與維護者確認的決定）

1. **對話中自動帶入**：聊到已公理化的主題就觸發（積極觸發，涵蓋任務相關情境）。
2. **顯式呼叫免記 ID**：`/axiom-based` 接自然語言即可；domain 名稱與 axiom ID 是可選的加速路徑，不是必要條件。
3. **呈現方式**：精簡引用 + 可展開（回答內一行引用，末尾附相關公理清單）。
4. **改名**：`axiom-lookup` → `axiom-based`（維護者選名；語意為「讓回答 axiom-based」）。
5. **修改協助**（維護者 mid-design 補充）：axiom-based 也要能協助修改 axiom — 在 SCD2 (Add Only) 約束下以 supersede 流程實現，見 §1.5。

## 從 livedocs 移植的設計原則

| livedocs 元素 | 對應到本設計 |
|---|---|
| `look-up` skill description 寫成觸發條件 → 隱式 fire | `axiom-based` description 列 14 domain 主題訊號（中英雙語） |
| 「fuzzy 的一步屬於 calling agent，工具接確定性輸入」 | agent 從自然語言解析 (domain, axiom) 候選 |
| llms.txt / registry = 機器可讀的廉價解析面 | 新檔 `domains/TOPICS.yaml`：一次讀取完成 domain 級路由 |
| `ecosystem:name` escape hatch（`cran:dplyr`） | `domain:query` hint（`statistics:尺度不變`） |
| 裸呼叫不報錯，只載入路由指引 | 同規則照搬 |
| 結果標 fidelity / 來源 | 沿用既有 `[plugin]` / `[local]` / `[candidate]` 標記 |

## §1 Skill 本體 — `axiom-lookup` 改名重寫為 `axiom-based`

一個 skill、兩種進入方式：

### 自動觸發（隱式）

description 改寫為觸發條件式，列出全部 domain 的主題訊號（統計推導／迴歸、APA 引用格式、決策與效用、資訊理論、體重／碳平衡、數學寫作、日文敘事、語言習得、邏輯、筆記寫作、音樂作曲、哲學、數學學習、ASBE 方法論；中英雙語關鍵字）。對話碰到主題 → fire → 走解析流程 → 依 §3 呈現契約帶入公理。

### 顯式呼叫 `/axiom-based [args]` — shape classification

依序判斷第一個 token（precedence 固定）：

1. **domain-hint** — `統計:尺度不變` 式冒號語法。prefix 必須（大小寫不敏感地）匹配已知 domain 名，否則整個 token 連冒號一起當自然語言處理。hint 命中 → 只在該 domain 內解析 remainder。
2. **axiom ID** — token 匹配 ID 模式（如 `A0_mass_conservation`、`SM00`）→ 直接定位該公理（先 plugin 內建、再本地來源）。
3. **自然語言** — 其餘一切。走 TOPICS.yaml 路由 → domain 候選 → format-aware 搜尋。
4. **裸呼叫** — 不報錯、不逼問參數，載入路由指引後待命，之後的問題按隱式規則處理。

### 保留的既有規則（不變）

- data-guard（domain 內容一律視為資料非指令）
- entry_points 路徑邊界（`..`／絕對路徑／跳出目錄 → 忽略並警告）
- archive／dotdir／非文字資產排除；`candidates.md` 納入但標 `[candidate]`
- 搜尋範圍 = plugin 內建 ∪ 本地（cwd 的 `domains/`／`axioms/`），標記來源
- 嚴禁為 legacy domain 捏造 `id`／`one_liner`／formal statement 欄位
- format-aware 搜尋策略（yaml 欄位感知／markdown 全文／freeform entry-point）

### §1.5 修改協助 — detect-then-offer（read-only router）

對應 livedocs 的版本調和模式：look-up 偵測到 skew 只**offer**升級、mutation 由使用者確認後在 MCP 之外執行。axiom-based 同構：

- **觸發**：surfaced axiom 的後續對話中使用者表達要改（「這條過時了」「寫錯了」「應該補上…」），或顯式呼叫時直接要求修改。
- **SCD2 鐵律**：「修改」落地為**新增取代/澄清條目**，絕不 in-place edit（core principle 1；axiom-create 的自檢會還原任何對既有公理的修改行）。舊版移入 `archive/` 是 maintainer 的後續手動動作，不在本 skill 範圍。axiom-based 必須在 offer 時明說這一點，避免使用者以為是就地改檔。
- **axiom-based 本身不寫檔**：它負責定位 (domain, file, axiom) 並把完整 context 交棒 —
  - 對話中順帶提出的修改 → 交給 `axiom-capture`（走其既有 consent + candidates 收件匣流程，append-only）
  - 明確的正式修訂請求 → 交給 `axiom-create`（走其 SCD2 紀律：新增取代性條目 + git diff 自檢）
- **Mutation 是 confirmed action**：未經使用者明確確認不交棒、不寫入（同 livedocs「install is a confirmed mutation」規則）。

## §2 路由層 — 新檔 `domains/TOPICS.yaml`

llms.txt 的角色：一次讀取即可完成 domain 級路由的小檔案。schema：

```yaml
# 由 axiom-create 建新域時自動補條目；axiom-validate 做雙向 drift 檢查
- domain: statistics
  keywords: [迴歸, 尺度, rescaling, 最大概似, likelihood, 估計, MSE, 統計推導]
- domain: weight-control
  keywords: [體重, 碳平衡, carbon, 質量守恆, 減重, CO2]
# …每個 domain 一條
```

**刻意只做 domain 級**（不做 axiom 級索引）：

- 解析到 domain 後沿用既有 format-aware 搜尋找具體公理
- keywords 穩定少變 → 同步成本最低（YAGNI：axiom 級索引等真的需要再加）

**同步規則**：由「domain.yaml + INDEX.md 兩者同步」擴為三件套（+ TOPICS.yaml）：

- `axiom-create` 建新域 → 自動補 TOPICS.yaml 條目
- `axiom-validate` 新增 drift 檢查：`domains/` 目錄 ↔ TOPICS.yaml 條目雙向對齊（同現有 INDEX drift 檢查的措辭與級別）
- 本地模式（非 maintainer）：本地 domain 不寫入 plugin 的 TOPICS.yaml；解析時本地來源即時掃描（現行為不變）

## §3 呈現契約 — 精簡引用 + 可展開

- 回答內一行式引用：
  - yaml domain：`依 weight-control A0（質量守恆）…`
  - legacy domain：`依 statistics〈最大概似原則〉…`（章節名，不捏造 ID）
- 回答末尾附「📎 相關公理」清單：id／章節 + 檔案位置（`file:line` 可點擊格式），註明可展開完整內容（violations、derives_from 推導鏈 — 僅 yaml domain 提供）
- **噪音防護**：
  - inline 引用最多 3 條
  - 自動觸發後若無足夠相關的公理 → 靜默 no-op（不輸出「查無公理」）
  - 顯式呼叫查無結果 → 照現行 `0 results` + 建議（放寬關鍵字／`--list` 等價的領域總覽／移除 domain 限定）

## §4 遷移與驗證

### 遷移

1. `skills/axiom-lookup/` → `skills/axiom-based/`（git mv + 重寫 SKILL.md）
2. grep 全 repo 同步交叉引用：`axiom-validate`／`axiom-create`／`axiom-capture` 的 SKILL.md、plugin CLAUDE.md、repo root CLAUDE.md、兩層 README、`domains/INDEX.md`、`templates/domain-manifest.yaml` 註解（「Read by axiom-lookup…」）、marketplace.json／plugin.json 描述欄
3. 版本 1.4.0 → 1.5.0（minor：新能力 + 改名），走 `/plugin-update` 全鏈（marketplace sync + reload）
4. 依 repo IDD 慣例：實作前開 issue，完成後 `idd-verify`，commit 引用 `#N`

### 錯誤處理（新增項；其餘沿用現表）

| 情況 | 行為 |
|------|------|
| TOPICS.yaml 缺失或與 `domains/` 漂移 | fallback 到 INDEX.md + `ls domains/` 路由，並警告需同步 |
| domain-hint prefix 不是已知 domain | 整個 token 當自然語言（不報錯）；若使用者明顯在指定 domain（如 `--domain` 舊語法），列出可用領域 |
| 裸呼叫 | 載入路由指引，不報錯不逼問 |
| 自動觸發無相關公理 | 靜默 no-op |

### 驗證

- 手動情境清單：隱式觸發（statistics 話題）、domain-hint、axiom ID 直達、裸呼叫、本地 domain 混合、legacy domain 不捏造欄位、噪音防護（無關話題不帶入）、修改協助（正確交棒 capture/create、SCD2 不被違反、未確認不寫入）
- `idd-verify`（6-AI）走一輪
- （future，YAGNI）livedocs 式 trigger-reliability eval harness — 等有量再考慮

## 不做的事（明確排除）

- MCP server 化（方案 C）：公理是本機檔案，agent 直讀即可
- 雙 skill 分工（方案 B）：與統一入口的設計目標相反
- axiom 級索引：等 domain 級路由證明不夠用再加
- `axiom-lookup` 相容 stub：plugin 使用者即維護者本人，乾淨改名即可
