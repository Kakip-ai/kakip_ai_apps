# kakip_ai_apps

Kakip用のAIアプリケーションのサンプルです。

## 共通手順

アプリケーションのビルドを行う前に以下を実行してください。

1. 必要なパッケージをインストールする

    ```
    sudo apt update
    sudo apt install -y build-essential cmake wget git
    ```

2. リポジトリをクローンする

    ```
    git clone https://github.com/Kakip-ai/kakip_ai_apps --recursive
    ```

3. rzv_drp-ai_tvmの設定を行う

    ```
    cd kakip_ai_apps
    cp 3rdparty/rzv_drp-ai_tvm/setup/include/* 3rdparty/rzv_drp-ai_tvm/tvm/include/tvm/runtime/
    ```

## アプリケーションのビルドと実行手順

アプリケーションのビルド及び実行手順については、アプリケーションディレクトリのREADME.mdを参照してください。

- [R01_object_detection](./R01_object_detection/README.md)