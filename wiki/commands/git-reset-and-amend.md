---
title: "修正 Commit 歷史紀錄：amend、reset 與版本整理黃金法則"
tags: [git-history, git-reset, git-amend, troubleshooting, intermediate]
analogy: "時光倒流修補存檔點；未出門前的草稿可以修改，寄出的信件不能抽回"
module: "04-time-travel"
updated: 2026-11-17
---

# 修正 Commit 歷史紀錄：amend、reset 與版本整理黃金法則

在開發過程中，難免會遇到「剛 commit 完發現少放一個檔案」、「提交訊息寫錯字」、或「想把最後一個測試用的 commit 刪掉」的情境。Git 提供了強大的歷史修復工具，讓你在發布前能將版本歷史整理得乾淨專業。

---

## 概念圖解與比喻 (Visual Analogy)
> **自管版本的時光機，但不可修改公共歷史。**
> 在你自己的電腦上，每個 Commit 就像你日記本上的草稿，你可以撕掉重寫（`reset`）或補貼貼紙（`amend`）。但一旦這頁日記已經拍照傳到群組（Push 到遠端與團隊共享），就絕對不能撕掉竄改，否則其他人的歷史線會全部斷裂。

---

## 核心觀念 (Core Concept)

### 1. 版本控管的黃金法則 (Golden Rule)
- **原則**：在尚未 `push` 分享給他人之前，本地分支的提交可以任意修訂整理。
- **禁忌**：一旦分支已經推送到遠端且有其他人協作，**絕對不要修改這些已發布的歷史紀錄**！

### 2. 兩種核心修復情境
- **情境 A：微調最後一次 Commit（`git commit --amend`）**
  - 用途：訊息寫錯、漏放檔案。
  - 行為：將暫存區的檔案合併進最新的 Commit 中，並允許替換 Commit 訊息。這會生成一個具有新 Hash 的全新 Commit 取代舊節點。
- **情境 B：撤銷最近一次 Commit（`git reset`）**
  - **`git reset --soft HEAD^`（溫和模式）**：
    - 撤銷 Commit，但保留所有變更於「暫存區（Staging Area）」。
    - 適合：想要重新寫 Commit 訊息，或補進更多檔案後再重新打包。
  - **`git reset --hard HEAD^`（強硬模式）**：
    - 徹底捨棄最後一次 Commit，工作區與暫存區全部回退至前一版本。
    - 適合：確定最後一次改動全都是廢棄實驗，完全不想保留。
  - **`git reset --hard ORIG_HEAD`（後悔救援）**：
    - 若不小心 hard reset 錯了，Git 在執行危險操作前會把原本位置記錄在 `ORIG_HEAD`，可用此指令瞬間救回！

---

## 常用指令與操作 (Key Commands)

```bash
# 1. 補漏檔案並修改最後一次提交訊息
git add forgotten_file.txt
git commit --amend -m "feat: 補上遺漏的設定檔並修正標題"

# 2. 撤銷最後一次 Commit，但將檔案改動保留在暫存區
git reset --soft HEAD^

# 3. 徹底抹除最後一次 Commit（放棄所有變更）
git reset --hard "HEAD^"   # Windows cmd 下 ^ 為跳脫字元，需加引號

# 4. 救命！剛才 hard reset 刪錯了，復原到 reset 前的狀態
git reset --hard ORIG_HEAD

# 5. 檢視特定 Commit 物件的詳細內容
git show HEAD
```

---

## 常見誤解與排查 (Gotchas & Troubleshooting)
- **Windows 命令提示字元中的 `^` 符號**：
  - 在 Windows CMD 下，脫字號 `^` 是跳脫字元，如果直接輸入 `git reset --hard HEAD^` 會造成指令中斷或無效。**務必加上雙引號**：`"HEAD^"`。
- **Commit 並沒有真正被即時刪除**：
  - 被 reset 的 Commit 依然暫存在 `.git/objects/` 的物件庫中，不會立即被系統資源回收機制清掉。只要能找到該 Commit 的 Hash ID，隨時都能救回。
