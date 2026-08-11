# GitHubの使い方
CLI(Command Line Interface)でのGitHubの使い方を説明します。

## 1. GitHubの基本的な作業の流れ

GitHubを使用した開発は、基本的に次の流れで行う。

```text
ファイルを編集
    ↓
変更内容を確認
    ↓
ステージング
    ↓
コミット
    ↓
GitHubへプッシュ
```

---
## 2.最初の設定

1. まずSSH鍵があるか確認する。
```bash
ls ~/.ssh
```

2. 鍵がなければ作成する
```bash
ssh-keygan -t ed25519 -C "自分のGihtubメールアドレス"
```
基本はEnter連打でも大丈夫です。

3. 公開鍵を表示する。
```bash
cat ~/.ssh/id_ed25519.pub
```
表示された
```
ssh-ed25519 AAAA.....
```
をコピーする。
4. GitHubで効果鍵を登録する。
GitHubの
```
Settings
→ SSH and GPG keys
→ New SSH key
```
から、先ほどコピーした公開鍵を登録する
5. SSH接続を確認する。
```bash
ssh -T git@github.com
```
初回は、
```
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```
と出るので、
```
yes
```
と入力する。

成功すると、だいたい
```
Hi ユーザー名! You've successfully ...
```
と表示される。

## 3.各班のレポジトリをクローンする
1.ワーキングスペースを作成する。
```bash
mkdir -p ~/ワーキングスペース名/src
cd ~/ワーキングスペース名/src
```
GitHub上にある各班のレポジトリを取得する。<br>
レポジトリはsrcの下にクローンする
SSHの場合次のようにする。
```bash
git clone git@github.com:ユーザー名/レポジトリ名/git
```
クローン後、作成されたフォルダへ移動する。

```bash
cd レポジトリ名
```

※HTTPSクローンの場合は次のようにする。<br>
```bash
git clone https://github.com/ユーザー名/レポジトリ名.git
```
---

## 4.新しいレポジトリを作成する方法
### 4.1 GitHub側でレポジトリを作成する

Github上で次の操作を行う。

1. GitHubにログインする
2. 「New repository」を選択する
3. レポジトリ名を入力する
4. Privateを選択する
5. 「Creeate repository」を選択する。


### 4.2 既存のフォルダをGit管理する
1. プロジェクトのフォルダへ移動する。

```bash
cd プロジェクト名
```
2. Gitレポジトリとして初期化する。
```bash
git init
```
3. ファイルをステージングする
```bash
git add .
```
4. 最初のコミットを作成する。
```bash
git commit -m "Initial commit"
```
5. ブランチ名を`main`に変更する。
```bash
git branch -M main 
```
6. GitHubのレポジトリを登録する。
```bash
git remote add origin https://guthub.com/ユーザー名/レポジトリ名.git
```
7. Githubへ送信する。
```bash
git push origin main
```

## 5.GitHubに上げたレポジトリを修正するとき
1. GitHub上の最新変更を取得する。
```bash
git pull 
```
2. ファイルを追加・修正した後、追加・修正したファイルをステージングする。
```bash
git add 追加・修正したファイルの相対パス
```
3. コミットする。
```bash
git commit -m "例）修正しました"
```
※コミット文は何を変更したかを分かるような内容にしましょう。<br>
4. GitHubへプッシュする
```bash
git push origin main 
```

## 6. ブランチの使い方
ブランチは、メインのコードに影響を与えずに別の作業を進めるための機能のこと。自分の環境を作りたいときにおすすめ

1. レポジトリのフォルダに移動
```bash
cd レポジトリフォルダ
```
2. ブランチを作成
```bash
git switch -c ブランチ名
```
上ができなかったらこっち
```bash
git checkout -b ブランチ名
```
3. 現在のブランチを確認する。
```bash
git branch
```
4. *が打たれているとことが現在のブランチ<br>
ブランチの切り替え
```bash
git switch ブランチ名
```
5. 作成したブランチをGitHubへ送る。
```bash
git push -u origin 作成したブランチ名
```

## 7. 編集方法
1. 自分のPCをgithubに上がっている最新情報に直す
```bash
git pull
```
2. 編集したフォルダやファイルを追加する
```bash
git add .
```
基本的には上のコードで良いが、特定のファイルだけを上げたいときはそのファイルの相対パスをかく
```bash
git add ファイルの相対パス
```
3. githubに何処を編集したのかというコミットを打つ
```bash
git commit -m "編集内容"
```
4. pushを行う
```bash
git push origin main
```
5. Webのgithubに移動して自分が上げたファイルが入っているか確認する。