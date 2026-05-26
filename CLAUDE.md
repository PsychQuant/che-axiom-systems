# che-axiom-systems (marketplace root)

此 repo 是 Claude Code marketplace，散發 `che-axiom-systems` plugin。

## 結構

- `.claude-plugin/marketplace.json` — marketplace manifest
- `plugins/che-axiom-systems/` — 唯一的 plugin（含 skills、domains、foundations、templates 等所有實作）
- `README.md` — marketplace 對外介紹
- `LICENSE` — MIT（biblatex-apa 子目錄保留 LPPL 1.3c）

## 給未來 Claude 的 note

當使用者要求修改公理、添加新領域、改 skill 邏輯時：**所有實作都在 `plugins/che-axiom-systems/` 底下**，root 只保留 marketplace metadata 與整體文件。

## 重要區分

- 「marketplace」=本 repo 整體（散發容器）
- 「plugin」=`plugins/che-axiom-systems/`（功能本體）

不要把兩者混在一起。
