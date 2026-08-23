# 🧊 笑話收藏器

單頁手機網站，收錄 PTT 笑話板真實笑話，支援滑動翻頁、分類篩選、書籤收藏。

**線上版本：** https://raymond19930624.github.io/Jokes/

---

## Agent Bootstrap

You are taking over this project after a long pause. Do not modify files yet.

1. Read `README.md`, `AGENT_HANDOFF.md`, and the latest git log.
2. Report: project purpose, current status, setup steps, important files, known risks.
3. Wait for the user's next request before changing any code.

---

## 快速說明

| 項目 | 說明 |
|------|------|
| 架構 | 單檔 `index.html`，無框架、無建置步驟 |
| 部署 | GitHub Pages（push to `main` 即自動更新，約 1–2 分鐘生效）|
| 笑話數 | 約 900 則（持續增加）|
| 來源 | PTT 笑話板、痞客邦等台灣網路來源（**禁止 AI 生成；每則新增內容須保留原始 URL，且不得與既有笑話重複或太近似**）|

## 本機開發

```bash
git clone https://github.com/Raymond19930624/Jokes
# 直接用瀏覽器開啟 index.html 即可預覽
```

無需安裝任何依賴。

## 新增笑話

每次觸發「新增」指令，agent 從 PTT 爬取 40 則真實笑話，格式：

```js
{ id:"k001", src:"PTT笑話版", cat:"諧音梗", q:"問題", a:"答案" },
```

**ID 前綴目前進度：** 已用 a b c d e f g h i j l m n o p r s t u v w x y z，**下一個用 k**

詳細交接說明見 `AGENT_HANDOFF.md`。
