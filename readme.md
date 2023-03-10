# Dockerについて  

簡単に  
コンテナ - サーバ上のパッケージ化された箱  
Docker - Linuxサーバ上で作ったり、動かしたりとコンテナを管理するツール  

コンテナ技術  
- Docker　(一番人気)  
- Linux Containers  
- Hyper-Vコンテナ  
- Windows コンテナ  


## Dockerと仮想環境の違い  

||Docker|仮想環境|
|--|--|--|
|存在場所|メモリ上|ディスク上|
|ゲストOS|なし|ホストOSとゲストOSに分かれる|
|データ管理|一時的|常に保存|
|コード化|Dockerfileで可能|不可能|


## DockerfileとDockerイメージ  

コンテナ作成は大きく三段階ある  
Dockerfile→Dockerイメージ→Dockerコンテナ  
DockerfileからDockerイメージを作成することをbuild(ビルド)  
Dockerイメージ空Dockerコンテナを作成することをrun(ラン)  

DockerイメージはDocker Hubからダウンロードする方法もある。  


## Docker toolboxのインストール  

以下のURLのから「DockerToolbox-19.03.1.exe」をダウンロードする  
https://github.com/docker-archive/toolbox/releases  

※インストールで詰まったので、クラウド版のDockerを使ううことにする。  

## 各勉強  

[Docker基本コマンド](https://github.com/RyuTanak/Docker_knowledge/blob/master/command.md)  
[Dockerコンテナのストレージ](https://github.com/RyuTanak/Docker_knowledge/blob/master/storage_progrem.md)  
[Dockerfile](https://github.com/RyuTanak/Docker_knowledge/blob/master/dockerfile.md)  

[テキスト（github）](https://github.com/uchidayuma/udemy-docker)  

## DockerでElastic Stackを動かしてみる  

今回は、Filebeat、Elasticsearch、KibanaをDockerで連携しつつ動かしてみる。  

[filebeatのダウンロード](https://github.com/RyuTanak/Docker_knowledge/blob/master/filebeat.md)  



