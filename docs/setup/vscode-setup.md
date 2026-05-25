# VS Code のインストール

Aurora の開発では、エディタとして Visual Studio Code を使います。  
ここでは Windows に VS Code をインストールし、WSL から開けるようにする手順をまとめます。

## VS Code をダウンロードする

[Visual Studio Code 公式サイト](https://code.visualstudio.com/) にアクセスします。

`Download for Windows` をクリックして、インストーラーをダウンロードします。

## VS Code をインストールする

ダウンロードしたインストーラーを実行します。

## WSL 拡張機能をインストールする

VS Code を起動し、左側の Extensions を開きます。

検索欄に `WSL` と入力し、Microsoft が提供している `WSL` 拡張機能をインストールします。

## WSL から VS Code を開く

Ubuntu などの WSL ターミナルを開き、作業したいディレクトリへ移動します。

例:

```bash
cd aurora_wiki
code .
```

VS Code が起動し、左下に `WSL: Ubuntu` のように表示されていれば成功です。

## `code` コマンドが使えない場合

通常は VS Code と WSL 拡張機能をインストールすると、WSL から `code .` を実行できます。

もし `code: command not found` のようなエラーが出る場合は、PATH を追加します。

まず WSL を開いて、Windows のユーザー名を確認します。

```bash
ls /mnt/c/Users
```

次に、以下を実行します。  
`<Windowsユーザー名>` は自分のユーザー名に置き換えてください。

```bash
echo 'export PATH="$PATH:/mnt/c/Users/<Windowsユーザー名>/AppData/Local/Programs/Microsoft VS Code/bin"' >> ~/.bashrc
source ~/.bashrc
```

確認します。

```bash
which code
code --version
```

これでエラーが出なければ、WSL 内で `code .` を使用できます。


## うまく開けない場合

`code .` で VS Code が開かない場合は、以下を確認してください。

- VS Code を一度再起動する
- WSL 拡張機能がインストールされているか確認する
- Windows 側で VS Code がインストールされているか確認する
- WSL ターミナルを開き直す
