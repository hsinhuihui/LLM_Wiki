---
title: "團隊分支工作流比較：Git Flow vs GitHub Flow vs GitLab Flow"
tags: [git-flow, github-flow, gitlab-flow, workflow, teamwork, architecture]
analogy: "交通路網的分流規範；大型鐵路調度 vs 敏捷高鐵專線 vs 上游優先水利網絡"
module: "05-github-advanced"
updated: 2026-11-17
---

# 團隊分支工作流比較：Git Flow vs GitHub Flow vs GitLab Flow

當開發團隊人數增加時，如果每個人對分支的用途與合併規則缺乏共識，儲存庫很快就會陷入混亂。業界針對不同發布週期與專案規模，衍生出了三種主流工作流程（Workflows）。

---

## 概念圖解與比喻 (Visual Analogy)
> **分支工作流就是團隊的「交通規則指南」。**
> 都是功能驅動開發（Feature-driven development），以需求為起點建立分支，開發完畢合併並銷毀。差異在於：
> - **Git Flow**：嚴謹的多軌大型客運鐵路（有專屬試車軌、發布軌與維修軌）。
> - **GitHub Flow**：極簡直達高鐵（只有主線與功能線，依賴自動化測試隨時發布）。
> - **GitLab Flow**：上游優先的梯級水利系統（代碼永遠由開發環境向下游生產環境單向流動）。

---

## 核心觀念 (Core Concept)

### 1. 三種工作流程對比矩陣

| 維度 | Git Flow | GitHub Flow | GitLab Flow |
| :--- | :--- | :--- | :--- |
| **提出時間/背景** | 最早提出（Vincent Driessen, 2010） | 由 GitHub 提出，專為簡化 Git Flow | 結合前兩者優點，由 GitLab 提出 |
| **分支架構** | 複雜（5 種分支）：<br>`master`, `develop`, `feature`, `release`, `hotfix` | 極簡（2 種分支）：<br>`master/main`, 敘述性 `feature` 分支 | 實用彈性：<br>`master` + `production` (或 `pre-production`, release 分支) |
| **核心原則** | 嚴格分工與排程發布 | **主分支隨時具備可部署狀態** | **上游優先（Upstream First）** |
| **協作核心** | 頻繁切換與多重合併（需合回 develop 與 master） | 依賴 **Pull Request** 與管理員審查 | 依賴 **Merge Request** 與 CI/CD 環境對應 |
| **適用場景** | 有固定發行週期、版本號（如 1.0, 2.0）的傳統軟體或大型專案 | 現代 Web 應用、SaaS、持續部署（CD/CI）、快速敏捷迭代 | 具備多重伺服器環境（Dev/Staging/Prod）或需長期維護舊版本的企業應用 |

---

### 2. 詳細工作流剖析

#### A. Git Flow
- **`master`**：穩定上線版，只從別的分支合併，具備版本標籤（Tag）。
- **`develop`**：主要開發基礎線，所有新功能分支（`feature`）由此切出並併回。
- **`release`**：準備上線前的凍結測試分支，修復的小問題需同時併回 `master` 與 `develop`。
- **`hotfix`**：線上緊急修補，直接由 `master` 切出，修完同時合回 `master` 與 `develop`。
- **痛點**：流程繁瑣、分支切換成本高，且容易漏掉雙重合併（漏合 develop）。

#### B. GitHub Flow
- **核心哲學**：只要 `master`（或 `main`）通過測試，就是隨時可部署上線的狀態。
- **標準 6 步驟**：
  1. 從 `main` 建立具描述性的分支（如 `user-login-oauth`）。
  2. 在本地提交修改（Commits）。
  3. 開啟 Pull Request 發起團隊討論與 Code Review。
  4. 部署至測試環境進行驗證。
  5. 審查通過，管理者執行合併（Merge）。
  6. 立即部署至生產環境，並刪除該 feature 分支。

#### C. GitLab Flow（上游優先原則）
- **核心精神**：代碼永遠由「最上游的 `master`」向下游的「環境分支」單向流動。
- **Bug 修復原則**：當生產環境（`production`）出現 Bug，**禁止直接在下游環境修補**！必須在最上游的 `master` 建立修復分支，驗證合併至 `master` 後，再依序往下流部署至 `pre-production` 與 `production`，徹底根絕「線上修好、下次改版又重現」的幽靈 Bug。

---

## 常用指令與操作 (Key Commands)

```bash
# 【GitHub Flow 實戰日常】

# 1. 切出具描述性的功能分支
git checkout -b feat/checkout-api

# 2. 開發、提交並推送
git add .
git commit -m "feat: 新增結帳試算 API"
git push -u origin feat/checkout-api

# 3. 於 GitHub 建立 PR -> 同儕審核 -> 通過後於網頁合併

# 4. 本地切回主幹並同步最新進度
git checkout main
git pull origin main

# 5. 刪除已完成合併的本地功能分支
git branch -d feat/checkout-api
```

---

## 簡報分鏡建議 (Slide Blueprint)
- **畫面焦點**：三欄對比圖表，上方呈現各自的節點拓撲圖（Git Flow 樹狀交錯網、GitHub Flow 簡約單主幹、GitLab Flow 梯級瀑布向下流）。
- **配色建議**：山吹黃代表開發、水色代表測試/預發、若竹綠代表生產/正式上線。
