# Lyon-env　version:1.1a

東京工科大学CS学部人工知能サーバーLyonにJupyterLabを利用したディープラーニングの学習環境を構築するDocker-Composeファイルとその他システムファイルになります。
イメージ自体はNvidia-Dockerが動作する環境であれば、Linuxでも動作いたします。

[Lyon公式ページ](https://sites.google.com/edu.teu.ac.jp/cscloud)

# Requirement

* GPUサーバー環境（SSH接続でのログインを想定）
* Dockerシステムの環境構築済みであること
* DockerCompose環境

[LyonにDockerを設定する｜ LyonクラウドVMの操作](https://sites.google.com/edu.teu.ac.jp/cscloud#h.89lswy9teuzt)

[LyonにDockerComposeをインストールする｜準備（はじめに）](https://power-banana-14a.notion.site/Lyon-JupyerLab-20230428-c4e3134fe8174bf3b6310cdd286d3a2b)


# Installation

GitHubからシステムを取得する
```bash
git clone https://github.com/Amenbo1219/Lyon-env.git
```
Lyon-Envのディレクトリに移動する
```bash
cd Lyon-env
```
Docker-compose をビルドする
```bash
docker compose build
```
ビルドしたイメージを起動する
```bash
docker compose up -d
```
ブラウザから http://接続したホスト名:9999 にログインする

# Note

* Pythonの他ライブラリを追加したい

     [py3/requirements.txt](py3/requirements.txt)に追加したいモジュールを追加する。
* イメージを変更・修正したい

     [py3/Dockerfile](py3/Dockerfile)に追加したいモジュールを追加する。

* ポート番号の変更・GPUメモリの割当量を変更したい

     [docker-compose.yml](docker-compose.yml)を変更する。
* JupyterのTokenを確認したい

     イメージビルド中にLogを確認し、LogからTokenを探す
    ```bash
    docker compose logs
    ```
* Jupyterにパスワードを設定したい

    　　コンテナが起動しているものとする。

    ```bash
    docker compose up -d
    ```
    コンテナにパスワードを設定する
    ```bash
    $ docker-compose exec py3 bash
    --- 以下、コンテナの中
    # jupyter notebook password
    # exit
    --- コンテナを再起動
    $ docker-compose down
    $ docker-compose up -d
    ```
* おすすめのイメージは？

    この辺のイメージがおすすめです

    * [Tensorflow系を使う場合|DockerHub](https://hub.docker.com/r/tensorflow/tensorflow/tags)

    * [Pytorch系を使う場合|DockerHub](https://hub.docker.com/r/pytorch/pytorch/tags)

    * [Cudaを使う場合|DockerHub](https://hub.docker.com/r/nvidia/cuda/tags)

    * [LyonにDockerComposeをインストールする｜特定環境を使う場合](https://sites.google.com/edu.teu.ac.jp/cscloud#h.d6y8bo3ee6h1)

* Tensorflowのイメージには何が含まれていますか？

     [テスト済みのビルド構成|Tensorflow](https://www.tensorflow.org/install/source?hl=ja#gpu)

# ReleaseNote
## 2023-05-22　Version1.0-release
* ファストコミット。
## 2023-05-22　Version1.0a-release
* デフォルトの共用メモリの容量を変更しました
## 2023-05-22　Version1.0b-release
* README.mdを更新しました。
 環境構築手法・参考文献・作成者情報を添付しました。
## 2023-06-24　Version1.1-release
* Compose上の共用メモリの記載に一部誤りがありましたので修正しました。
* DEMOスクリプトにCycleＧanのスクリプトを追加しました。
## 2023-06-24　Version1.1a-release
* README.mdを更新しました。
* Version情報を追記しました。

# Author

作成情報を列挙する

* 作成者：Amembo1219
* 所属：Faculty of Computer Science, Tokyo University of Technology 
* E-mail c0b20140d0@edu.teu.ac.jp

