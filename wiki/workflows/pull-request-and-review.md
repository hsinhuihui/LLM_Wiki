---
title: "GitHub 協作流程：Pull Request (PR) 開立、Code Review 與壓縮合併"
tags: [github, pull-request, code-review, workflow, teamwork]
analogy: "請求合併的正式提案書；同儕專家評審會；壓成單一乾淨包裹入庫"
module: "05-github-advanced"
updated: 2026-11-17
---

# GitHub 協作流程：Pull Request (PR) 開立、Code Review 與壓縮合併

在現代軟體工程與多人團隊中，任何開發者都不能直接將未經審核的代碼直接推送到主要主幹（`main`）。**Pull Request（簡稱 PR，在 GitLab 稱為 Merge Request）** 是確保代碼品質、落實同儕審查與知識共享的核心機制。

---

## 概念圖解與比喻 (Visual Analogy)
> **PR 是正式的「成果驗收與合併提案書」。**
> 你在自己的獨立工作線（Feature Branch）完成開發後，向專案維護者遞交一份提案書：「我完成了這個功能，請幫我檢查並批准合併入主幹」。在此介面中，團隊成員可以逐行留言審查，確保每一行進入主幹的代碼都具備高水準。

---

## 核心觀念 (Core Concept)

### 1. PR 的四大核心價值
- **視覺化討論區**：針對特定行數進行代碼討論、提出優化建議。
- **品質守門員**：結合 CI/CD 自動化測試（GitHub Actions），測試通過後方可准許合併。
- **追蹤與關聯**：可直接關聯專案 Issue（例如：`Closes #53`），合併時自動關閉該任務。

### 2. 開立 PR 的標準四步驟
1. **發起比對**：Push 分支至遠端後，點擊 GitHub 專案首頁黃色橫幅的 `Compare & pull request`。
2. **撰寫結構化資訊**：
   - **Title（標題）**：清楚表達目的（遵循語義化規範，例如 `feat: 新增會員登入與 Token 驗證機制`）。
   - **Description（描述）**：條列修改重點、影響範圍、測試方式與關聯的 Issue。
3. **指派審查者 (Reviewers)**：在右側欄位邀請資深工程師或同組協作者。
4. **送出 PR**：點擊綠色 `Create pull request` 進入審查階段。

### 3. Code Review（程式碼審查）的核心原則
- **對 Reviewer 而言**：
  - 關注可讀性、架構設計、安全邊界與團隊規範。
  - **保持建設性語氣**：提出替代方案（如「這裡使用 async/await 會不會讓異步邏輯更直觀？」），避免非建設性質疑。
- **對 Author 而言**：
  - 視審查為代碼精進的機會，理性討論並及時修正反饋。

### 4. 最佳合併策略：Squash and Merge（壓縮合併）
- **運作機制**：將功能分支上所有零散、微小的 Commit（如 `fix typo`, `test`, `wip`）壓縮為**單一個乾淨俐落的 Commit**，再合併至主分支。
- **核心優勢**：保持主幹（`main`）的 Commit History 極度整潔，方便日後進行版本追溯與上線比對。

---

## 常用指令與操作 (Key Commands)

```bash
# 1. 建立獨立功能分支
git checkout -b feature/login-auth

# 2. 開發並提交代碼
git add .
git commit -m "feat: 完成登入邏輯"

# 3. 推送至遠端儲存庫
git push -u origin feature/login-auth

# 4. 到 GitHub 網頁端開立 PR，進行 Code Review 與 CI 測試

# 5. 審查通過後，於網頁端點選「Squash and merge」完成主幹合併
```

---

## 簡報分鏡建議 (Slide Blueprint)
- **畫面焦點**：左側展示 Feature Branch 向 Main 發起 PR 的結構圖；中央展示 Code Review 對話註解氣泡；右側展示 Squash and Merge 將多節點壓縮為單節點的動畫流程。
- **配色建議**：水色代表功能分支、若竹綠代表審查通過與主分支、珊瑚粉代表 Review 留言標籤。
