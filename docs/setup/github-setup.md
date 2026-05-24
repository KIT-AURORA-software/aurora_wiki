# GitHub のセットアップ

Aurora の開発で GitHub を使うための準備をまとめます。

## Git と GitHub について

### Git とは

Git は、ファイルの変更履歴を管理するためのツールです。  
いつ、誰が、どのファイルを変更したのかを記録できます。

### GitHub とは

GitHub は、Git で管理している内容をインターネット上で保存・共有できるサービスです。  
チームでコードやドキュメントを共有したり、レビューしたりするときに使います。

## やること

1. GitHub アカウントを作成する
2. Git をインストールする
3. Git のユーザー名とメールアドレスを設定する
4. SSH キーを作成する
5. GitHub に SSH キーを登録する
6. 接続確認を行う

## GitHub アカウントを作成する

[GitHub 公式サイト](https://github.com/) にアクセスして、アカウントを作成します。

登録時に必要なものは以下です。

- ユーザー名
- メールアドレス
- パスワード

登録後、メールアドレスの認証が必要な場合は、届いたメールから認証を完了してください。

## Git をインストールする

[Git for Windows 公式サイト](https://gitforwindows.org/) にアクセスします。

![Git for Windows のダウンロード画面](git_install.png)

`Download` ボタンを押して、インストーラーをダウンロードします。  
基本的には、インストーラーの初期設定のまま進めれば大丈夫です。

インストール後、コマンドプロンプトまたは PowerShell で以下を実行します。

```bash
git --version
```

Git のバージョンが表示されれば、インストールは成功です。

## Git のユーザー設定

Git でコミットしたときに表示される名前とメールアドレスを設定します。

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

設定できたか確認します。

```bash
git config --global user.name
git config --global user.email
```

## SSH キーを作成する

GitHub と安全に接続するために SSH キーを作成します。

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

途中で保存先やパスフレーズを聞かれます。  
よく分からない場合は、保存先は Enter で進めて問題ありません。

公開鍵の内容を表示します。

```bash
type %USERPROFILE%\.ssh\id_ed25519.pub
```

表示された内容をコピーして、GitHub に登録します。

## GitHub に SSH キーを登録する

GitHub の画面で以下の順に進みます。

1. 右上のアイコンをクリックする
2. `Settings` を開く
3. `SSH and GPG keys` を開く
4. `New SSH key` をクリックする
5. `Title` に分かりやすい名前を入力する
6. `Key` に公開鍵を貼り付ける
7. `Add SSH key` をクリックする

## 接続確認

以下のコマンドで、GitHub に接続できるか確認します。

```bash
ssh -T git@github.com
```

初回は接続してよいか確認されることがあります。  
`yes` と入力して進めてください。

成功すると、GitHub への接続確認メッセージが表示されます。

