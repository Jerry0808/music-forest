# 音樂森林｜鋼琴老師用數位古典音樂繪本

## 如何執行

直接雙擊 `index.html`，用 Chrome、Edge、Safari 或 Firefox 開啟。不需要安裝套件、伺服器、帳號或網路。瀏覽器會等老師按下播放後才啟動聲音。

## 資料夾結構

```text
index.html
assets/
  classical-excerpts.js
  audio/README.md
```

- `index.html`：40 首曲目資料、老師介面、收藏、最近播放與三個課堂工具。
- `assets/classical-excerpts.js`：已驗證片段的 MIDI note events 與來源資料。所有音符都有 MIDI pitch、start、duration、velocity。
- `assets/audio/`：保留給未來已授權真人錄音；目前播放流程不依賴錄音檔。

## 目前音樂策略

古典片段不是憑記憶輸入，也不是「仿某作品」的生成旋律。流程是：

```text
公開領域／合法授權 MIDI、LilyPond 或樂譜
→ 解析 tempo map、note-on、note-off、velocity；只有無 MIDI 時才逐音核對樂譜
→ 依完整小節裁出代表樂句
→ 匯出 CLASSICAL_EXCERPTS
→ Web Audio 依 AudioContext.currentTime 排程演奏
```

只有來源、授權、作品、樂章與解析結果都存在時才設為 `verified: true`。其餘曲目顯示「音樂片段整理中」，不播放替代旋律。

目前 40 首皆已建立並通過資料驗證。主要來源是 Mutopia Project 的可追溯 MIDI，以及 PDMX `no-license-conflict` 子集中的 CC0／Public Domain Mark 樂譜資料；每首來源與授權可在曲目頁的「樂譜來源與驗證資料」展開查看。

《山魔王的宮殿》已改用 Mutopia 公開領域鋼琴縮編譜第 49–64 小節的完整主題重現，保留 MIDI 原有的音高、節奏、力度與速度推進，不再使用先前被截斷的低音開場。

《獅王進行曲》不再誤用只有 12 小節序奏的 MIDI。現版逐音轉錄 Paul M. Hanna 的 CC BY-SA 4.0 管樂版 Oboe 分譜第 13–20 小節，並用聖桑 Public Domain 親筆總譜核對主題與原調；網站資料中也保留兩個來源連結與雜湊值。

## 新增或更新片段

1. 取得可合法使用且能追溯版本的 MIDI；優先使用 Mutopia，必要時使用 PDMX `no-license-conflict` 子集或明確標示授權的 IMSLP／其他可信資料庫。
2. 解析來源的 tempo map、pitch、onset、duration 與 velocity，不可手猜音符。
3. 選擇自然結束的代表樂句，通常 15–30 秒。
4. 在 `assets/classical-excerpts.js` 加入一筆與 `MUSIC_LIBRARY.id` 相同的資料。
5. 確認來源、授權與片段統計後，才可設為 `verified: true`。

## 維護與驗證

在網址後加上 `?debug=1` 可顯示開發驗證面板，包含來源、授權、長度、BPM、音符數、最低／最高 MIDI pitch 與前 30 個 note events。一般老師介面不顯示此面板。

收藏、最近播放、音量與靜音只存於目前裝置的 `localStorage`，不會上傳。

## 版權提醒

古典作品進入 Public Domain，不代表現代錄音、編曲或校訂版也屬於 Public Domain。禁止擷取 Spotify、Apple Music、YouTube 或來源不明的錄音／MIDI。若來源授權要求姓名標示或相同方式分享，正式發布時也必須保留相應標示。
