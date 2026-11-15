---
status: ready-for-github
phase: "静的アプリ初版"
next: "新規GitHubリポジトリへ登録し、GitHub Pagesを設定する"
waiting_on: null
updated: 2026-11-15
---

# 会場図メーカー — 仕様と現在地

## 背景

会場レイアウト自動作成に、過去の人流CSVを根拠とした人員配置シミュレーションを加える。

## ゴール

ブラウザーだけで動作し、GitHub Pagesで公開できる静的アプリ。

## 仕様

- 幅・奥行き・人数・形式からSVGの会場図を作成する。
- 会場実績CSVを読み込み、ピーク勤務帯とエリア別スタッフ配分を表示する。
- HTML/CSS/JavaScriptは `index.html` にまとめる。
- データ出典・計算方法・データ制約を画面とREADMEに記載する。

## 現在地

- 完了: アプリ実装、ローカルブラウザーでのCSV取込・配置計算確認、Sandbox `/home/daytona/index.html` への配置。
- 未着手: GitHubリポジトリ作成とpush、GitHub Pages公開。
- 既知の問題: 共有可能なDaytona期限付きプレビューURLは未発行。

## 次のアクション

1. GitHubに空のリポジトリを作成し、このフォルダーをpushする。
2. Settings → Pagesで `main` / `/ (root)` を選択する。
3. 公開URLで画面とCSV取込を確認する。

## 未決事項

- GitHubのリポジトリ名と公開範囲。
