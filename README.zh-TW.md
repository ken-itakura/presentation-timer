# 自我介紹計時器

[English](README.md) | [日本語](README.ja.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md) | [हिन्दी](README.hi.md) | [Español](README.es.md) | [Français](README.fr.md) | [العربية](README.ar.md) | [বাংলা](README.bn.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Bahasa Indonesia](README.id.md) | [Deutsch](README.de.md) | [한국어](README.ko.md) | [Türkçe](README.tr.md) | [Tiếng Việt](README.vi.md)

用於同學會等場合、讓參加者依序自我介紹的單頁計時器。只要在瀏覽器中開啟 `index.html` 即可使用，無需安裝、伺服器或網路連線。

## 使用方式

1. 在瀏覽器（Safari / Chrome）中開啟 `index.html`。
2. 在設定畫面：匯入 CSV（參見 `sample/participants.csv`，或按「載入範例」）、逐人切換出席／缺席、依任一欄位排序、設定標題 / 每人時間 / 稱謂 / 語言，並試聽音效。
3. 按「進入計時」（同時啟用聲音）。
4. 進行計時：

| 操作 | 效果 |
|---|---|
| `Space` / 開始按鈕 | 開始下一位發言（伴隨掌聲） |
| 點選右側清單中的名字 | 從該人開始；排在其前面的人移入「已跳過」 |
| 點選「已跳過」中的名字 | 開始該人的發言 |
| 取消「已跳過」中的「出席」勾選 | 確認後設為缺席並從清單移除（計時不會停止） |

剩 10 秒：每秒一聲滴答 · 剩 3 秒：急促的嗶嗶聲 · 0 秒：爆炸聲並顯示「時間到」標籤。右上角顯示總用時，右側列出接下來的 10 位。

## CSV 格式

第一列為標題列。自動辨識 UTF-8 / Shift_JIS 編碼。姓名與稱謂欄位會依標題（如 `姓名`、`稱謂`）自動選擇，也可在設定中變更。稱謂儲存格為空時使用預設稱謂。

```csv
name,honorific,group,year
Alex Morgan,,A,2001
Sam Rivera,Dr.,B,2001
```

## 多語言

支援 16 種語言：在設定畫面透過「語言」切換（首次使用瀏覽器語言，所選語言會被儲存）。介面文字、標題預設值、預設稱謂、範例資料與稱謂位置（姓名前／後）會隨語言改變；阿拉伯文使用由右至左的版面。翻譯尚未經母語人士審閱，可編輯 `index.html` 中的 `I18N` 來修正。新增語言時，請在 `LANGS`、`I18N`、`SAMPLE_NAMES` 各加入一項。

## 行動裝置

支援手機直向與橫向版面。iPhone 開啟靜音開關時不會發出聲音。透過「檔案」App 開啟檔案最為可靠；使用 GitHub Pages 發布後只需開啟網址即可。

## 結構

```
.
├── index.html            # app (HTML / CSS / JavaScript in one file)
├── sample/
│   └── participants.csv  # sample list
├── README.md             # + README.<lang>.md (16 languages)
```

`index.html` 包含全部內容：多語言詞典、CSV 解析、設定畫面、以 Web Audio 合成音效（無需音訊檔）、計時邏輯（以時間戳計算，不易漂移）與計時畫面。設定與進度會自動儲存到 `localStorage`。

授權：未指定
