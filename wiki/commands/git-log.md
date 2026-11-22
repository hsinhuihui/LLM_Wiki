---
title: "git log — 翻閱時光相簿的歷史足跡"
tags: [git-command, beginner]
metaphor: "在暖爐前泡一杯熱茶，一頁頁翻看相簿裡的舊照片"
module: "01-git-basics"
updated: 2026-11-17
---

# `git log` — 翻閱時光相簿的歷史足跡

`git log` 讓你回顧過往所有的存檔紀錄，查看每張照片是誰拍的、何時拍的、以及留下了什麼話。

---

## 🎨 繪本隱喻 (Visual Metaphor)
> 冬天的森林裡，你坐在劈啪作響的暖爐旁，捧著綠色精裝相簿。手指滑過一張張貼著金色標籤的拍立得照片，看著這座城堡從當初的一塊磚頭，一步步長成如今雄偉的模樣。

---

## 💡 核心觀念 (Core Concept)
- 依時間倒序顯示每一次 commit。
- 顯示 7~40 碼的 SHA-1 Hash 身份識別碼、作者名稱與時間。
- 按鍵盤 `q` 可以優雅地離開閱讀模式回到終端機提示字元。

---

## ⚡ 常用指令與咒語 (Key Commands)

```bash
# 查看完整相簿紀錄
git log

# 單行簡潔模式（像目錄清單一樣乾淨）
git log --oneline

# 畫出漂亮的分支樹狀圖
git log --oneline --graph --decorate --all
```
