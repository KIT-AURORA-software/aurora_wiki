# 環境構築

Aurora の開発を始めるために必要なセットアップ手順をまとめます。  
はじめて環境を作る場合は、上から順番に確認してください。

## セットアップ手順

1. [GitHub のセットアップ](github-setup.md)
2. [WSL のインストール](wsl-install.md)
3. [開発ツールの準備](dev-tools.md)
4. [リポジトリの取得](repository.md)
5. [動作確認](verification.md)

## 対象環境

| 項目 | 内容 |
| --- | --- |
| OS | Windows |
| 開発環境 | WSL |
| エディタ | VS Code |
| バージョン管理 | Git / GitHub |

## 全体の流れ

```text
GitHub アカウント準備
  ↓
Git / SSH 設定
  ↓
WSL インストール
  ↓
VS Code 連携
  ↓
Aurora リポジトリを clone
  ↓
ローカルで動作確認
```

## 困ったとき

セットアップ中にエラーが出た場合は、以下を確認してください。

- エラーメッセージをそのまま検索する
- 実行したコマンドを記録する
- OS、WSL、Git のバージョンを確認する
- 解決したら手順を Wiki に追記する

よくある問題は、今後 `troubleshooting.md` にまとめます。

