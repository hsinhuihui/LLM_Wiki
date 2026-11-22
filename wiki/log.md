# 知識庫操作日誌 (Wiki Log)

> 本日誌記錄所有知識庫的演進歷史（Ingest、Lint、Slide 編譯等）。以時間倒序或順序排列，每筆紀錄開頭符合 `## [YYYY-MM-DD] <動作> | <標題>` 規範。

---

## [2026-11-22] Refactor & Cleanup | 移除舊 slides 資料夾並同步修正全域架構規範與路徑
- **移除冗餘**：考量核心成果（`index.html`、`git-presentation.html`、`git-handout.html`）已全數遷移至專案第一層根目錄，依使用者需求安全刪除 `slides/` 資料夾，消除重複檔案，簡化 GitHub 倉庫結構。
- **規範更新（`AGENTS.md`）**：
  - 更新「第 3 節目錄架構」：正式將第一層根目錄明定為核心展示層（包含 GitHub Pages 入口 `index.html`、全螢幕簡報 `git-presentation.html` 與圖文講義 `git-handout.html`）。
  - 更新「第 5 節設計規範」與「第 6 節篇章規劃」：全面修正簡報生成與維護路徑為根目錄檔案。
- **索引更新（`wiki/index.md`）**：同步將 Deliverables 成果連結更新至根目錄，修正本機超連結為最新路徑，確保知識庫中央目錄精確無誤。

---

## [2026-11-22] Deploy & Export | 簡報與圖文講義部署至專案根目錄（第一層資料夾）
- 依據使用者 GitHub 上傳需求（如 GitHub Pages 直接託管或第一層直接預覽），已將簡報與講義同步部署至專案最外層：
  - **`index.html`**：直接複製 `slides/git-presentation.html` 至根目錄，上傳至 GitHub 並啟用 GitHub Pages 時，預設首頁即可直接開啟 24 頁全景簡報。
  - **`git-presentation.html`**：同步保留具名簡報檔案於根目錄。
  - **`git-handout.html`**：同步將長滾動圖文講義放置於根目錄，確保根目錄簡報右上角切換至講義的超連結（`<a href="git-handout.html">`）與講義切回簡報之連結雙向無縫互通。
- 原 `slides/` 目錄下的來源檔案保持完整保留。

---

## [2026-11-20] Fix & Polish | Slide 05 `add` 膠囊與 Slide 23 分支工作流文字邊界精修
- 依據使用者最新截圖回饋：
  1. **Slide 05（git status 狀態座標圖）**：
     - 原問題：中介通道寬度不足，導致 `add` 按鈕右側邊緣直接切過並壓在綠色暫存區方框的左側黑線上。
     - 解決方案：將紅色未暫存方框寬度調整為 175px（$x:15 \sim 190$），綠色已暫存方框設定為 $x:270 \sim 445$，中間空隙一舉拓寬至 **80px**；`add` 按鈕（寬 38px）與下方箭頭精準置中於 $x=230$，左右兩側**各留出 21px 完整無暇的純白淨空**，絕不碰觸任何邊框。
  2. **Slide 23（三大團隊分支工作流拓撲）**：
     - 原問題：Flow 2 中的 `feature branch ➔ PR` 文字過於靠右且撞上卡片右邊框；Flow 3 中的 `上游優先原則 (Upstream First)` 文字太長，末端的 `First` 超出右側方框被裁切。
     - 解決方案：全面使用 `text-anchor="middle"` 置中對齊；Flow 2 標籤置中於弧線下方 $x=295$（距右邊框高達 85px 淨空）；Flow 3 將管線方框設定為 245px，管線字樣置中封裝於內，下方「上游優先原則 (Upstream First)」置中於 $x=292$，距離右邊界維持高達 **68px** 之安全緩衝，徹底確保文字 100% 收納於方框內部，無任何裁切或溢出。
  3. **Slide 04（三大核心空間）**：
     - 順帶將工作區、暫存區與版本庫間的兩道過渡間隙進一步拓寬至 64px，`add` 與 `commit` 按鈕兩側均勻維持 10px～13px 呼吸空間。

---

## [2026-11-20] Fix & Refine | 簡報 10 大視覺重疊與換頁控制深度精修
- 依據使用者具體截圖與指令回饋，針對 [`slides/git-presentation.html`](file:///c:/Users/hsin/Desktop/GenAI/HW/LLM%20Wiki%20Notes/slides/git-presentation.html) 進行逐頁像素級精準重構：
  1. **Slide 04（三大空間狀態）**：將工作區、暫存區、版本庫中間空隙由 37px 拓寬至 53px 與 56px，`add` 與 `commit` 膠囊按鈕及箭頭完全獨立置中，兩側預留充裕呼吸空隙，徹底告別邊框壓迫。
  2. **Slide 11、12、13（分支合併拓撲箭頭與圓圈）**：重新計算切線幾何座標，所有指向節點（C2、C3、C4、C5）之實體與虛線箭頭尖端嚴格停止於圓外半徑 $(r + 4\text{px})$ 處；Slide 12 之 `main` 垂直三角指針停止於 $y=124$，距 C3 頂端留有 5px 乾淨淨空，杜絕任何侵入圓圈重疊。
  3. **Slide 15（Git vs GitHub 雙向傳輸）**：雙向 push / pull 箭頭縮短至兩端距離方框 7px 以上安全距離；「Repo 雲端託管」標籤獨立自圓圈下方移出至 $y=155$，字圖徹底分離無重疊。
  4. **Slide 17（origin/main 唯讀書籤）**：左側「本地 main 指標」與「origin/main 唯讀書籤」寬度拓寬為 200px，「本地領先新提交」與「記錄上次同步點」所有說明文字 100% 收納於卡片內；fetch 虛線管線兩端均留有 7px 以上淨空不貼邊。
  5. **Slide 18（日常同步流程）**：`pull` 方框移至 $y=120$（箭頭位於 $y=152$），`push` 方框移至 $y=192$（箭頭位於 $y=225$），方框與箭頭管線垂直完全錯開 8~9px，徹底消除方框壓在線上的問題。
  6. **Slide 19（GitHub Copilot 整合）**：淡黃色幽靈建議框拓寬至 200px，程式碼文字精簡為 `function isEmail(str)`，字距與左右邊距寬裕舒展。
  7. **Slide 21（amend vs reset）**：在卡片內部右側打造專屬彩色膠囊徽章，「原位抽換頂端節點」與「HEAD 指標倒退回 C1」文字完整收納於膠囊與主卡片內（右界 $x=425 < 440$）。
  8. **Slide 22（PR Squash 壓縮）**：Feature 卡片高度精簡為 100px，main 卡片下移至 $y=180$，中間留出 65px 淨空區，「Squash 壓縮 ➔」方框置中於 $y=130$，上下各留有 15px 以上安全距離，徹底根絕與上下卡片邊框之重疊。
  9. **Slide 24（全域換頁控制守衛）**：在 `updateDeck()` 中加入終點頁狀態控制，當位於第 24 頁時，下一頁按鈕自動轉換為提示「已達最後一頁 ✓」並禁用（`disabled = true; cursor: not-allowed`）；鍵盤與點擊事件皆設置邊界守衛，禁止從最後一頁循環跳轉回第一頁。

---

## [2026-11-20] Fix & Optimize | 簡報圖譜全面放大：消除留白、提升圖元與文字飽滿度
- 問題排查：在 Slide 03、04 等多個頁面中，左欄 Graph 卡片面積充裕（約 550px × 380px），但內嵌 SVG 的 viewBox 預設過小（360×200），且圖元（矩形、節點圓形、文字）未充分利用畫布，導致圖示在巨大的白框中顯得過於小巧且四周留白過多。
- 解決方案：
  - **SVG 畫布比例重構**：將左欄所有 SVG 的 `viewBox` 統一調整為更契合卡片比例的 `0 0 460 310`。
  - **CSS 縮放自適應**：將 `.graph-stage-card svg` 設為 `width: 100%; height: 100%;`，讓圖譜自適應填滿卡片內部。
  - **節點與文字全面放大 150% ~ 200%**：
    - Commit 圓形節點半徑由 `r: 14~16` 大幅提升至 `r: 24~28`。
    - 三大空間容器高度由 130px 擴展至 260px，寬度由 60~95px 擴展至 115~135px。
    - 標籤與內文文字由原本的 9~10px 放大至 12~15px 粗體，大幅提升遠距與投影時的可讀性。
  - **版面視覺對稱**：適度微調 `.graph-layout` 比例至 `1.12fr 0.88fr`，圖譜飽滿大器，兩側排版平衡優雅。

---

## [2026-11-20] Compile Slide | Graph 導向 24 頁綜合簡報正式發布
- 依據經使用者確認之 `graph_presentation_blueprint.md` 藍圖，正式完成【階段四：HTML/SVG 獨立簡報編譯】。
- 更新產出檔案：[`slides/git-presentation.html`](file:///c:/Users/hsin/Desktop/GenAI/HW/LLM%20Wiki%20Notes/slides/git-presentation.html)。
- 核心實作重點：
  - **總頁數精確收斂為 24 頁**，涵蓋五大圖譜階段（全景導覽、空間狀態圖、Commit DAG、分支合併拓撲、遠端拓撲圖、團隊工作流）。
  - **專業雙欄對稱版面**：全面落實「左側 52% 向量 SVG Graph 卡片 + 右側 48% 技術剖析與終端指令」。
  - **精確圖元標準**：Commit 圓形節點（短 Hash）、Branch 膠囊標籤（main/feature）、HEAD 聚光燈（珊瑚粉）、遠端雲端端點與資料流管線。
  - **嚴格安全邊距**：所有向量 SVG 圖譜預留四周至少 15px ~ 20px 安全邊距，杜絕左右裁切；投影片上下 padding 控制於 14px，容器 `max-height: 94vh`，底部橫幅與底欄皆擁有充裕呼吸空間。
  - **交互控制**：頂端動態章節徽章、進度條百分比、頁碼計數器（01 / 24）、底部章節下拉跳轉與鍵盤翻頁全螢幕支援。

---

## [2026-11-20] Plan & Blueprint | Graph 導向簡報：視覺語彙規範與 24 頁逐頁分鏡腳本草案
- 依據使用者需求確立「以 Graph 方式重新設計投影片」之執行準則。
- 完成【階段二：Graph 視覺語彙規範】：
  - 確立「左側 52% 向量 SVG Graph + 右側 48% 技術剖析與指令卡片」的專業對稱版面。
  - 制定 Commit 節點（圓形 Hash）、Branch 指標（膠囊標籤）、HEAD 聚光燈（珊瑚粉）、Remote 端點（水色雲端）與三大空間容器之視覺符號標準。
- 完成【階段三：24 頁逐頁分鏡腳本】：
  - 完整規劃 24 頁的 Graph 視覺焦點、狀態轉移邏輯、右側解說與邊界防裁切檢核要點。
  - 產出詳細藍圖文件：`graph_presentation_blueprint.md`。

---

## [2026-11-20] Compile Handout | 單一綜合圖文講義：Git & GitHub 現代圖文講義 (Technical Study Guide)
- 依據使用者最新偏好「以推薦的方式，做成圖文講義型」，正式編譯並發布**單一獨立綜合圖文講義**。
- 產出檔案：[`slides/git-handout.html`](file:///c:/Users/hsin/Desktop/GenAI/HW/LLM%20Wiki%20Notes/slides/git-handout.html)。
- 格式優勢與核心特性：
  - **長滾動流暢圖文排版**：徹底根絕 16:9 固定比例投影片垂直空間緊繃、容易裁切卡片與橫幅底部的痛點。
  - **左側懸浮章節目錄（Sticky TOC）**：採用 IntersectionObserver 即時監聽閱覽位置高亮章節，支援一鍵流暢錨點跳轉。
  - **頂端閱讀進度條**：直觀顯示閱覽進度百分比。
  - **終端機一鍵複製按鈕**：所有指令區塊右上角皆具備「複製指令」互動回饋。
  - **支援列印與轉存 PDF**：內建 `@media print` 樣式，點擊頂端「列印 / 轉存 PDF」按鈕即可匯出高質感實體或數位講義。
  - **雙模式自由切換**：頂端提供按鈕可隨時一鍵跳轉至 16:9 簡報投影版（[`slides/git-presentation.html`](file:///c:/Users/hsin/Desktop/GenAI/HW/LLM%20Wiki%20Notes/slides/git-presentation.html)）。
- 涵蓋內容：整合全部 5 篇 raw 來源文獻，包含 6 大單元（00 講義導讀地圖、01 Git 核心架構、02 分支與合併、03 GitHub 遠端協作、04 版本回溯救援、05 團隊協作工作流、06 核心心法與日常速查清單）。
- 同步更新：`AGENTS.md`（新增 5.7 圖文講義規範）、`wiki/index.md`。

---

## [2026-11-19] Fix Layout | 綜合簡報：修復垂直高度過密導致底部橫幅被裁切問題
- 問題排查：在 Slide 16（版本歷史整理黃金法則）與部分包含底部口訣橫幅的頁面中，卡片垂直間距過大（padding 16px、行高 1.6），造成卡片與底部口訣橫幅推擠至舞台最下方，被底欄邊界與 `overflow: hidden` 裁切。
- 解決方案：
  - 全域容器優化：設定 `.deck-container` 的 `max-height: 94vh`，防止不同解析度筆電螢幕視窗溢出。
  - 緊湊化頂部與底部控制列：`.deck-header` 內距縮減至 `8px 20px`，`.deck-footer` 縮減至 `6px 20px`，為舞台釋放大量垂直空間。
  - 投影片內距優化：`.slide` 內距由 `26px 42px` 縮減至 `16px 36px`。
  - 卡片與字體行距微調：卡片內距調整為 `12px 14px`，行高收斂至 `1.45 ~ 1.5`，橫幅標籤外距調整至 `8px`。
  - 調整後 Slide 16 底部橫幅與底欄之間留有充足呼吸空間（逾 60px 安全緩衝），徹底根除裁切問題。

## [2026-11-19] Compile Slide | 單一綜合獨立 HTML 簡報：Git & GitHub 現代圖解指南
- 依據 `AGENTS.md` 最新規格，將 5 篇原始資料之提煉精華正式編譯為單一完整綜合簡報。
- 產出檔案：[`slides/git-presentation.html`](file:///c:/Users/hsin/Desktop/GenAI/HW/LLM%20Wiki%20Notes/slides/git-presentation.html)。
- 結構特色：
  - 共計 **25 頁完整 16:9 投影片**，劃分為五大篇章（總覽導讀、Git 核心架構、分支與合併實戰、GitHub 遠端協作、版本回溯救援、團隊協作工作流、全篇總結）。
  - 配備**動態章節徽章、連續進度條、即時章節下拉跳轉選單、全域頁碼計數與鍵盤導航（Home/End/F 全螢幕）**。
  - 嚴格落實日系和風文具風格（和紙白底 `#FFFCF6`、3px 墨灰框線、實體硬陰影、純內嵌向量 SVG 與 Huninn 粉圓體）。
  - 單檔零外部依賴，離線可直接雙擊瀏覽器全螢幕投影。

## [2026-11-19] Spec Update | 修訂 AGENTS.md：確立「至少 Ingest 5 篇資料，最後產出單一綜合 HTML 簡報」規範
- 依據作業最新需求修訂 `AGENTS.md`：
  - 目標確立：原始來源層維持至少 5 篇 raw 檔案，透過 LLM Wiki 體系建立互聯知識庫。
  - 產出結構升級：由原先分散的 5 份獨立簡報，轉為編譯為**單一綜合獨立 HTML 簡報檔**（`slides/git-presentation.html`）。
  - 單一簡報劃分五大篇章（Chapter 1~5），貫穿三大空間、分支合併、GitHub 遠端、版本救援與團隊協作工作流。
  - 同步更新 Design System、目錄結構、SVG 安全邊距與工作流規範。

## [2026-11-17] Fix Layout | Module 01: 修正封面三大空間 SVG 右側超出 viewBox 裁切問題
- 問題排查：`slides/01-git-basics.html` 第 1 頁封面圖解之「版本庫 (Repository)」卡片座標超出 SVG viewBox（原本 `viewBox="0 0 320 220"`，而第三張卡片終點達 `x=345`），造成右緣與文字被截斷。
- 解決方案：將 SVG 畫布座標拓寬為 `viewBox="0 0 380 220"`，重新計算三區域卡片（工作區、暫存區、版本庫）與動態箭頭之對稱分佈座標，左右預留 15px 邊距，確保完整居中顯示且不被裁切。

## [2026-11-17] Compile Slide | Module 05: GitHub 團隊協作與工作流：PR、Code Review 與 Branching Flow
- 依據 `wiki/workflows/pull-request-and-review.md` 與 `wiki/workflows/git-branching-strategies.md` 分鏡藍圖編譯。
- 產出檔案：[`slides/05-github-advanced.html`](file:///c:/Users/hsin/Desktop/GenAI/HW/LLM%20Wiki%20Notes/slides/05-github-advanced.html)。
- 包含 6 頁獨立 16:9 投影片：PR 價值、開立四步驟與 Code Review 守則、Squash and Merge 歷程壓縮、三大分支流（Git Flow / GitHub Flow / GitLab Flow）、上游優先（Upstream First）原則。

## [2026-11-17] Compile Slide | Module 04: 版本回溯與救援：Reset、Revert 與 Stash 實戰
- 依據 `wiki/commands/git-reset-and-amend.md` 分鏡藍圖編譯。
- 產出檔案：[`slides/04-time-travel.html`](file:///c:/Users/hsin/Desktop/GenAI/HW/LLM%20Wiki%20Notes/slides/04-time-travel.html)。
- 包含 6 頁獨立 16:9 投影片：版本整理黃金法則、`commit --amend` 補漏、`reset --soft` vs `--hard` 深度對比、`ORIG_HEAD` 救命後悔藥、`git stash` 抽屜機制。

## [2026-11-17] Compile Slide | Module 01: Git 核心架構：工作區、暫存區與版本提交（專業圖解版）
- 依據 `wiki/concepts/three-areas.md` 分鏡藍圖重新編譯為專業圖解版。
- 產出檔案：[`slides/01-git-basics.html`](file:///c:/Users/hsin/Desktop/GenAI/HW/LLM%20Wiki%20Notes/slides/01-git-basics.html)。
- 包含 6 頁獨立 16:9 投影片：版本控制核心價值、三大空間職責、日常三步提交、常用指令速查與避坑錦囊。

## [2026-11-17] Compile Slide | Module 02: Git 分支與合併：原理、衝突解決與最佳實踐
- 依據 `wiki/concepts/branch-and-merge.md` 與 `wiki/troubleshooting/merge-conflicts.md` 分鏡藍圖編譯。
- 產出檔案：[`slides/02-branch-merge.html`](file:///c:/Users/hsin/Desktop/GenAI/HW/LLM%20Wiki%20Notes/slides/02-branch-merge.html)。
- 包含 6 頁獨立 16:9 投影片：
  1. 封面（分支分岔拓撲圖與節點樹展示）。
  2. 分支的本質：輕量指針（40 字元 Hash 參照）與 HEAD 聚光燈角色。
  3. 建立與切換分支最佳實踐（`checkout -b`、`switch -c`、切換前維持工作區乾淨）。
  4. 兩種合併模式：Fast-forward 快進滑動 vs 三方合併（3-way Merge 尋找共同祖先建立 C6）。
  5. 合併衝突排查：衝突標記結構解析（`<<<<<<<`、`=======`、`>>>>>>>`）與四步標準解法。
  6. 分支管理實務速查表（`branch -v`、`branch -d`、`merge --abort`）。
- 嚴格遵守日系簡約、專業圖解與 Huninn 字型設計規範。

## [2026-11-17] Ingest | Git上的三種工作流程. 此篇介紹Git的三種工作流程，建議對Git有簡單了解再閱讀此篇...pdf
- 攝取來源：`raw/Git上的三種工作流程. 此篇介紹Git的三種工作流程，建議對Git有簡單了解再閱讀此篇。若要找git… _ by Bowen _ 儲思盆 _ Pensieve _ Medium.pdf`。
- 提煉核心觀念：
  - 功能驅動開發（Feature-driven development）核心精神。
  - Git Flow（五大分支傳統架構）vs GitHub Flow（以 main 為中心極簡分支）vs GitLab Flow（上游優先 Upstream First）。
- 新增 Wiki 頁面：
  - `wiki/workflows/git-branching-strategies.md`
- 關聯模組：**Module 05**。

## [2026-11-17] Ingest | Day 16：【GitHub 協作流程】Pull Request 機制的開立與 Code Review 流程.pdf
- 攝取來源：`raw/Day 16：【GitHub 協作流程】Pull Request 機制的開立與 Code Review 流程 - iT 邦幫忙__一起幫忙解決難題，拯救 IT 人的一天.pdf`。
- 提煉核心觀念：
  - Pull Request (PR) 作為視覺化討論區與代碼品質守門員。
  - GitHub 開立 PR 標準四步驟（Compare & pull request、Title/Desc、Reviewers、Create PR）。
  - Code Review 建設性審查原則與心理建設。
  - Squash and Merge（壓縮合併）保持主幹 Commit 歷史整潔的最佳實踐。
- 新增 Wiki 頁面：
  - `wiki/workflows/pull-request-and-review.md`
- 關聯模組：**Module 05**。

## [2026-11-17] Ingest | Learn-Git-in-30-days_zh-tw_18.md at master · doggy8088_Learn-Git-in-30-days · GitHub.pdf
- 攝取來源：`raw/Learn-Git-in-30-days_zh-tw_18.md at master · doggy8088_Learn-Git-in-30-days · GitHub.pdf`。
- 提煉核心觀念：
  - 版本整理黃金法則：未推送（Push）前可自由修訂，已發布歷史嚴禁竄改。
  - `git commit --amend` 微調最新提交訊息與補漏檔案。
  - `git reset --soft HEAD^` 撤銷提交但保留暫存變更。
  - `git reset --hard "HEAD^"` 強硬回退與 `git reset --hard ORIG_HEAD` 救命復原機制。
  - Git 物件儲存庫（`.git/objects/`）本質。
- 新增 Wiki 頁面：
  - `wiki/commands/git-reset-and-amend.md`
- 關聯模組：**Module 04**。

## [2026-11-17] Ingest | Git - 分支和合併的基本用法.pdf
- 攝取來源：`raw/Git - 分支和合併的基本用法.pdf`。
- 提煉核心觀念：
  - 分支本質為可移動指針（SHA-1 指標），`git checkout -b` 建立並切換。
  - Fast-forward（快進合併）線性歷史向前滑動機制。
  - Three-way Merge（三方合併）共同祖先（Common Ancestor）計算與合併提交（Merge Commit）。
  - 合併衝突（Merge Conflict）標記語法（`<<<<<<<`、`=======`、`>>>>>>>`）與手動編輯 + `git add` 標記已解決流程。
- 新增與更新 Wiki 頁面：
  - `wiki/concepts/branch-and-merge.md`
  - `wiki/troubleshooting/merge-conflicts.md`
- 關聯模組：**Module 02**。

## [2026-11-17] Refactor | 規格升級：確立「日系清新專業圖解」風格規範
- 修訂 [`AGENTS.md`](file:///c:/Users/hsin/Desktop/GenAI/HW/LLM%20Wiki%20Notes/AGENTS.md)：
  - 明確設定文案與簡報走「專業、乾淨、適度圖解比喻」路線。
  - **嚴格禁止**童話奇幻用語（如「雲端冒險島」、「遠端航行」、「魔法陣」、「小精靈」等）。
  - 將 SVG 插圖主題由萌系童話全面轉向「專業技術架構圖、流程圖、IDE 視窗圖解、節點樹」。
- 全面重構 [`slides/03-github-teamwork.html`](file:///c:/Users/hsin/Desktop/GenAI/HW/LLM%20Wiki%20Notes/slides/03-github-teamwork.html)：
  - 模組重命名為《GitHub 協作基礎：遠端倉庫與推送流程》。
  - 採用清爽高質感的工程圖解 SVG，移除中二與冒險用語，全面提升專業感。
- 同步更新中央目錄 `wiki/index.md`。

## [2026-11-17] Compile Slide | Module 03: 雲端冒險島！GitHub 團隊協作與推送
- 依據 `wiki/concepts/git-vs-github.md`、`wiki/workflows/first-push.md` 與 `wiki/concepts/github-copilot.md` 分鏡藍圖編譯。
- 產出檔案：[`slides/03-github-teamwork.html`](file:///c:/Users/hsin/Desktop/GenAI/HW/LLM%20Wiki%20Notes/slides/03-github-teamwork.html)。
- 包含 6 頁獨立 16:9 投影片：
  1. 封面（雲端城堡、章魚貓旗幟與彩色紙飛機航行）。
  2. Git 隨身畫具箱 vs GitHub 雲端藝廊雙雄對比。
  3. 出海起手式：六步遠航魔法（init → add → commit → branch -M → remote add → push -u）。
  4. 雲端收發室三大日常咒語（clone、pull、push）。
  5. 出海三大新手暗礁（空目錄、Token 密碼認證、master/main 分支名不同調）。
  6. 特別加映神隊友：GitHub Copilot 畫室小精靈與四大提效心法。
- 遵循日系繪本 Design System（和紙白底、3px 墨灰框線、Huninn 粉圓體、平塗無漸層、手繪 SVG）。

## [2026-11-17] Ingest | GitHub 是什麼？新手入門看這篇，GitHub Copilot 教學一次上手！
- 攝取來源：`raw/GitHub 是什麼？新手入門看這篇,GitHub Copilot 教學一次上手！.pdf`。
- 提煉核心繪本隱喻：
  - Git vs GitHub ＝ 畫家隨身畫具箱 vs 雲端世界萬國藝廊。
  - 遠端推送 ＝ 給作品貼上傳送符咒（origin），摺成紙飛機發射出海（push -u）。
  - GitHub Copilot ＝ 站在肩膀上的發光心靈感應小精靈（按 Tab 採納）。
- 新增與更新 Wiki 頁面：
  - `wiki/concepts/git-vs-github.md`
  - `wiki/workflows/first-push.md`
  - `wiki/concepts/github-copilot.md`
  - `wiki/commands/git-init.md`
  - `wiki/commands/git-add.md`
  - `wiki/commands/git-commit.md`
  - `wiki/commands/git-status.md`
  - `wiki/commands/git-log.md`
- 同步更新中央目錄 `wiki/index.md`。

## [2026-11-16] Init | 建立知識庫骨架與 AGENTS.md 規範
- 初始化 Karpathy LLM Wiki 結構：`raw/`、`wiki/`、`slides/`。
- 確立「日系繪本風」HTML 簡報設計規範（#FFFCF6、3px #3E3A39、四色平塗、Google Fonts Huninn、手繪 SVG）。
- 建立初始 `index.md` 與模組化四單元大綱。
- 產出示範性首發繪本簡報 `slides/01-git-basics-demo.html`。
