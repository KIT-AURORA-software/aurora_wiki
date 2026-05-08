# GitHub のセットアップ

Aurora の開発で GitHub を使うための準備をまとめます。

## やること

1. GitHub アカウントを作成する
2. Git をインストールする
3. Git のユーザー名とメールアドレスを設定する
4. SSH キーを作成する
5. GitHub に SSH キーを登録する
6. 接続確認を行う

## Git のユーザー設定

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

## SSH キーの作成

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

## 接続確認

```bash
ssh -T git@github.com
```

成功すると、GitHub への接続確認メッセージが表示されます。

