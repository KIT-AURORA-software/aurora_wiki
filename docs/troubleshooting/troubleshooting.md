# エラー集

Aurora の開発中に発生したエラーと、その対応方法をまとめます。  
同じ問題で迷わないように、原因と解決手順を残していきます。

## 書き方

エラーを追加するときは、以下の形で書いてください。

```md
## エラー名または症状

### 症状

どのタイミングで、どのようなエラーが出たかを書く。

### 原因

分かっている範囲で原因を書く。

### 対応

解決に使ったコマンドや手順を書く。

### 補足

関連リンクや注意点があれば書く。
```

## 公開前の注意

エラー文を貼る前に、以下の情報が含まれていないか確認してください。

- パスワード
- API キー
- GitHub token
- SSH 秘密鍵
- 個人のメールアドレス
- 学内・内部向けの URL
- ローカルPCのユーザー名
- 公開していないサーバー名や IP アドレス

必要な場合は、以下のように置き換えてから記録します。

```text
C:\Users\your-name\project
https://example.internal.local
192.168.xxx.xxx
```

## MkDocs

### `mkdocs` コマンドが見つからない

### 症状

```text
mkdocs: command not found
```

または

```text
'mkdocs' is not recognized as an internal or external command
```

### 原因

MkDocs がインストールされていない、または PATH が通っていない可能性があります。

### 対応

MkDocs をインストールします。

```bash
pip install mkdocs mkdocs-material
```

インストール後、バージョンを確認します。

```bash
mkdocs --version
```

## Git

### `git` コマンドが見つからない

### 症状

```text
git: command not found
```

または

```text
'git' is not recognized as an internal or external command
```

### 原因

Git がインストールされていない、または PATH が通っていない可能性があります。

### 対応

[Git for Windows](https://gitforwindows.org/) から Git をインストールします。  
インストール後、以下のコマンドで確認します。

```bash
git --version
```

### `Permission denied (publickey)` が出る

### 症状

```text
Permission denied (publickey).
```

### 原因

GitHub に SSH キーが登録されていない、または違う SSH キーを使っている可能性があります。

### 対応

SSH 接続を確認します。

```bash
ssh -T git@github.com
```

SSH キーの作成と登録は、[GitHub のセットアップ](../setup/github-setup.md) を確認してください。

## WSL

### `wsl` コマンドが見つからない

### 症状

```text
wsl: command not found
```

または、PowerShell で WSL が起動できない。

### 原因

WSL がインストールされていない可能性があります。

### 対応

PowerShell を管理者として開き、以下を実行します。

```powershell
wsl --install
```

詳しくは [WSL のセットアップ](../setup/wsl-setup.md) を確認してください。
