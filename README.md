# Poetry の環境構築

## 1. install

公式ドキュメントを参照
[https://python-poetry.org/docs/#installing-with-the-official-installer](https://python-poetry.org/docs/#installing-with-the-official-installer)

Linux, macOS, WSL
※必ず、`\home`ディレクトリで行う。

```shell
curl -sSL https://install.python-poetry.org | python3 -
```

Windows (Powershell)

```shell
(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -
```

## 2. 環境変数を通す

Linux
※poetry から指示されるコマンドを打てばよい
以下は、前回成功した時のコマンド

```shell
sudo export PATH="/home/linuxbrew/.local/bin:$PATH"
```

Windows
poetry から吐き出されたパスをユーザー環境変数の Path に通す

## 3. 環境構築が正常にできたかの確認

```shell
poetry --version
```

## poetry の基本コマンド

### poetry project の生成

```shell
poetry new project名
```

### 既存の project を poetry 環境にする

※option は、省略可能

```shell
poetry init --name "package名" --description "パッケージの説明" --author "作者" --python "pythonのversion"
```

### `petry.lock` から package を install

※pyproject.toml に記載されたすべてのパッケージの依存関係を解決し、インストールが行われる。
※また、インストールされる依存パッケージは最新バージョンのものが入る。

```shell
poetry install
```

### package の install

```shell
poetry add package名
```

### package の uninstall

```shell
poetry remove package名
```

### package の一覧表示

```shell
poetry show
```

### package のアップデート

```shell
poetry update
```

### `requirements.txt`の生成

```shell
poetry export -f requirements.txt --output requirements.txt --without-hashes
```

## poetry の仮想環境

### 仮想環境外からのコマンド実行

```shell
poetry run [実行したいコマンド]
```

### 仮想環境に入る

```shell
poetry shell
```

### 仮想環境から出る

```shell
exit
```

## タスクランナーのインストール

参考資料
[https://poethepoet.natn.io/](https://poethepoet.natn.io/)

```shell
poetry add poethepoet
```

### pyproject.toml の中に、以下を記載

```toml
[tool.poe.tasks]
タスクランナー名 = "タスクの内容"
```

### 実行

```shell
poetry run poe タスクランナー名
```
