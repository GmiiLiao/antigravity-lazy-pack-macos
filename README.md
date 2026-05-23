# 🌌 Anti-Gravity 專屬懶人包 — 全平台服務連接與開發自動化指南（macOS 版）

歡迎使用 **Anti-Gravity 專屬懶人包 macOS 版**！本專案是原版 Windows 懶人包的 macOS 調適版本，為在 **macOS** 上使用 AI 編碼助理（Anti-Gravity 2）的使用者提供一個極致流暢、全自動化的開發與服務連接範本。

> 🪟 原版 Windows 懶人包請見：[mathruffian-dot/antigravity-lazy-pack](https://github.com/mathruffian-dot/antigravity-lazy-pack)

透過本專案的指南與設定，您將能夠引導 AI 助理完美連接 NotebookLM、Firebase、GitHub 以及 Obsidian，並透過專案駕駛艙（`ANTIGRAVITY.md`）實現「開工/收工/專案初始化」的一鍵自動化 SOP。

---

## 🚀 專案核心特色

1. **🍎 macOS 原生優化**：所有指令均針對 macOS Terminal（zsh）調適，移除 Windows 專屬的 PowerShell 限制與繞過技巧。
2. **🔗 全平台服務整合**：完整打通 Google NotebookLM、Firebase、GitHub 與 Obsidian 本地第二大腦。
3. **🤖 專案駕駛艙 (SOP)**：設定開工、收工及專案初始化技能，讓 AI 代理自動管理您的工作流。
4. **🎨 原生免 API Key 繁體中文生圖**：配置以繁體中文為優先的優雅資訊圖表生成指南。
5. **📊 實戰成果展示**：收錄真實運作產出的「AI 教育代理人」深度趨勢報告與視覺化圖表。

---

## 📂 檔案目錄說明

* 📄 **[09-AntiGravity專屬懶人包-macOS版.md](09-AntiGravity專屬懶人包-macOS版.md)**：**核心指南主檔**，詳細記錄所有 macOS 服務連接步驟與防坑指南。
* 📝 **[ai_educational_agents_trends.md](ai_educational_agents_trends.md)**：實戰產出的 AI 教育代理人教學與行政應用深度報告（與原版相同）。
* 📊 **[notebooks.json](notebooks.json)**：由 NotebookLM MCP 介面自動獲取的最新筆記本資料（與原版相同）。
* 🖼️ **[ai_educational_agents_infographic_zh.png](ai_educational_agents_infographic_zh.png)**：使用原生生圖技能生成的繁體中文「AI 教育代理人應用」高品質資訊圖表。
* 🖼️ **[ai_educational_agents_infographic.png](ai_educational_agents_infographic.png)**：雙語對照版的高品質概念資訊圖表。

---

## 🛠️ 快速開始

### 第零步：確認 macOS 基礎環境

```bash
# 安裝 Homebrew（若尚未安裝）
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 確認 Python 3、Node.js 已就緒
python3 --version && node --version && npm --version
```

### 接著請閱讀 📖 [09-AntiGravity專屬懶人包-macOS版.md](09-AntiGravity專屬懶人包-macOS版.md)，照著內部的三大步驟進行配置：

1. **第一部分**：連接 NotebookLM MCP、Firebase、GitHub 與 Obsidian（macOS 版指令）。
2. **第二部分**：利用原生 `generate_image` 進行繁體中文生圖。
3. **第三部分**：建立與執行開工/收工/專案初始化 SOP 自動化技能。

---

## 🍎 vs 🪟 Windows vs macOS 主要差異對照

| 項目 | Windows 版 | macOS 版 |
|------|-----------|---------|
| Shell | PowerShell / CMD | Terminal（zsh） |
| NotebookLM 編碼問題 | 需設定 `$env:PYTHONIOENCODING="utf-8"` | ✅ 無需設定，預設 UTF-8 |
| Firebase 執行原則限制 | 需用 `cmd /c firebase ...` 包裝 | ✅ 直接執行 `firebase ...` |
| 環境變數設定 | `$env:變數="值"` | `export 變數="值"` |
| 環境變數持久化 | 系統環境變數設定 | 寫入 `~/.zshrc` |
| 套件管理器 | Chocolatey / winget | **Homebrew** |
| GitHub CLI 安裝 | `winget install gh` | `brew install gh` |
| 清除環境變數 | `$env:GITHUB_TOKEN=""` | `unset GITHUB_TOKEN` |

---

祝您與您的 AI 助理在 macOS 上對話愉快，享受極速開發的樂趣！🚀🍎
