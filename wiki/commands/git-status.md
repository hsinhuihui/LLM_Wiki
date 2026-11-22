---
title: "git status — 翻開目前的畫室狀態清單"
tags: [git-command, beginner]
metaphor: "店長戴上老花眼鏡，拿著小板夾清點畫桌與展示台"
module: "01-git-basics"
updated: 2026-11-17
---

# `git status` — 翻開目前的畫室狀態清單

在不知道該做什麼的時候，輸入 `git status` 是最安心的選擇。它會清楚告訴你目前的畫室現況。

---

## 🎨 繪本隱喻 (Visual Metaphor)
> 小貓店長一手拿著小板夾、一手推了推鼻樑上的老花眼鏡：「來看看～紅色的字代表還在畫桌上亂跑的小搗蛋（未暫存）；綠色的字代表已經乖乖排在展示台上等拍照的好寶寶（已暫存）！」

---

## 💡 核心觀念 (Core Concept)
- **紅色檔案（Changes not staged for commit / Untracked files）**：在工作區修改或新建立，但還沒執行 `git add`。
- **綠色檔案（Changes to be committed）**：已經執行過 `git add`，正等待按下 `git commit`。
- **乾淨狀態（nothing to commit, working tree clean）**：代表畫桌與展示台都空空如也，全部內容都已妥善存進相簿！

---

## ⚡ 常用指令與咒語 (Key Commands)

```bash
# 檢查畫室狀態（最詳盡版）
git status

# 簡潔短版狀態（方便快速查看）
git status -s
```
