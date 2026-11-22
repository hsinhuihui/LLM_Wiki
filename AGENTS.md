# AGENTS.md — Git & GitHub 專業圖解知識庫與簡報管家規範

本文件是此儲存庫的核心 Schema 與 Agent 行為準則。任何接手本專案的 LLM Agent 必須嚴格遵守以下角色定義、目錄結構、資料處理流程、文案風格與視覺設計規範。

---

## 1. 核心定位與願景

本知識庫參考 **Andrej Karpathy 的 LLM Wiki 模式**：
- **知識是持續累積、交叉關聯的複利資產**，而非每次臨時 RAG 檢索。
- **Wiki 由 LLM 維護，人類負責提供來源與提問**。
- **資料攝取規範**：至少 Ingest 5 篇原始資料（`raw/`），提煉並建構成結構化、高度互聯的技術知識網絡。
- **最終產出**：將抽象的 Git & GitHub 概念轉化為**「日系簡約、清新專業、圖解輔文」的現代知識庫**，並具備**一鍵編譯為「一份高質感綜合獨立 HTML 圖文講義／簡報」**的能力（首選推薦具備側邊目錄與無高度限制的圖文講義型）。

---

## 2. 文案風格與專業度準則 (Tone & Metaphor Guidelines)

### 2.1 專業、乾淨、適度生活化
- **受眾定位**：希望踏實學好 Git/GitHub 的工程師、設計師與初學者。簡報必須呈現**清楚、條理分明、高專業質感**的視覺與文字。
- **可以簡單舉例**：允許使用生活化、直觀的日常物件輔助理解抽象架構（例如：暫存區 = 寄件打包箱；Commit = 永久存檔快照；Remote = 雲端同步端點；Branch = 獨立工作線；Stash = 工作抽屜）。
- **嚴禁過度誇張與幼稚化（Strict Prohibition）**：
  - **嚴格禁止童話、奇幻、冒險島或中二用語**。
  - **禁止詞彙範例**：`雲端冒險島`、`遠端航行`、`出海`、`新手村出發`、`神秘空間`、`魔法陣`、`心靈感應小精靈`、`時光倒流魔法書`、`小動物畫家`、`暗礁` 等。
  - **文案標準**：直截了當講清楚「為什麼要這樣設計」、「底層邏輯是什麼」、「解決什麼問題」，不堆砌多餘的煽情故事。

---

## 3. 目錄架構

```text
.
├── AGENTS.md                    # 本文件（系統綱領）
├── index.html                   # [GitHub Pages 首頁] 24 頁全景簡報預設入口
├── git-presentation.html        # [簡報產出] 16:9 全螢幕獨立簡報投影版
├── git-handout.html             # [講義產出 / 首選推薦] 日系清新綜合圖文講義（自適應長滾動、無裁切問題）
├── raw/                         # [唯讀來源層] 存放原始教學文章、筆記、官方文件（至少 5 篇，Agent 不得竄改）
└── wiki/                        # [知識庫層] Agent 負責編譯與維護的 Markdown 檔案
    ├── index.md                 # 知識總目錄（含各頁摘要、分類與 5 篇來源清單）
    ├── log.md                   # 時序操作日誌（Ingest, Query, Lint, Slide 產出紀錄）
    ├── concepts/                # 核心概念（三個區域、HEAD 指標、分支本質等）
    ├── commands/                # 常用指令（init, add, commit, push, pull, reset 等）
    ├── workflows/               # 實戰流程（首次推送、GitHub PR 協作、衝突解決、工作流等）
    └── troubleshooting/         # 錯誤排查與救援（撤銷 commit、復原檔案、衝突解決等）
```

---

## 4. Wiki 頁面標準格式

所有在 `wiki/` 下建立的筆記必須採用標準 Frontmatter 與固定結構：

```markdown
---
title: "頁面標題（例如：暫存區 Staging Area）"
tags: [git-core, beginner]
analogy: "寄件打包區 / 預覽拍攝台"
chapter: "01-git-basics" # 對應單一綜合簡報的篇章主題
updated: YYYY-MM-DD
---

# 頁面標題

## 概念圖解與比喻 (Visual Analogy)
> 用最簡潔、直觀的生活或工程物件比喻這個概念。
> 例如：Staging Area 是寄件前的打包台，只有裝進箱子的修改才會被封裝進下一個提交版本（Commit）中。

## 核心觀念 (Core Concept)
- 概念的白話技術解釋（清楚交代工作原理與資料流向）。
- 為什麼需要它？解決了什麼問題？

## 常用指令與操作 (Key Commands)
```bash
# 附帶清楚技術註解的指令範例
git add <檔案名稱>
```

## 常見誤解與排查 (Gotchas & Troubleshooting)
- 開發者常踩的坑或報錯訊息。
- 具體成因與標準解決步驟。

## 簡報分鏡建議 (Slide Blueprint)
- **畫面焦點**：[例如：左側檔案修改清單，中央暫存區卡片，右側 Commit 歷程節點]
- **配色建議**：山吹黃底狀態卡片、珊瑚粉核心指令
- **建議版面**：架構對比 / 步驟流向圖 / 雙欄排版
```

---

## 5. 日系清新簡約 HTML 簡報設計規範（Design System）

當 Agent 生成或更新根目錄簡報 `git-presentation.html`（或 `index.html`）時，**必須嚴格遵循以下 CSS 與 SVG 設計規範**：

### 5.1 設計理念
- **日系清新、簡約專業、和風文具質感**（Technical Zine / Japanese Minimalist Design）。
- **淺色和紙底**，版面俐落通透，具備高可讀性與專業感。
- **平塗無漸層（Flat Solid Color）**，拒絕浮誇發光特效。

### 5.2 色彩規範 (Color Tokens)
```css
:root {
  /* 背景與基底 */
  --bg-washi: #FFFCF6;       /* 和紙白（全域簡報底色） */
  --card-white: #FFFFFF;     /* 純白卡片底色 */

  /* 墨灰線條與文字（核心輪廓） */
  --ink-charcoal: #3E3A39;   /* 3px 粗線條、文字、圖標描邊 */

  /* 四色功能性調色盤 */
  --coral-pink: #F2A497;     /* 珊瑚粉：核心動作、HEAD、警告、重要按鈕 */
  --yamabuki-yellow: #F6D27A;/* 山吹黃：工作區、本地狀態、提示、待辦事項 */
  --mizuiro-blue: #A8D3E6;   /* 水色：遠端 GitHub、同步流程、網路節點 */
  --wakatake-green: #B9DAA5; /* 若竹綠：成功提交、主要分支 main、完成狀態 */
}
```

### 5.3 框線與圓角規範
- **所有邊框一律**：`border: 3px solid var(--ink-charcoal);`
- **卡片大圓角**：`border-radius: 20px;` 或 `22px;`
- **標籤與按鈕**：`border-radius: 999px;`（膠囊狀）
- **實體硬邊陰影（無模糊）**：`box-shadow: 4px 4px 0px var(--ink-charcoal);`

### 5.4 字型與排版
- 內嵌 Google Fonts「Huninn（粉圓體）」：
  ```html
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Huninn&display=swap" rel="stylesheet">
  ```
- 內文字距與行高：`letter-spacing: 0.02em; line-height: 1.6;`

### 5.5 SVG 插圖繪製原則
- **一律使用手繪風內嵌 `<svg>`**，不依賴外部圖片檔案。
- SVG 描邊：`stroke="#3E3A39" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"`
- SVG 畫布邊界：嚴格控制圖形座標在 `viewBox` 範圍內，確保左右預留至少 15px 安全邊距，杜絕內容被裁切。
- **繪圖主題聚焦專業圖解**：
  - 架構圖、流程圖、終端機視窗、Git Commit 節點樹、分支流向、資料傳輸管線、乾淨的設備/雲端示意圖示。
  - 不使用童話動物角色或誇張奇幻物件，保持簡潔專業且親切。

### 5.6 簡報互動規範 (Presentation Runtime)
- **單一獨立 HTML 檔案**：整份簡報所有篇章濃縮於單一檔案，離線可直接雙擊在瀏覽器全螢幕播放，零外部依賴。
- 固定的 16:9 簡報投影比例（在各種螢幕尺寸下等比例縮放居中）。
- 鍵盤控制：`ArrowRight` / `Space` / `PageDown` 切換下一頁；`ArrowLeft` / `PageUp` 切換上一頁；`F` 切換全螢幕。
- 畫面元素：
  1. 上方有**當前篇章徽章、全域進度條**與**頁碼徽章**（例如 `05 / 25`）。
  2. 左右各有一個翻頁按鈕。
  3. 平滑溫和的頁面淡入淡出動效。

### 5.7 日系清新圖文講義規範（Technical Handout / Study Guide Runtime）[首選推薦]
- **單一獨立 HTML 講義檔**（`git-handout.html`）：
  - 徹底克服 16:9 投影片高度受限容易截斷文字的痛點，採用**自然垂直滾動圖文排版**。
  - 左側配備 **Sticky 懸浮目錄側邊欄**，支援章節即時高亮與點擊流暢跳轉。
  - 頂端設有 **即時閱讀進度指示條（Reading Progress Bar）**。
  - 終端機指令區配備 **一鍵複製指令按鈕（Copy to Clipboard）**。
  - 支援 `@media print`：點擊頂端「列印 / 轉存 PDF」即可直接印製或匯出高品質實體講義。

---

## 6. 單一綜合簡報篇章規劃 (Comprehensive Slide Blueprint)

全份簡報（`git-presentation.html` / `index.html`）整合知識庫 5 篇 raw 來源之技術精華，分為五大核心篇章：

### 篇章一：Git 核心架構：工作區、暫存區與版本提交 (Ch 1)
- 版本控制核心價值與 Ctrl+S 的致命缺點。
- 三大核心工作空間（Working Tree / Staging Area / Repository）職責與比喻。
- 日常開發標準三步曲（工作區修改 → `git add` → `git commit`）。
- 常用起手指令與新手防雷避坑錦囊。

### 篇章二：Git 分支與合併：原理、衝突解決與最佳實踐 (Ch 2)
- 分支本質為輕量可移動指標（40 字元 Hash 參照）與 HEAD 聚光燈。
- 建立與切換分支最佳實踐（`switch -c`、切換前維持工作區乾淨）。
- 兩種合併模式：Fast-forward 線性快進 vs 三方合併（3-way Merge 尋找共同祖先）。
- 合併衝突排查：標準衝突標記結構（`<<<<<<<`、`=======`、`>>>>>>>`）與四步手動解套流程。

### 篇章三：GitHub 協作基礎：遠端倉庫與推送流程 (Ch 3)
- Git 本機工具 vs GitHub 雲端託管平台的架構分工。
- 首次將本地專案推上 GitHub 的標準 6 步驟流程。
- 遠端同步日常三大操作：`git clone` 下載、`git pull` 拉取、`git push` 推送。
- 新手推送三大常見疑難（Token 驗證、空目錄、分支名稱不同步）。
- AI 輔助開發心法：GitHub Copilot 編輯器輔助最佳實務。

### 篇章四：版本回溯與救援：Reset、Revert 與 Stash 實戰 (Ch 4)
- 版本整理黃金法則：本地未推送自由整理，已推送遠端嚴禁竄改歷史。
- `git commit --amend` 微調最後一次提交訊息與補漏檔案。
- `git reset --soft` vs `git reset --hard` 深度對比與暫存區狀態影響。
- `git reset --hard ORIG_HEAD` 一鍵後悔救命藥與 `.git/objects/` 底層存檔機制。
- `git stash` 臨時工作抽屜：暫存手邊半成品以快速切換任務。

### 篇章五：GitHub 團隊協作與工作流：PR、Code Review 與 Branching Flow (Ch 5)
- Pull Request (PR) 提案機制與代碼品質守門員角色。
- 開立 PR 標準流程與建設性 Code Review 審查禮儀。
- `Squash and merge` 壓縮合併：保持主幹 Commit 歷史整潔的最佳實踐。
- 三大主流分支工作流評析：Git Flow（傳統嚴謹多軌）vs GitHub Flow（極簡敏捷單主幹）vs GitLab Flow（上游優先環境部署）。
- 上游優先原則（Upstream First）與全篇協作總結口訣。

---

## 7. Agent 操作指令與標準作業流程 (Standard Workflows)

### 流程一：`Ingest`（攝取資料）
1. 讀取 `raw/` 中的新文件（確保至少累積 5 篇來源）。
2. 提煉技術要點，並歸納出簡潔的生活化/圖解比喻（**嚴禁童話與誇張修辭**）。
3. 建立或更新 `wiki/` 頁面（符合標準 Frontmatter 與結構）。
4. 更新 `wiki/index.md` 與 `wiki/log.md`。

### 流程二：`Lint`（知識庫體檢）
定期檢查 `wiki/`：
- 是否有孤立頁面或斷裂連結？
- 是否有過度童話化或不合規範的語氣？
- 概念之間是否有技術定義矛盾之處？

### 流程三：`Compile Slide`（編譯綜合簡報）
1. 讀取 `wiki/` 內所有對應篇章的技術內容與分鏡藍圖。
2. 依據 Design System 將五大篇章編譯為**單一綜合 HTML 簡報檔**（`slides/git-presentation.html`）。
3. 確保風格專業、排版俐落、SVG 圖解座標在 viewBox 內無裁切。
4. 更新 `wiki/log.md` 與 `wiki/index.md`。

---

## 8. 禁令與原則 (Strict Constraints)
- **作業交付規範**：原始資料必須至少 Ingest 5 篇，最終產出必須為**單一一份 HTML 簡報**。
- **嚴禁誇張與童話修辭**（禁止冒險島、航行、魔法、精靈等詞彙）。
- **嚴禁使用漸層色彩**（禁止使用 `linear-gradient`，全面使用平塗色塊）。
- **嚴禁深色模式 / 黑色背景**（一律淺色和紙白 `#FFFCF6`）。
- **嚴禁省略 3px 墨灰框線**（維持實體質感）。
- **保持專業、俐落與平易近人**：清晰、條理、工程級的整潔度。
