# Docker の使い方

[Docker のセットアップ](docker-setup.md)  


## GitHub 認証
[GitHub のセットアップ](github-setup.md)  
を参照してください。  

## レポジトリのクローン

KIT-AURORA-software の repositories の

```
aurora_ws
```

から HTTPS をコピーして、ホームディレクトリで以下を実行します。

```bash
git clone <レポジトリのhttps>
ls
```  

で

```bash
aurora_ws
```

があればクローン成功です。

## VS Code でコンテナを起動する場合
事前準備  
VS Code の拡張機能 `Dev Containers` をインストールしておきます。  



```bash
cd aurora_ws
code .
```

VS Code で

```
Ctrl + Shift + P
```

を押し、検索欄で

```
Dev Containers: Reopen in Container 
```

を選択します。  

コンテナが起動できたら、VS Code のターミナルのプロンプトが

```
/workspace
```

になっていることを確認できれば完了です。

## ターミナルでコンテナを起動する場合
```bash
cd ~/aurora_ws/.devcontainer
docker compose up -d --build
```
でコンテナを起動します。
```bash
docker ps
```
起動していれば、例えばこう表示されます。
```
NAMES
コンテナ名
```
  
コンテナに入る：
```bash
docker exec -it <コンテナ名> bash
```
コンテナから抜ける :
```bash 
exit
```
コンテナを止める :
```bash
docker stop <コンテナ名> 
```

## VS Code でコンテナを作り直す場合
VS Code でコンテナを作り直す場合は
```
Ctrl + Shift + P
```
を押して、検索欄で以下を選びます。
```text
Dev Containers: Rebuild and Reopen in Container
```

## ターミナルでコンテナを作り直す場合

```bash
cd ~/aurora_ws/.devcontainer
docker compose down
docker compose up -d --build
```

## Docker 内にカメラを渡す
事前準備  
WSL で`/dev/video0` と `/dev/video1`が見えるようにしてください。  
できていない人は  
[WSL のセットアップ](wsl-setup.md)  
の`WSL 内でカメラを使用したいとき`を参照してください。  

`.devcontainer/docker-compose.yml` を VS Code で開きます。 

対象サービスの中に追加します。
```yaml
devices:
  - /dev/video0:/dev/video0
  - /dev/video1:/dev/video1
```  

すでに `devices:` がある場合は、その中に追加します。

```yaml
services:
  ros2-dev:
    devices:
      # - /dev/dri:/dev/dri
      - /dev/video0:/dev/video0
      - /dev/video1:/dev/video1
```

コンテナを作り直します。  

Docker を作り直したら、コンテナ内のターミナルで
```bash
ls /dev/video*
```
ここで
```
/dev/video0  /dev/video1
```
が出れば、Docker 内でカメラ認識完了です。
