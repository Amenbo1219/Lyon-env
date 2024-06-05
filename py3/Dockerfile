FROM python:3.8.18-slim-bullseye

RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

# パッケージの追加とタイムゾーンの設定
# 必要に応じてインストールするパッケージを追加してください
RUN apt-get update && apt-get install -y \
    tzdata \
    git \
    curl \
&&  apt-get clean \
&&  rm -rf /var/lib/apt/lists/*
# JupyterLab関連のパッケージ（いくつかの拡張機能を含む）
# 必要に応じて、JupyterLabの拡張機能などを追加してください
# 研究室用追加パッケージ
RUN pip install --no-cache-dir \
    pip install praat-parselmouth

#　追加パッケージのインストール
COPY requirements.txt /install/requirements.txt
RUN pip3 install --upgrade pip
RUN pip3 install -r /install/requirements.txt
