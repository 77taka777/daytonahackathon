# 会場図メーカー

イベント会場の座席・通路・ステージ配置を自動作成し、過去の人流CSVを使ってスタッフ配置案を計算する静的Webアプリです。

## 使い方

`index.html` をブラウザーで開いてください。ビルドやパッケージのインストールは不要です。

1. 会場名、幅・奥行き、参加者数、レイアウトを入力して「自動で会場図を作る」を押します。
2. スタッフ数と勤務時間を入力します。
3. 「人流CSVを読み込む」から、会場の過去イベントで記録したデータを読み込みます。
4. 結果を確認し、SVG保存または印刷からPDF保存します。

CSVの列は `timestamp,zone,count`（日時、エリア、人数）です。日本語列名も利用できます。複数日・15分間隔の記録を推奨します。取り込んだCSVはブラウザー内だけで処理され、外部サーバーへ送信されません。

## 人員配置の計算

CSV内で最も人流が多い連続勤務時間帯を選び、その時間帯のエリア別平均人数比を使って、入力スタッフ数をエリアに配分します。実データを読み込むまで配置人数は提案しません。これは過去実績から作る参考案です。必要最低人員、休憩、避難経路、安全要件の確認は会場の責任者が行ってください。

## データ出典と制約

- [国土交通省「人流データを活用した地域課題の解決」](https://www.mlit.go.jp/tochi_fudousan_kensetsugyo/chirikukannjoho/content/001709686.pdf) — イベントの過去人流を次回の警備・人員配置検討に活用する考え方を参照。
- [国土交通省「人流データ選定ガイド」](https://www.mlit.go.jp/tochi_fudousan_kensetsugyo/chirikukannjoho/content/001733098.pdf) — データの対象期間・対象規模が適合するか確認するための参考。
- [G空間情報センター 人流オープンデータ](https://front.geospatial.jp/data/2022/01/841/) — 地域レベルの参考データ。粗い地域メッシュを会場内の人流や人員配置に直接読み替えることはできません。

実際の配置には、対象会場で計測したエリア別のカウント・滞留データを使ってください。データが通行量か滞留人数かを確認し、意味の異なる指標を混在させないでください。

## GitHub Pagesで公開

GitHubにこのフォルダーの内容をリポジトリのルートとしてpushし、リポジトリの **Settings → Pages → Deploy from a branch** で `main` ブランチと `/ (root)` を選択します。公開URLはGitHub Pagesの設定画面に表示されます。

空のGitHubリポジトリを作成した後、ターミナルでこのフォルダーへ移動し、`<ユーザー名>/<リポジトリ名>` を置き換えて次を実行します。

```bash
git init
git add .
git commit -m "Create venue layout maker"
git branch -M main
git remote add origin https://github.com/<ユーザー名>/<リポジトリ名>.git
git push -u origin main
```

このアプリは静的ファイルだけで動きます。サーバー、APIキー、秘密情報は不要です。公開後も人流CSVは各閲覧者のブラウザー内でのみ処理されます。

## Daytonaの利用

このプロジェクトでは、Daytonaを開発用Sandboxおよびアプリの配置・プレビュー環境として使用しました。アプリ本体は `/home/daytona/index.html` に配置しています。Daytonaの認証情報や署名付きプレビューURLはリポジトリに含めません。GitHub Pages公開後はGitHub PagesのURLを共有してください。

## ファイル

- `index.html` — アプリ本体（HTML/CSS/JavaScriptを含む）
- `README.md` — 使い方、計算方法、出典、公開手順
- `.nojekyll` — GitHub Pagesで静的ファイルをそのまま配信
