# Domains INDEX

14 個內建公理化領域。每個領域的 `domain.yaml` manifest 是機器可讀的 source of truth；本表由 manifest 彙整。新增/修改領域後三件套同步：`domain.yaml` + 本表 + [`TOPICS.yaml`](TOPICS.yaml)（axiom-based 的路由層）。

| Domain | 描述 | Format | Maturity | Entry point |
|--------|------|--------|----------|-------------|
| `academic-presentation` | 學術會議報告（投影片＋講稿）的建構與交付公理 | yaml | bootstrapped | `CLAUDE.md` |
| `apa7-style` | APA 第七版寫作與引用格式規範 | yaml | bootstrapped | `CLAUDE.md` |
| `asbe` | ASBE 方法論自身的公理化（self-bootstrap） | yaml | bootstrapped | `asbe_axioms_bootstrapped.yaml` |
| `decision-making` | 決策理論：效用、偏好與悖論 | markdown | legacy | `axiomatization_of_decision_making.md` |
| `information-theory` | 資訊理論：測度與不等式 | markdown | legacy | `axiomatization_of_information_theory.md` |
| `japanese-narrative` | 日本文學敘事構成（日文目錄體系） | freeform | legacy | `公理/INDEX.md` |
| `language-learning` | 語言習得模型與現象 | markdown | legacy | `axiomatization_of_language_learning.md` |
| `logic-and-language` | 邏輯系統與後設邏輯 | markdown | legacy | `axioms_of_logic.md` |
| `mathematical-learning` | 數學學習：能力依賴與機率模型 | markdown | legacy | `axiomatization_of_mathematical_learning.md` |
| `mathematical-writing` | 數學寫作（statement-placement 公理） | yaml | bootstrapped | `mathematical_writing_axioms.yaml` |
| `musical-composition` | 音樂作曲與理論（日文） | freeform | legacy | `音楽作曲と理論の公理化.md` |
| `note-writing` | 筆記寫作原則 | markdown | legacy | `README.md` |
| `philosophy` | 哲學隨筆：他者作為起點 | freeform | legacy | `My Essey/…批判與重構.md` |
| `statistics` | 統計與資料科學 | markdown | legacy | `00_principles.md` |
| `weight-control` | 體重控制：質量守恆與碳平衡 | yaml | bootstrapped | `weight_control_axioms.yaml` |

## 欄位語意

- **Format** — `yaml`：ASBE 結構化 schema，欄位級可驗證；`markdown`：散文公理；`freeform`：自訂體系
- **Maturity** — `bootstrapped`：validate 以 ERROR 級執行 A1–A5；`legacy`：缺欄位降級 WARNING
- 完整定義見 [`../templates/domain-manifest.yaml`](../templates/domain-manifest.yaml)
