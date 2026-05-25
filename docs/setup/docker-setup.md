# Docker 環境構築

## WSL の確認
```bash
wsl -l -v
```
以下のように表示されれば大丈夫です。
```
NAME      STATE           VERSION
Ubuntu    Running         2
```
※ VERSION が「2」になっていることが重要  
入っていなければ、  
[WSL のセットアップ](wsl-setup.md)  
を参照してください。  

## Docker Desktop のインストール
以下からダウンロード
https://www.docker.com/products/docker-desktop/  

インストール時に  
- 「Use WSL 2 instead of Hyper-V」にチェック  

## Docker Desktop の設定

Docker Desktop を起動し  
設定 → Resources → WSL Integration

- 「Enable integration with my default WSL distro」ON  
- 使用する Ubuntu を ON  

「Apply & Restart」を押します。 

※ Docker Desktop を開いてずっと loading 画面の場合は、PC を一度再起動して Docker Desktop を開き直すと直ることがあります。

## 動作確認 (WSL で)

```bash
docker --version
docker compose version
docker ps
```
エラーが出なければ大丈夫です。

Docker を使いたい場合は  
[Docker の使い方](docker-usage.md)  
を参照してください。
