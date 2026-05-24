# WSL のセットアップ

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

## WSL 内でカメラを使用したいとき

この手順は、USB カメラを WSL に渡したい場合の手順です。  
PC 内蔵カメラや一部のカメラは、WSL から認識できない場合があります。

まず、Windows でカメラが認識されているかを確認します。

```powershell
Get-PnpDevice -Class Camera
```

最終的に

```text
OK  Camera <カメラの種類>
```

のような結果が出れば、Windows 内ではカメラが認識されています。

次に、PowerShell で `usbipd` が入っているか確認します。

```powershell
usbipd --version
```

バージョンが表示されなければ、管理者 PowerShell でインストールします。

```powershell
winget install --interactive --exact dorssel.usbipd-win
```

インストール後、PowerShell を開き直します。

PowerShell で接続できるデバイス一覧を表示します。

```powershell
usbipd list
```

一覧の中から、使用したいカメラデバイスの `BUSID` を探します。

使用したいカメラデバイスの `BUSID` を指定して、管理者 PowerShell で以下を実行します。

```powershell
usbipd bind --busid <カメラデバイスのBUSID>
```

その後、PowerShell で WSL に接続します。

```powershell
usbipd attach --wsl --busid <カメラデバイスのBUSID>
```

成功すると、`usbipd list` で `Attached` のような状態になります。

```powershell
usbipd list
```

WSL に戻り、カメラが認識されているか確認します。

```bash
ls /dev/video*
```

このとき、

```text
/dev/video0
/dev/video1
```

のような表示が出れば成功です。
