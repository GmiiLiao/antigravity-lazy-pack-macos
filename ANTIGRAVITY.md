# 🚀 專案駕駛艙 (ANTIGRAVITY Cockpit)

> 版本：v1.0-macOS · 建立於 2026-05-23
> 告訴 AI 助理：「請執行開工 SOP」或「請執行收工 SOP」

---

## 🌐 我的環境設定

| 項目 | 設定值 |
|------|--------|
| 作業系統 | macOS |
| 主要工作目錄 | ~/Documents/ |
| Obsidian Vault | ~/Documents/ObsidianVault/ |
| GitHub 帳號 | GmiiLiao |
| Firebase 帳號 | nicholas@gmii.tw |
| Firebase Token | （已存於 ~/.zshrc 的 FIREBASE_TOKEN） |

### Firebase 專案清單
| 專案名稱 | Project ID |
|---------|------------|
| chatroom-store | chatroom-store |
| kittenbottw | kittenbottw-web |
| learn-gmii | learn-gmii-495505 |

### NotebookLM 筆記本（前3常用）
| 筆記本 | 說明 |
|--------|------|
| 遊戲化教學運用手冊 | 教學設計 |
| 親子旅館活動規劃預想 | 活動企劃 |
| 合作方案 | 商業合作 |

---

## ☀️ 開工 SOP

> 指令：「請執行開工 SOP」

請 AI 助理依序完成以下步驟：

1. **顯示今日資訊**
   - 顯示目前日期時間（台北時間）
   - 顯示今天是星期幾

2. **讀取今日任務**
   - 讀取 Obsidian Vault 中 `每日任務/今日任務.md`
   - 若不存在，自動建立今日的任務頁面（以 YYYY-MM-DD 命名）

3. **確認服務連線狀態**
   - 執行 `GITHUB_TOKEN='' gh auth status` 確認 GitHub
   - 執行 `nlm list notebooks` 確認 NotebookLM（列出前3筆）

4. **顯示開工摘要**
   - 整理成簡潔的「今日工作準備報告」

---

## 🌙 收工 SOP

> 指令：「請執行收工 SOP」

請 AI 助理依序完成以下步驟：

1. **Git 自動提交**
   - 找出今日有修改的專案目錄
   - 詢問我是否要 commit（顯示 `git status`）
   - 執行 commit，訊息格式：`[YYYY-MM-DD] 今日工作摘要`
   - Push 到 GitHub

2. **建立工作日誌**
   - 在 Obsidian `工作日誌/YYYY-MM-DD.md` 建立今日紀錄
   - 內容包含：完成事項、遇到問題、明日計畫

3. **顯示收工摘要**
   - 今日完成了什麼
   - 明日建議優先處理什麼

---

## 🆕 專案初始化 SOP

> 指令：「請初始化新專案 [專案名稱]」

請 AI 助理依序完成以下步驟：

1. **建立本地目錄**
   ```bash
   mkdir -p ~/Documents/[專案名稱]
   cd ~/Documents/[專案名稱]
   git init
   ```

2. **建立基本結構**
   - `.gitignore`（含 macOS .DS_Store）
   - `README.md`

3. **推送到 GitHub**
   ```bash
   GITHUB_TOKEN='' gh repo create [專案名稱] --public --source=. --remote=origin --push
   ```

4. **在 Obsidian 建立專案筆記**
   - 路徑：`專案/[專案名稱].md`
   - 包含：專案目標、GitHub 連結、建立日期

5. **（選用）初始化 Firebase**
   ```bash
   firebase init --token $FIREBASE_TOKEN
   ```

---

## 📋 常用快速指令

```bash
# GitHub
GITHUB_TOKEN='' gh repo list --limit 10

# Firebase
firebase projects:list --token $FIREBASE_TOKEN

# NotebookLM
nlm list notebooks
nlm query [筆記本ID] "你的問題"

# Obsidian Vault
ls ~/Documents/ObsidianVault/
```

---

*最後更新：2026-05-23 · Anti-Gravity 2 macOS 版*
