# Anti-Gravity 2 專屬懶人包 #09：全平台服務連接與自動化技能大整合（macOS 版）

> 版本：v1.0-macOS (Anti-Gravity 2 專屬版)
> 更新日期：2026-05-23
> 語系偏好：預設繁體中文（Taiwan）
> 適用系統：macOS 12 Monterey 及以上版本

---

## 🚀 這個懶人包會幫你做什麼？

本懶人包是專為在 **macOS** 上使用 **Anti-Gravity 2 (AI 編碼助理)** 的使用者設計的終極整合指南。照著本懶人包的步驟，您將能一步步引導 AI 助理連接您所有的雲端與本地服務，並打造全自動化的「開工/收工/專案初始化」工作流：

1. **NotebookLM 連接**：透過 `notebooklm-mcp-cli` 讀寫您的 NotebookLM 筆記與來源。
2. **Firebase 連接**：透過 `firebase-tools` 管理並部署您的 Firebase 雲端資料庫。
3. **GitHub 連接**：透過 `gh` CLI 進行自動化 Git commit、push 與遠端倉庫建立。
4. **Obsidian 第二大腦連接**：透過 `@bitbonsai/mcpvault` 與本地 Markdown 筆記雙向同步。
5. **「開工/收工/專案初始化」全自動技能**：透過 `ANTIGRAVITY.md` 專案駕駛艙落實 SOP 流程。
6. **免 API Key 原生生圖**：利用內建生圖引擎以 **繁體中文** 為預設語系生成高品質資訊圖表。

---

## 📋 事前準備：macOS 基礎環境確認

在開始之前，請確認以下工具已安裝。如果尚未安裝，請照順序執行：

### 1. 安裝 Homebrew（macOS 套件管理器）
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
安裝完成後，將 Homebrew 加入 PATH（Apple Silicon Mac 需執行此步驟）：
```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

### 2. 確認 Python 3 已安裝
```bash
python3 --version
# 若無，透過 Homebrew 安裝：
brew install python3
```

### 3. 確認 Node.js 已安裝
```bash
node --version
npm --version
# 若無，透過 Homebrew 安裝：
brew install node
```

---

## 🛠️ 第一部分：全平台服務連接指南

### 🎯 步驟一：連接 Google NotebookLM (MCP)

1. **安裝 CLI 工具**：
   ```bash
   pip3 install notebooklm-mcp-cli
   ```

2. **登入 Google 帳號**：
   ```bash
   nlm login
   ```

3. **驗證連線（列出筆記本）**：
   ```bash
   nlm list
   ```

> ✅ **macOS 無需擔心**：Windows 上的 CP950 編碼錯誤在 macOS 上不存在，因為 macOS 預設使用 UTF-8 編碼，`nlm` 指令可直接執行，無需額外設定環境變數。

4. **（可選）若遇到 `nlm` 指令找不到，請將 pip 安裝路徑加入 PATH：**
   ```bash
   echo 'export PATH="$HOME/Library/Python/3.x/bin:$PATH"' >> ~/.zshrc
   source ~/.zshrc
   ```
   > 💡 請將 `3.x` 替換為您的實際 Python 版本（例如 `3.11`）。

---

### 🎯 步驟二：連接 Firebase 資料庫

1. **安裝 Firebase CLI**：
   ```bash
   npm install -g firebase-tools
   ```

2. **登入 Firebase**：
   ```bash
   firebase login
   ```
   > 此指令會自動開啟瀏覽器進行 Google 帳號授權。

3. **列出您的 Firebase 專案確認連線**：
   ```bash
   firebase projects:list
   ```

> ✅ **macOS 無需擔心**：Windows 上的 `PSSecurityException`（PowerShell 執行原則限制）問題在 macOS 不存在。`firebase` 指令可在 Terminal（終端機）中直接執行，無需 `cmd /c` 包裝器。

4. **（可選）若遇到權限問題，可使用 npx 方式執行**：
   ```bash
   npx firebase-tools login
   npx firebase-tools projects:list
   ```

---

### 🎯 步驟三：連接 GitHub 帳戶

1. **安裝 GitHub CLI（若尚未安裝）**：
   ```bash
   brew install gh
   ```

2. **驗證與登入**：
   ```bash
   unset GITHUB_TOKEN   # 確保清除可能干擾的環境變數
   gh auth login --web --git-protocol https
   gh auth status
   ```

3. **設定 Git 全域使用者資訊**：
   ```bash
   git config --global user.name "您的名字"
   git config --global user.email "您的email@example.com"
   ```

4. **驗證 Git 設定**：
   ```bash
   git config --global --list
   ```

> 💡 **macOS 提示**：若您的 Mac 安裝了多個 Git 版本（例如 Xcode Command Line Tools 與 Homebrew 的 Git），建議使用 Homebrew 的版本：
> ```bash
> brew install git
> which git  # 應顯示 /opt/homebrew/bin/git
> ```

---

### 🎯 步驟四：連接 Obsidian 第二大腦

1. **安裝全域 MCP 伺服器**：
   ```bash
   npm install -g @bitbonsai/mcpvault
   ```

2. **初始化 mcpvault 並指向您的 Obsidian Vault 資料夾**：
   ```bash
   mcpvault init --vault ~/Documents/ObsidianVault
   ```
   > 💡 請將路徑替換為您實際的 Obsidian Vault 位置。在 macOS 上，Vault 通常位於 `~/Documents/` 或 `~/Obsidian/` 底下。

3. **啟動 MCP 伺服器**（背景執行）：
   ```bash
   mcpvault start &
   ```

4. **在 Anti-Gravity 助理中確認連線**：
   告知 AI 助理：「請使用 mcpvault 讀取我的 Obsidian 筆記」，若助理能列出筆記檔案，即代表連線成功。

> 💡 **macOS Obsidian 預設路徑參考**：
> - iCloud 同步版：`~/Library/Mobile Documents/iCloud~md~obsidian/Documents/您的Vault名稱`
> - 本機版：`~/Documents/ObsidianVault` 或自訂路徑

---

## 🎨 第二部分：原生免 API Key 繁體中文生圖

Anti-Gravity 2 內建 `generate_image` 工具，可直接生成高品質圖片，**無需任何 API Key**。

### 使用方式

在與 AI 助理的對話中，直接用自然語言描述您想要的圖片：

**範例指令：**
```
請生成一張關於「AI 教育代理人應用」的繁體中文資訊圖表，
包含以下主題：個人化學習、教師助理、智慧教室、心理健康預警。
請使用深色系配色，並確保所有文字以繁體中文呈現。
```

### 技巧提示

| 技巧 | 說明 |
|------|------|
| 明確指定語言 | 在 prompt 中加入「所有文字使用繁體中文」 |
| 指定風格 | 可加入「資訊圖表風格」、「簡約設計」、「深色背景」等 |
| 指定尺寸意圖 | 描述「寬版橫幅」、「正方形」、「直式海報」 |
| 迭代優化 | 收到圖片後，可繼續說「請將標題加大」、「換成藍色主題」 |

### 儲存生成的圖片

生成的圖片會自動儲存為 Artifact，您可以：
```bash
# 找到生成的圖片並複製到桌面
cp ~/path/to/artifact/image.png ~/Desktop/
```

---

## 🤖 第三部分：建立「開工/收工/專案初始化」SOP 自動化技能

### 📄 建立專案駕駛艙 ANTIGRAVITY.md

在您的主要工作目錄下建立 `ANTIGRAVITY.md` 檔案：

```bash
touch ~/Projects/ANTIGRAVITY.md
```

以下是建議的 `ANTIGRAVITY.md` 範本內容：

```markdown
# 🚀 專案駕駛艙 (Project Cockpit)

## 我的工作環境
- **作業系統**：macOS
- **主要工作目錄**：~/Projects/
- **Obsidian Vault**：~/Documents/ObsidianVault/
- **GitHub 帳號**：您的GitHub帳號
- **Firebase 專案 ID**：您的Firebase專案ID

## 開工 SOP（每日開始工作時執行）

請 AI 助理依序完成以下步驟：
1. 顯示今天的日期與時間
2. 列出 ~/Projects/ 目錄下的所有專案
3. 讀取 Obsidian Vault 中的「今日任務」筆記
4. 顯示 GitHub 上最近的 5 個 commit 紀錄
5. 整理成「今日工作摘要」顯示給我

## 收工 SOP（每日結束工作時執行）

請 AI 助理依序完成以下步驟：
1. 將今日修改的所有程式碼自動 commit 到 GitHub（commit message 格式：`[日期] 今日工作摘要`）
2. 在 Obsidian 中建立/更新「工作日誌/YYYY-MM-DD.md」筆記，記錄今日完成事項
3. 顯示明日建議優先處理的事項

## 專案初始化 SOP（開始新專案時執行）

請 AI 助理依序完成以下步驟：
1. 在 ~/Projects/ 下建立新專案資料夾（資料夾名稱請詢問我）
2. 初始化 git repo 並建立 .gitignore
3. 在 GitHub 上建立同名的遠端 repo 並推送
4. 在 Obsidian 中建立對應的專案筆記頁面
5. （選用）初始化 Firebase 專案
```

### 🎯 使用方式

每次開工時，只需對 AI 助理說：
> 「請執行 ANTIGRAVITY.md 中的**開工 SOP**」

AI 助理會自動讀取駕駛艙設定並依序執行所有步驟。

---

## 🍎 macOS 專屬實用技巧

### 環境變數持久化

在 macOS 上，環境變數應設定在 `~/.zshrc`（預設 Shell 為 zsh）：

```bash
# 編輯 ~/.zshrc
nano ~/.zshrc

# 加入以下內容（範例）
export GITHUB_TOKEN=""          # 通常不需要，gh CLI 會自動管理
export PYTHONIOENCODING="utf-8" # 非必要，macOS 預設已是 UTF-8

# 套用變更
source ~/.zshrc
```

### 開啟終端機的方式
- **Spotlight**：`⌘ + Space`，輸入 `Terminal`
- **Finder**：應用程式 → 工具程式 → 終端機
- **iTerm2**（推薦）：[下載 iTerm2](https://iterm2.com/)，功能更強大

### 查看隱藏檔案（如 .gitignore）
```bash
# 在終端機顯示隱藏檔
ls -la

# 在 Finder 中顯示隱藏檔案（按下快捷鍵）
# ⌘ + Shift + .
```

### 常用路徑對照（Windows → macOS）

| Windows 路徑 | macOS 對應路徑 |
|---|---|
| `C:\Users\使用者名稱\` | `~/` 或 `/Users/使用者名稱/` |
| `C:\Users\使用者名稱\Documents\` | `~/Documents/` |
| `%APPDATA%` | `~/Library/Application Support/` |
| `PowerShell` | `Terminal`（zsh） |
| `cmd /c 指令` | 直接執行指令（不需包裝） |
| `$env:變數="值"` | `export 變數="值"` |

---

## 🔧 常見問題排解（macOS 版）

### Q: `pip3 install` 出現「Permission denied」？
```bash
# 使用 --user 選項安裝到使用者目錄
pip3 install --user notebooklm-mcp-cli

# 或使用虛擬環境（推薦）
python3 -m venv ~/.venv/antigravity
source ~/.venv/antigravity/bin/activate
pip install notebooklm-mcp-cli
```

### Q: `npm install -g` 出現「Permission denied」？
```bash
# 方法一：使用 sudo（不推薦）
sudo npm install -g firebase-tools

# 方法二（推薦）：修改 npm 全域安裝目錄
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.zshrc
source ~/.zshrc
npm install -g firebase-tools
```

### Q: `gh` 指令找不到？
```bash
brew install gh
```

### Q: `firebase login` 無法開啟瀏覽器？
```bash
firebase login --no-localhost
```
> 系統會提供一個 URL，請手動複製到瀏覽器開啟授權。

### Q: Apple Silicon（M1/M2/M3）Mac 相容性問題？
```bash
# 確認 Homebrew 安裝在正確路徑
which brew  # 應顯示 /opt/homebrew/bin/brew（而非 /usr/local/bin/brew）

# 若有 Rosetta 相關問題，可透過 Rosetta 執行
arch -x86_64 zsh  # 切換到 x86_64 模式（通常不需要）
```

---

## ✅ 快速驗證清單

完成所有設定後，執行以下指令確認一切正常：

```bash
echo "=== 環境驗證 ===" && \
echo "Python: $(python3 --version)" && \
echo "Node: $(node --version)" && \
echo "npm: $(npm --version)" && \
echo "Git: $(git --version)" && \
echo "GitHub CLI: $(GITHUB_TOKEN="" gh --version | head -1)" && \
echo "Firebase CLI: $(firebase --version)" && \
echo "NotebookLM CLI: $(nlm --version 2>/dev/null || echo '請確認安裝')" && \
echo "=== 驗證完成 ==="
```

---

祝您與您的 AI 助理在 macOS 上對話愉快，享受極速開發的樂趣！🚀🍎
