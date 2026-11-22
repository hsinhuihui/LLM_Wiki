---
title: "第一次出海遠航：把本地作品推上 GitHub 雲端倉庫"
tags: [github, remote, workflow, beginner]
metaphor: "給作品貼上雲端城堡的郵寄地址，搭乘紙飛機發射出海！"
module: "03-github-teamwork"
updated: 2026-11-17
---

# 第一次出海遠航：把本地作品推上 GitHub 雲端倉庫

當你在自己的電腦（本地）畫好了作品，也拍好了一張張拍立得照片（commit），下一步就是把作品「發射」到 GitHub 雲端藝廊！

---

## 🎨 繪本隱喻 (Visual Metaphor)

1. **`git remote add origin <url>` ＝ 貼上通往雲端島嶼的傳送符咒 🏷️**
   - 你的畫室在陸地上，GitHub 是漂浮在天上的島嶼。
   - `origin` 是你給那座雲端島嶼取的「親切暱稱」。這行咒語的意思是：「**記住這串長長的地標網址，以後我都叫你 origin 囉！**」
2. **`git push -u origin main` ＝ 第一次搭乘紙飛機出海遠航 ✈️**
   - 你把主要故事線（`main` 分支）上的所有畫作放進紙飛機。
   - `-u`（Upstream）就像幫紙飛機裝上自動導航雷達：告訴它「**以後只要我喊 `git push`，你就自動飛往這座島嶼的 main 展廳，不用我再報路了！**」
3. **`git pull origin main` ＝ 從雲端收發室簽收最新畫卷 📦**
   - 當夥伴在雲端更新了畫作，你派出一隻鴿子把最新內容叼回你的草稿桌。

---

## 💡 核心觀念 (Core Concept)

- **遠端（Remote）的意義**：
  - 專案不能只存在單一電腦，硬碟損壞或換電腦時會欲哭無淚。
  - 將專案備份至雲端，同時開啟多人協作的橋樑。
- **標準 6 步出海起手式**：
  1. 在本機專案資料夾喚醒 Git（`git init`）。
  2. 挑選檔案放上拍照台（`git add .`）。
  3. 拍下第一張紀念照片（`git commit -m "初始化專案"`）。
  4. 統一主流線名稱為 `main`（`git branch -M main`）。
  5. 綁定 GitHub 儲存庫網址（`git remote add origin <網址>`）。
  6. 點火發射到雲端（`git push -u origin main`）。

---

## ⚡ 常用指令與咒語 (Key Commands)

```bash
# 【新手專案首次上傳 GitHub 完整咒語】

# 1. 喚醒畫室記錄精靈
git init

# 2. 把所有畫稿請上展示台
git add .

# 3. 按下快門拍照封存
git commit -m "feat: 初次初始化專案"

# 4. 把主故事線名稱統一名為 main（符合現代 GitHub 規範）
git branch -M main

# 5. 綁定 GitHub 雲端倉庫地址（origin）
git remote add origin https://github.com/你的帳號/你的儲存庫名稱.git

# 6. 裝上自動導航雷達，第一次推送至雲端
git push -u origin main
```

```bash
# 【日常遠端互動常用咒語】

# 下載雲端上的整個公開/私有展覽館到本機
git clone https://github.com/作者/專案.git

# 抓取雲端最新修改並與本地合併
git pull origin main

# 將本機新的 commit 推上雲端
git push
```

---

## 🛟 新手容易踩的雷 (Gotchas & Traps)

> [!WARNING]
> **雷點 1：專案資料夾裡「完全沒有任何檔案」就執行 push**
> Git 只能追蹤檔案，無法追蹤空空如也的資料夾！請務必先在目錄下建立至少一個檔案（例如 `README.md` 或程式碼檔案），才能成功 `git add` 與 `commit` 喔！

> [!CAUTION]
> **雷點 2：帳號密碼登入被拒絕（Support for password authentication was removed）**
> GitHub 現已不允許直接在終端機輸入純文字密碼。你需要到 GitHub 的 `Settings` → `Developer Settings` → `Personal Access Tokens` 申請一把「金鑰匙（Token）」當作密碼貼入，或者設定 SSH Key。

> [!NOTE]
> **雷點 3：本地分支叫 `master`，GitHub 雲端叫 `main`**
> 過去 Git 預設主分支為 `master`，而 GitHub 現已全面改為 `main`。這就是為什麼要在 push 前執行 `git branch -M main`，避免在雲端長出兩條不同名字的孤兒分支！

---

## 🎬 簡報分鏡建議 (Slide Blueprint)

- **畫面構圖**：橫向 4 步驟大導覽圖。
  - 步驟 1（和紙白底）：本地小熊將畫稿放進紙箱（`git init` + `add` + `commit`）。
  - 步驟 2（山吹黃 `#F6D27A`）：小兔子用羽毛筆在行李牌上寫下 `origin` 地址（`remote add origin`）。
  - 步驟 3（水色 `#A8D3E6`）：摺好一架巨大紙飛機，發射航向彩雲（`git push -u origin main`）。
  - 步驟 4（若竹綠 `#B9DAA5`）：雲端島嶼上的章魚貓揮旗迎接，相片順利入庫！
- **色彩重點**：
  - 傳送門與遠端箭頭一律使用水色 `#A8D3E6`。
  - 3px 墨灰框線，重要終端機指令以膠囊卡片呈現。
