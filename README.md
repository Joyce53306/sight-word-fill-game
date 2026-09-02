# Sight Word Sentence Builder 🔤

拖拉式 sight word 句子填空遊戲。孩子先聽句子語音，再從三個選項中把正確的字拖進空格，答對才能進下一題。

© Joyce53306

---

## 檔案結構

```
sight-word-fill-game/
├── index.html        # 遊戲本體（畫面、拖拉邏輯、語音）
├── questions.json     # 題庫（Middle Class / Big Class）
└── README.md
```

`index.html` 開啟後會用 `fetch('questions.json')` 讀題目，所以這**兩個檔案要放在同一層資料夾**，不能只上傳 index.html。

## 放上 GitHub Pages

1. 到 GitHub 開一個新的 repository（例如 `sight-word-fill-game`）
2. 把 `index.html`、`questions.json` 這兩個檔案上傳到 repo 的**根目錄**（不要放進子資料夾，除非你也跟著調整 Pages 設定）
3. 到 repo 的 **Settings → Pages**，Source 選 `main` branch、`/ (root)`，儲存
4. 等一兩分鐘，網址會是 `https://<你的帳號>.github.io/sight-word-fill-game/`

之後每次改 `questions.json`（加題、修題）直接在 GitHub 上編輯或重新上傳覆蓋，Pages 會自動更新，不用動 `index.html`。

## 題庫怎麼加新題目

打開 `questions.json`，格式是這樣：

```json
{
  "middle": [
    {
      "level": "middle",
      "before": "I am",
      "after": "great magician.",
      "answer": "a",
      "options": ["go", "a", "to"],
      "needsReview": false
    }
  ],
  "big": [ ... ]
}
```

- `before` / `after`：句子挖空前、後的文字（挖空處會自動插入）
- `answer`：正確答案（大小寫要跟句子裡實際需要的一致，例如句首要大寫）
- `options`：三個選項，**要包含 answer**，遊戲畫面會照這個陣列順序顯示
- `needsReview: true` 代表這題答案目前不在圈字作業字庫裡，是待確認狀態，可以自己改成 `false`（確認沒問題後）

新增題目：複製一個物件、改內容、貼到 `middle` 或 `big` 陣列裡就好，不用改 `index.html`。

## 目前題庫涵蓋範圍

- **Middle Class 中班**：22 句，選項只從中班圈字作業字庫（ML1–ML10）抽
- **Big Class 大班**：30 句，選項從中班 + 大班圈字作業字庫（ML1–10 + BL1–10）合併抽

## 待確認清單

以下答案目前不在圈字作業字庫裡（文法正確優先保留，字庫可自行決定要不要加這些變化形）：

- `needs`（She needs a pig. — 圈字作業字庫是 need）
- `grows`（Mom grows apples. — 圈字作業字庫是 grow）

## 整合進 Game Base

之後要跟你其他工具（Joyce's ABC Adventure）整合，可以：
1. 直接把整個 `sight-word-fill-game/` 資料夾放進你 game hub 的 repo 裡當一個子資料夾
2. 在你的 hub 首頁加一個連結卡片指到 `sight-word-fill-game/index.html`
3. 風格（Andika 字型、配色）跟你其他工具一致，不用額外調整

## 授權 / 浮水印

原始碼裡有隱藏簽名（HTML 註解、meta 標籤、DOM 隱藏文字、console log）標示 © Joyce53306，屬於防抄襲標記，不影響遊戲畫面或功能。
