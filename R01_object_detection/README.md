# 物体検出サンプルアプリケーション(YOLOv3)

## 概要

本アプリケーションはUSBカメラの画像から対象物を検出し、HDMI画面に出力するアプリケーションです。

## ビルドとデプロイ手順

1. クローンしたディレクトリを環境変数に設定する

    ```
    # "/path/to"はクローンしたディレクトリのパスに置き換えてください。
    export WORK=/path/to/kakip_ai_apps
    ```

2. ビルドディレクトリを作成する

    ```
    cd $WORK/R01_object_detection
    mkdir build && cd build
    ```

3. ビルドを行う

    ```
    cmake ../src
    make -j$(nproc)
    ```

4. 実行用ディレクトリに実行ファイルをコピーする

    ```
    cd $WORK/R01_object_detection/exe
    cp $WORK/R01_object_detection/build/object_detection .
    ```

5. TVMのコンパイル(最適化)済みファイル(deploy.so)を取得する

    ```
    wget https://github.com/Kakip-ai/kakip_ai_apps/releases/download/v1.0.0/R01_object_detection_deploy.so -O ./yolov3_onnx/deploy.so
    ```

    自身でAIモデルをコンパイル(最適化)する場合は、以下のRenesas社のリポジトリ、ドキュメントを確認してください。  
    - [Githubリポジトリ](https://github.com/renesas-rz/rzv_drp-ai_tvm)
    - [環境構築](https://github.com/renesas-rz/rzv_drp-ai_tvm/blob/v2.3.1/setup/SetupV2H.md#installation)
    - [コンパイル(最適化)のチュートリアル](https://github.com/renesas-rz/rzv_drp-ai_tvm/blob/v2.3.1/tutorials/tutorial_RZV2H.md)

## 実行手順

予めUSBカメラをkakipに接続し、以下のように実行してください。

```
cd $WORK/R01_object_detection/exe
./object_detection
```
