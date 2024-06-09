FROM tensorflow/tensorflow:2.12.0-gpu 

RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

# パッケージの追加とタイムゾーンの設定
# 必要に応じてインストールするパッケージを追加してください
RUN apt-get update && apt-get install -y \ 
    tzdata \
    git \ 
    wget \
    libglib2.0-0 \
    libsm6  \ 
    libxrender1  \ 
    libxext6 \
    libgl1-mesa-dev \
&&  apt-get clean \
&&  rm -rf /var/lib/apt/lists/*
# JupyterLab関連のパッケージ（いくつかの拡張機能を含む）
# 必要に応じて、JupyterLabの拡張機能などを追加してください

RUN pip install torch==2.3.0 torchvision==0.18.0 torchaudio==2.3.0 --index-url https://download.pytorch.org/whl/cu118

# 研究室用追加パッケージ
RUN pip install --no-cache-dir \
    pip install praat-parselmouth

#　追加パッケージのインストール
COPY requirements.txt /install/requirements.txt
RUN pip3 install --upgrade pip
RUN pip3 install -r /install/requirements.txt

RUN export TF_CPP_MIN_LOG_LEVEL=2
