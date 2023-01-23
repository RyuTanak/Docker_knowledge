# docker-compose  

複数のコンテナを連携させることができる。  
これはコマンド(docker run)でも可能であるが、コマンドが複雑になるためdocker-composeを使ってシンプルに行う。  

コマンドでwordpressをインストールする場合。  
まず、環境変数を設定しながらMySQLのインストールをする。  
```
docker run --name wordpress -e MYSQL_ROOT_PASSWORD=password -e MYSQL_DATABASE=wordpress -d mysql:5.6
```
wordpessコンテナを起動する。  
```
docker run -p 8080:80 -e WORDPRESS_DB_PASSWORD=password -d --name wordpress --link wordpressdb:mysql wordpress:4.7-php5.6
```

## docker-composeとは  

- 複数コンテナをまとめて管理  
- yamlファイルの設計図  
- コンテナの立ち上げを自動化  

## imageとbuild  

```yaml
version: "3"
service:
  web:
    build:./php
  db:
    image:mariadb: 10.4
```
image→DockerHubから指定  
build→Dockerfileのパスを指定  

## container_name  

コンテナに任意の名前をつける  
(docker --nameと同じ)  
```yaml
version: "3"
service:
  web:
    build:./php
    cintainer_name: "php8"
  db:
    image:mariadb: 10.4
    cintainer_name: "db2"
```

## volume  

コンテナとホストにディレクトリ共有  
ホストのパス:コンテナのパス  
(docker run -vと同じ)  
```yaml
version: "3"
service:
  web:
  db:
    volume:
    ./data:/var/lib/mysql
```

## port  

コンテナのポート開放とポートフォワーディング  
(docker rn -pと同じ)  
外部公開ポート：コンテナ内部ポート  
```yaml
version: "3"
service:
  web:
    image:php:8.0
    ports:
      "8080:80"
  db:
```

## コンテナ間通信の方法  

サービス名がIPアドレスに変換される  

## wordpressを立ち上げてみる  

gitのファイルをコピーしたら、docker-composeの実行  
```
docker-compose up -d
```

## docker-composeコマンドの紹介  

### docker-compose down  
docker-compose.ymlで管理されているコンテナをストップ&削除  
### restart  
docker-compose.ymlで管理されている全てのコンテナを再起動  
### ps  
docker-compose.ymlで管理されているコンテナ一覧を表示  
### run  
docker-compose.ymlで管理されているサービスを一つ指定してコマンドを実行  