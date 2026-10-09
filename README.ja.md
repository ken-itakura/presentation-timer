# 自己紹介タイマー

[English](README.md) | [日本語](README.ja.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md) | [हिन्दी](README.hi.md) | [Español](README.es.md) | [Français](README.fr.md) | [العربية](README.ar.md) | [বাংলা](README.bn.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Bahasa Indonesia](README.id.md) | [Deutsch](README.de.md) | [한국어](README.ko.md) | [Türkçe](README.tr.md) | [Tiếng Việt](README.vi.md)

同窓会などで、参加者に順番に自己紹介してもらうときに使う、1ページ完結のタイマーアプリです。`index.html` をブラウザで開くだけで動きます（インストール・サーバー・ネット接続は不要）。

## 使い方

1. `index.html` をブラウザ（Safari / Chrome）で開く。
2. 準備画面で、CSVを読み込む（`sample/participants.csv` または「サンプルを読み込む」）、各人の出欠を切り替える、好きなフィールドで並べ替える、タイトル・発表時間・敬称・言語を設定する、音を試す。
3. 「本番画面へ」を押す（このとき音声も有効になります）。
4. タイマーを進める：

| 操作 | 動作 |
|---|---|
| `Space` / スタートボタン | 次の方の発表を開始（拍手SE） |
| 右端のリストの名前をクリック | その人から開始。手前の人は「スキップされた人」へ移動 |
| スキップされた人の名前をクリック | その人の発表を開始 |
| スキップされた人の「出席」チェックを外す | 確認後、欠席扱いでリストから削除（タイマーは止まりません） |

残り10秒：1秒ごとにチック音 · 残り3秒：ピピピピ連続音 · 0秒：爆発音と「時間切れです」ラベル。右上に全体の経過時間、右端に次の10人を表示します。

## CSVの形式

1行目はヘッダー行です。文字コードは UTF-8 / Shift_JIS を自動判別します。名前・敬称の列は見出し（`名前` / `氏名` / `敬称` など）から自動で選ばれ、設定で変更できます。敬称のセルが空の人には、標準の敬称を使います。

```csv
name,honorific,group,year
Alex Morgan,,A,2001
Sam Rivera,Dr.,B,2001
```

## 多言語対応

16言語に対応しています。準備画面の「言語」で切り替えます（初回はブラウザの言語設定、選んだ言語は保存されます）。画面の文言、タイトルの初期値、標準の敬称、サンプルデータ、敬称の位置（名前の前／後）が言語に合わせて変わり、アラビア語は右から左のレイアウトになります。翻訳はネイティブの確認を受けていません。修正は `index.html` 内の `I18N` を編集してください。言語を追加するには、`LANGS`・`I18N`・`SAMPLE_NAMES` に1言語ぶん足します。

## モバイル

縦向き・横向きに対応したレイアウトです。iPhone では消音スイッチがONだと音が鳴りません。ファイルは「ファイル」アプリ経由で開くのが確実です。GitHub Pages で公開すれば URL を開くだけで使えます。

## 構成

```
.
├── index.html            # app (HTML / CSS / JavaScript in one file)
├── sample/
│   └── participants.csv  # sample list
├── README.md             # + README.<lang>.md (16 languages)
```

`index.html` にすべてが入っています：多言語の辞書、CSVパーサー、準備画面、Web Audio による効果音の合成（音声ファイル不要）、タイマー処理（時刻ベースでズレにくい）、本番画面。設定と進行状況は `localStorage` に自動保存されます。

ライセンス：未設定
