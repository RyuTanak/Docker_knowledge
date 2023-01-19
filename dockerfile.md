# dockerfileとは  

Dockerイメージをコード化したもの  
Docker buildコマンドを実行すると、テキストファイルからDockerイメージを作成  

簡単な例  
```
FROM nginx:1.16
RUN apt install -y
COPY source /var/www/html
EXPOSE 8080
```
詳しくは後程  

## Dockerfileのベストプラクティス  

https://docs.docker.jp/engine/articles/dockerfile_best-practice.html  

![image](./image/16.png)  
→エフェメラルは状態を持たないという意味  
 コンテナにボリュームを持たせないようにホストと共有させたこととか  


## Dockerfileの主要コマンド  

### RUNとCND  

どちらもLinuxコマンドを実行する命令  
実行タイミングが異なる。  

RUN:Dockerfile→イメージ  
CMD:イメージ→コンテナ  

```
RUN apt-get install -y nginx
CMD ["nginx","-g","daemon off;"]
```

以下のDockerfileを実行する。  
```
FROM ubuntu:20.04
RUN apt-get update -y && \
    apt-get install -y nginx
CMD ["nginx", "-g", "daemon off;"] 
```

```
FROM ubuntu:20.04
```
→ベースのOSがubuntuを指定。  

```
RUN apt-get update -y && \
```
→パッケージのアップデート  
 「&& \」はレイヤーを1つにまとめる  

```
    apt-get install -y nginx
```
→nginxのインストール  
ここまでがビルド時に実行されるもの  

```
CMD ["nginx", "-g", "daemon off;"] 
```
→nginxの起動コマンド  

buildコマンドを使ってイメージを作成する。  
```
docker build -t dockerfile-run-nginx /workspaces/Docker_knowledge/run/
```
-tオプションはイメージの名前をつけるもの  
最後にDockerfileがあるディレクトリを指定  

実行すると、イメージが作成される。  
![image](./image/17.png)  

このイメージからコンテナを作成してみる  
```
docker run -d -p 8081:80 --name dockerfile-run-nginx docker-run-nginx
```
コンテナが作成され、起動していることが分かる  
![image](./image/18.png)  


## 
