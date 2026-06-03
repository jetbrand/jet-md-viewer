# MD Previewer

ブラウザだけで動く、単一 HTML ファイルの Markdown プレビューアです。サーバーやビルドは不要で、`md-previewer.html` を開くだけで使えます。

## 特徴

- **インストール不要** — 1 ファイル完結（依存は Mermaid の CDN のみ）
- **ドラッグ＆ドロップ** — `.md` / `.markdown` / `.txt` をドロップまたは選択
- **複数ファイル** — タブで切り替え、プレビュー中にもファイルを追加可能
- **3 つの表示モード** — ソース / 分割 / プレビュー
- **Mermaid 対応** — **```mermaid** と書いたフェンスコードブロックを図として描画
- **ダークモード** — OS の `prefers-color-scheme` に追従

## オンラインで使う

GitHub Pages で公開しています。

**https://jetbrand.github.io/jet-md-viewer/**

## 使い方

1. 上記 URL を開くか、ローカルでは `index.html`（または `md-previewer.html`）をブラウザで開く
2. Markdown ファイルをドロップするか、画面をクリックして選択する
3. ヘッダーのタブで表示モードを切り替える

```bash
# macOS の例
open index.html
```

複数ファイルを一度に開くこともできます。プレビュー画面にファイルをドロップすると、タブが追加されます。

## 対応している Markdown（目安）

独自の軽量パーサーで、よく使う記法を中心に変換します。

| 記法 | 例 |
|------|-----|
| 見出し | `#` 〜 `######` |
| 強調 | `**太字**`、`*斜体*`、`~~取り消し~~` |
| リスト | `-` / `*` / `+`、番号付き `1.` |
| 引用 | `> 引用` |
| コード | インライン `foo`、行頭の ``` でブロック |
| リンク・画像 | `[text](url)`、`![alt](url)` |
| 表 | GitHub 風の `` | col | `` 形式 |
| 水平線 | `---` など |
| 図 | **```mermaid** フェンスブロック |

CommonMark や GFM の全機能には対応していません。複雑な拡張記法が必要な場合は、専用の Markdown ビューアの利用を検討してください。

## ファイル構成

```
jet-md-viewer/
├── index.html          # GitHub Pages 用（md-previewer.html と同一）
├── md-previewer.html   # アプリ本体
└── README.md
```

## 技術メモ

- Markdown → HTML は `md-previewer.html` 内の `parseMarkdown()` で処理
- Mermaid は [jsDelivr の `@mermaid-js/tiny`](https://cdn.jsdelivr.net/npm/@mermaid-js/tiny@11/) を読み込み（初回の図描画時にネットワークが必要）
- ファイル内容はブラウザ内の `FileReader` で読み込み、外部へ送信しません

## ライセンス

リポジトリにライセンスファイルがない場合は、利用・改変前にリポジトリオーナーに確認してください。
