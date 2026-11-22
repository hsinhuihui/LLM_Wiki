# Git & GitHub 專業圖解知識庫目錄 (Wiki Index)

> 這裡是知識庫的中央索引目錄，由 Agent 依據 `AGENTS.md` 規範自動維護。紀錄所有攝取來源（Raw Sources）、知識庫章節與簡報模組。

---

## 📥 原始資料來源庫 (Ingested Sources, 5/5 已達標)

| 編號 | 來源檔案名稱 | 來源主題摘要 | 對應模組 |
| :---: | :--- | :--- | :---: |
| **01** | `GitHub 是什麼？新手入門看這篇,GitHub Copilot 教學一次上手！.pdf` | Git vs GitHub 本質差別、初次推送 6 步驟、GitHub Copilot 指南 | **Module 03** |
| **02** | `Git - 分支和合併的基本用法.pdf` | Git 官方手冊：分支建立與切換、Fast-forward 合併、三方合併與衝突標記排查 | **Module 02** |
| **03** | `Learn-Git-in-30-days_zh-tw_18.md at master · doggy8088...pdf` | Will 保哥 30 天精華：修改 commit 紀錄、`commit --amend`、`reset --soft/hard` 與版本整理黃金法則 | **Module 04** |
| **04** | `Day 16：【GitHub 協作流程】Pull Request 機制的開立與 Code Review 流程...pdf` | iT 邦幫忙鐵人賽：Pull Request (PR) 機制、Code Review 評審禮儀、`Squash and merge` 壓縮合併策略 | **Module 05** |
| **05** | `Git上的三種工作流程...by Bowen...pdf` | 團隊分支策略大對決：Git Flow（傳統多軌）vs GitHub Flow（極簡主幹）vs GitLab Flow（上游優先） | **Module 05** |

---

## 🎨 綜合獨立交付成果：圖文講義與投影簡報 (Deliverables)

> 依據作業最新交付規範與 GitHub Pages 託管需求，全知識庫 5 篇文獻精華已完整編譯並部署於**專案第一層根目錄**，提供兩種無縫切換的閱讀模式：

1. 📖 **【首選推薦】日系清新圖文講義**：[`git-handout.html`](file:///c:/Users/hsin/Desktop/GenAI/HW/HW10/LLM%20Wiki%20Notes/git-handout.html)
   - **特色**：長滾動自然流暢排版，**天然根絕 16:9 投影片高度裁切困擾**。
   - 配備左側懸浮目錄導航（Sticky TOC）、頂端閱讀進度條、一鍵複製指令按鈕、課堂便籤盒與一鍵列印/轉存 PDF 支援。
2. 🖥️ **16:9 全螢幕簡報投影版（DAG 拓撲與視覺圖譜全景）**：[`index.html`](file:///c:/Users/hsin/Desktop/GenAI/HW/HW10/LLM%20Wiki%20Notes/index.html) ｜ [`git-presentation.html`](file:///c:/Users/hsin/Desktop/GenAI/HW/HW10/LLM%20Wiki%20Notes/git-presentation.html)
   - **特色**：24 頁全域進度控制、動態篇章徽章、章節快速下拉選單、以 Graph 雙欄視角（左 52% 向量圖譜 + 右 48% 技術剖析）解構三大空間狀態轉移、Commit DAG、分支分岔與遠端拓撲。
   - `index.html` 設為根目錄入口，開啟 GitHub Pages 即可直接透過線上網址全螢幕展示。

---

## 💡 核心概念篇 (Concepts)

- [三個工作區域：工作區、暫存區與版本庫](concepts/three-areas.md)
  - *圖解比喻*：修改工作桌、寄件打包區、永久版本庫存檔
  - *簡報單元*：Module 01
- [Git 分支機制與合併原理：Fast-forward 與三方合併](concepts/branch-and-merge.md)
  - *圖解比喻*：可移動的便利貼書籤；指標向前滑動 vs 追溯共同祖先建立新存檔點
  - *簡報單元*：Module 02
- [Git 與 GitHub 的差別：本機工具 vs 雲端專案託管平台](concepts/git-vs-github.md)
  - *圖解比喻*：本機版本控制引擎 vs 雲端協作與代碼審查平台
  - *簡報單元*：Module 03
- [AI 輔助開發實務：GitHub Copilot 指南](concepts/github-copilot.md)
  - *圖解比喻*：編輯器即時代碼補全助手、Tab 鍵採納與上下文型別定義
  - *簡報單元*：Module 03 / Module 05

---

## 🧭 實戰流程篇 (Workflows)

- [首次推送專案：把本地專案推上 GitHub 遠端倉庫](workflows/first-push.md)
  - *技術流向*：`git init` → `git add .` → `git commit` → `git branch -M main` → `git remote add origin` → `git push -u origin main`
  - *簡報單元*：Module 03
- [GitHub 協作流程：Pull Request (PR) 開立、Code Review 與壓縮合併](workflows/pull-request-and-review.md)
  - *核心機制*：Feature Branch 提交提案、同儕建設性評審、`Squash and merge` 維護整潔歷史
  - *簡報單元*：Module 05
- [團隊分支工作流比較：Git Flow vs GitHub Flow vs GitLab Flow](workflows/git-branching-strategies.md)
  - *架構比對*：傳統嚴謹五軌 vs 敏捷單主幹 vs 上游優先（Upstream First）環境部署
  - *簡報單元*：Module 05

---

## ⚡ 常用指令篇 (Commands)

- [`git init` — 初始化本地 Git 儲存庫](commands/git-init.md)
- [`git add` — 將檔案變更加入暫存區](commands/git-add.md)
- [`git commit` — 封裝變更並建立歷史版本節點](commands/git-commit.md)
- [`git status` — 檢視當前工作區與暫存區狀態](commands/git-status.md)
- [`git log` — 檢視版本歷史提交紀錄](commands/git-log.md)
- [`修正 Commit 歷史紀錄：amend、reset 與版本整理黃金法則`](commands/git-reset-and-amend.md)
  - *核心指令*：`git commit --amend`、`git reset --soft/hard HEAD^`、`git reset --hard ORIG_HEAD`
  - *簡報單元*：Module 04

---

## 🛠️ 常見錯誤排查篇 (Troubleshooting)

- [合併衝突排查與解決：標記語法與標準處理流程](troubleshooting/merge-conflicts.md)
  - *標記解析*：`<<<<<<< HEAD`、`=======`、`>>>>>>>` 衝突區段處理
  - *標準解法*：手動編輯移除標記 → `git add` 標記已解決 → `git commit` 完成三方合併
  - *簡報單元*：Module 02
