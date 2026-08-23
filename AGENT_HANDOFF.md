# AGENT_HANDOFF — 笑話收藏器

> 封存日期：2026-07-19  
> 狀態：**封存完成，可安全刪除本機，隨時從 GitHub 還原**

---

## 專案狀態

| 項目 | 說明 |
|------|------|
| 功能完整度 | ✅ 完成，無待開發功能 |
| GitHub 同步 | ✅ 本機與 `origin/main` 完全同步 |
| 線上網站 | ✅ https://raymond19930624.github.io/Jokes/ 正常運作 |
| 未解問題 | 無 |

---

## 技術棧

- **單檔靜態網站**：`index.html`（HTML + CSS + 內嵌 JS，無任何外部依賴）
- **字體**：Google Fonts Noto Sans TC（CDN，需連網）
- **部署**：GitHub Pages（`main` branch，push 後約 1–2 分鐘生效）
- **版本控制**：Git / GitHub（https://github.com/Raymond19930624/Jokes）

---

## 從全新 clone 還原步驟

```bash
git clone https://github.com/Raymond19930624/Jokes
cd Jokes
# 直接用瀏覽器開啟 index.html 預覽本機版
# 或直接瀏覽 https://raymond19930624.github.io/Jokes/
```

**無需安裝任何依賴、無需 Node.js、無需 build。**

---

## 環境變數與 Secret

無任何環境變數或 secret。  
GitHub Pages 部署為公開倉庫，無需任何 token 設定。

---

## 重要檔案

| 檔案 | 說明 |
|------|------|
| `index.html` | 唯一主檔（267 KB），所有笑話資料與 UI 都在這裡 |
| `README.md` | 專案說明，含 Agent Bootstrap 指令 |
| `HANDOFF.md` | 開發交接摘要（本 session 產出） |
| `AGENT_HANDOFF.md` | 本檔，長期封存交接文件 |

### index.html 內部結構

- **笑話資料陣列**：約 line 400–1738，共約 900 則
- **各批次分隔**：`// ── X批：...` 注解
- **下一批插入點**：`j040` 之後，`// ── 網路精選 ──` 之前（約 line 1676）
- **UI 邏輯**：line 1739 之後

---

## 笑話 ID 前綴使用狀況

| 已用 | 下一個可用 |
|------|-----------|
| a b c d e f g h i j l m n o p r s t u v w x y z | **k**（k001–k040）|

---

## 新增笑話標準作業流程

1. 從 PTT 笑話板 index 頁面（`https://www.ptt.cc/bbs/joke/index{N}.html`）由高往低爬
2. 找標題吸引人的「猜謎」「耍冷」類文章，fetch 內文確認 Q&A
3. 篩選：諧音梗 / 腦筋急轉彎 / 幹話集 / 短句梗
4. 排除：政治敏感、成人、過長故事、punchline 不清楚
5. 收集滿 40 則，寫入 `index.html` 指定插入點
6. commit：`新增 40 則 PTT 精選笑話（k001-k040）`
7. **立即 push**（不 push 則 GitHub Pages 不更新）

> ⚠️ **鐵則：禁止 AI 生成笑話。** 每則必須來自真實 PTT 或台灣網路來源。
> ⚠️ **禁止重複或近似笑話。** 新增前必須比對既有題目與答案；`index.html` 的 `CURATED_JOKES` 會排除重複題目、完全相同內容及已知近似版本。每則新增內容都要保留可開啟的原始 URL。

---

## 驗證狀態

| 驗證項目 | 結果 | 方式 |
|----------|------|------|
| GitHub Pages 正常 | ✅ | 使用者手機瀏覽確認 |
| 本機與遠端同步 | ✅ | `git status` clean，`git push` 完成 |
| 笑話資料格式 | ✅ | 所有 id 格式符合 `[a-z]\d{3}` |
| 建置流程 | N/A | 靜態單檔，無需建置 |
| 自動化測試 | N/A | 無測試框架 |

---

## 已知風險與限制

- PTT 舊文章可能 404（已刪除），爬取時需從 index 頁面確認有效 URL
- Google Fonts CDN 離線時字體 fallback 為系統字（UI 仍可用）
- 沒有分頁功能，所有笑話資料都在單一 HTML 檔案（目前 267 KB，仍在合理範圍）

---

## 延後項目（使用者未來可選擇處理）

- 無強制待辦，以下為可選優化：
  - 笑話去重檢查（目前靠人工判斷）
  - 搜尋功能
  - 讀取進度記憶（目前每次開啟重新隨機）

---

## 未來 Agent 接手指令

```
你即將接手一個已封存的靜態笑話網站。請先閱讀：
1. AGENT_HANDOFF.md（本檔）
2. README.md
3. git log --oneline -10

閱讀完畢後：
- 用自己的話說明你對目前專案狀態的理解
- 確認下一批笑話的 ID 前綴（應為 k，k001–k040）
- 說明插入位置與 commit/push 流程

在使用者明確下達指令前，不要修改任何檔案，不要執行任何指令。
```
