# PyQtのセットアップ

## 1. ワークスペースの作成
```bash
mkdir science_gui
cd science_gui
```

## 2. 仮想環境の作成
```bash
python3 -m venv .venv
```

## 3. 仮想環境の有効化
```bash
source .venv/bin/activate
```

## 4. ライブラリのインストール
```bash
python -V
```
python 3.5以上ならOK
```bash
python -m pip install --upgrade pip
pip install PyQt5
```

## 5. xcb関係ライブラリのインストール
```bash
sudo apt update

sudo apt install -y \
    libxcb-xinerama0 \
    libxcb-cursor0 \
    libxkbcommon-x11-0 \
    libxcb-icccm4 \
    libxcb-image0 \
    libxcb-keysyms1 \
    libxcb-render-util0 \
    libxcb-shape0

```

## 6. VSCodeに行ってコードの作成をしてください
