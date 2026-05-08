# WSL のインストール

Windows 上で Aurora の開発環境を作るために、WSL をインストールします。

## WSL をインストールする

PowerShell を管理者として開き、以下を実行します。

```powershell
wsl --install
```

インストール後、PC を再起動してください。

## Ubuntu を起動する

再起動後、スタートメニューから Ubuntu を起動します。  
初回起動時にユーザー名とパスワードを設定します。

## パッケージを更新する

```bash
sudo apt update
sudo apt upgrade
```

## 確認する

```bash
wsl --version
```

バージョン情報が表示されれば、WSL の準備は完了です。

