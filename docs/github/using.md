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

## 2.人が上げたレポジトリを使用したいとき
すでにGitHub上にあるレポジトリを取得する場合は`clone`を使用する。

HTTPSの場合は次のようにする。
```bash
git clone https://github.com/ユーザー名/レポジトリ名.git
```
SSHの場合は次のようにする。
```bash
git clone git@github.com:ユーザー名/レポジトリ名/git
```
クローン後、作成されたフォルダへ移動する。

```bash
cd レポジトリ名
```
---

## 3.新しいレポジトリを作成する方法
### 3.1 GitHub側でレポジトリを作成する

Github上で次の操作を行う。

1. GitHubにログインする
2. 「New repository」を選択する
3. レポジトリ名を入力する
4. Privateを選択する
5. 「Creeate repository」を選択する。


### 3.2 既存のフォルダをGit管理する
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

## 4.GitHubに上げたレポジトリを修正するとき
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

## 5. ブランチの使い方
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
