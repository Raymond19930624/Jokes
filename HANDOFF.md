# Agent Handoff — 笑話收藏器

## 目前目標

持續從 PTT 笑話板（及其他台灣網路來源）收集**真實**笑話，每次「新增」或「更新」指令觸發一批 40 則，寫入 `index.html` 並 commit + push 到 GitHub。  
成功標準：網站 https://raymond19930624.github.io/Jokes/ 能顯示最新笑話，手機瀏覽正常。

---

## 已完成事項

- 建立單檔 Vanilla JS 網站 `index.html`（無其他依賴，GitHub Pages 部署）
- 笑話資料以 JS 陣列形式內嵌，格式：`{id:"xxx", src:"來源", cat:"類別", q:"問題", a:"答案"}`
- 已提交並 push 以下批次（共 900 則）：
  - t、u、v、w、x、y、a、e、f、j 等多批（各 40 則）
  - 以及多個早期來源批次（痞客邦、西施問路、寶貝問路等）
- 已用 ID 前綴：a, b, c, d, e, f, g, h, i, j, l, m, n, o, p, r, s, t, u, v, w, x, y, z
- **下一個可用前綴：k、q**（其他字母已用）
- 本 session 最後一批：j001–j040（commit `94f10c3`），已 push

---

## 目前狀態

- 工作區狀態：**乾淨**，與 `origin/main` 完全同步
- 主要變更：本 session 新增 j批（40 則）並 push，GitHub Pages 已更新
- 已完成驗證：使用者確認可在 https://raymond19930624.github.io/Jokes/ 瀏覽（曾遇到手機看不到新笑話 → 原因是未 push，push 後解決）
- 需補驗證：無
- 不建議重跑：無大型測試，單檔靜態站

---

## 遇到過的問題

- **手機看不到新笑話**：原因是本機 commit 後忘記 push。解法：`git push origin main`。提醒：每次 commit 後必須 push，GitHub Pages 才會更新。
- **404 PTT 文章**：PTT 部分文章已被刪除，fetch 時會 404。解法：從 index 頁面找有效標題再 fetch 內文。
- **AI 生成笑話事件**：曾有一批（q001-q060）被判定為 AI 生成而整批 revert（commit `cbc7741`）。這是最嚴重的錯誤，已建立嚴格規則。

---

## 待開發 / 待處理

- [ ] 下次使用者說「新增」→ 收集 40 則**真實** PTT 笑話，ID 前綴用 **k**（k001–k040）
- [ ] 插入位置：`j040` 之後、`// ── 網路精選 ──` 之前（約 line 1676）
- [ ] commit 訊息格式：`新增 40 則 PTT 精選笑話（k001-k040）`
- [ ] commit 後立即 push

---

## 不要重做 / 不要誤判

- **絕對禁止 AI 生成笑話**：每則笑話必須來自真實網路來源（PTT、痞客邦等），且可提供原始 URL 佐證
- **不要**在 commit 前忘記 push（用戶看不到更新）
- **不要**跳過 PTT index 頁面、直接猜 URL（很多文章已刪除）
- **不要**修改已存在的笑話資料（除非使用者明確要求修正）
- **不要**新增任何 JS 依賴或拆分成多個檔案（維持單檔架構）

---

## 重要檔案

- `D:\Codex\Jokes\index.html`：唯一主檔，所有笑話資料與 UI 邏輯都在這裡
  - 笑話陣列從約 line 400 開始到 line 1738 結束
  - 各批次以 `// ── X批：...` 注解分隔
  - **下一批插入點**：line ~1676（`j040` 之後，`// ── 網路精選 ──` 之前）

---

## PTT 爬取方法

```
# Index 頁面（從高頁碼往低爬）
https://www.ptt.cc/bbs/joke/index{N}.html   # 目前爬到約 index2130 附近

# 個別文章
https://www.ptt.cc/bbs/joke/M.{timestamp}.A.{hash}.html
```

篩選標準：
- ✅ 猜謎 / 耍冷 / 短梗
- ✅ 諧音梗、腦筋急轉彎、幹話集、短句梗、對話
- ❌ 政治敏感、成人、故事格式太長、punchline 不清楚

---

## 下一位 Agent 指令

```
請先閱讀專案根目錄的 HANDOFF.md（位於 D:\Codex\Jokes\HANDOFF.md），了解目前的開發狀態。

閱讀完畢後，請：
1. 用你自己的話整理你對目前進度的理解
2. 確認下一批笑話的 ID 前綴（應為 k）與插入位置
3. 提出你建議的下一步行動

【重要】在使用者明確說「新增」或給出指令前，請不要修改任何檔案、不要執行命令、不要開始爬取笑話。
```
