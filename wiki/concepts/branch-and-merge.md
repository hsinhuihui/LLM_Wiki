---
title: "Git 分支機制與合併原理：Fast-forward 與三方合併"
tags: [git-branch, git-merge, beginner, core-concept]
analogy: "平行獨立工作線；指標向前滑動 vs 追溯共同祖先建立新存檔點"
module: "02-branch-merge"
updated: 2026-11-17
---

# Git 分支機制與合併原理：Fast-forward 與三方合併

分支（Branch）是 Git 最強大也最輕量的核心特色。不同於其他版控系統需要「複製整份專案資料夾」，Git 的分支僅僅是一個**指向特定 Commit 的可移動指標（40 字元的 SHA-1 參照）**。

---

## 概念圖解與比喻 (Visual Analogy)
> **分支不是複製目錄，而是貼上可移動的便利貼書籤。**
> 當你在主幹（`master` / `main`）工作時，書籤指向當前最新提交；當需要開發新功能（如 `iss53`）或緊急修復（`hotfix`）時，只需在當前節點貼上新書籤。你可以在不同書籤之間瞬間切換，而不會干擾彼此的檔案。

---

## 核心觀念 (Core Concept)

### 1. 建立與切換分支
- **傳統指令**：`git branch <name>`（建立）+ `git checkout <name>`（切換）。
- **現代推薦**：`git checkout -b <name>` 或 `git switch -c <name>`（建立並同時切換）。
- **工作區狀態注意**：切換分支前，工作區或暫存區最好保持乾淨（所有變更已 commit 或 stash），否則 Git 會因潛在衝突阻止切換。

### 2. 兩種合併機制 (Merge Strategies)
- **快進合併 (Fast-forward Merge)**：
  - **條件**：目標分支（如 `hotfix`）所指向的 Commit，能夠直接線性追溯回目前分支（如 `master`）。
  - **行為**：兩者之間沒有分岔，Git 不需要做額外的合併計算，僅僅是將分支指標直接「向前推進」到最新節點。
- **三方合併 (Three-way Merge)**：
  - **條件**：兩個分支的歷史已經分岔（例如 `master` 在分岔後有了新的 commit，而 `iss53` 也有自己的 commit）。
  - **行為**：Git 會自動找出兩個分支的「共同祖先（Common Ancestor）」，結合兩端分支最新快照進行三方對比，並自動產生一個擁有**兩個親代（Two Parents）**的全新提交，稱為「合併提交（Merge Commit）」。

---

## 常用指令與操作 (Key Commands)

```bash
# 建立並同時切換到新分支
git checkout -b iss53

# 切換回主分支
git checkout master

# 合併特定分支到當前所在分支
git merge hotfix    # 若為線性歷史，觸發 Fast-forward

# 刪除已完成合併的獨立分支
git branch -d hotfix

# 查看所有本地分支與當前所在位置
git branch -v
```

---

## 常見誤解與排查 (Gotchas & Troubleshooting)
- **誤解：分支刪除會遺失歷史紀錄？**
  - 分支本質只是個指針。只要該分支已經合併進主幹，刪除分支（`git branch -d`）只是撕掉便利貼標籤，所有提交歷史與代碼快照依然完整保留在 Git 歷史樹中。
- **切換分支報錯（Your local changes would be overwritten by checkout）**：
  - 表示本地工作區有未提交的檔案與目標分支衝突。請先執行 `git commit` 或 `git stash` 暫存，再行切換。

---

## 簡報分鏡建議 (Slide Blueprint)
- **畫面焦點**：左側展示線性 Fast-forward 指針滑動；右側展示分岔後的 Common Ancestor（C2）與三方合併新節點（C6）。
- **配色建議**：山吹黃代表主分支 master、若竹綠代表 feature 分支、珊瑚粉代表 Merge Commit。
