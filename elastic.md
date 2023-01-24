# ElasticsearchやKibanaで連携してみる  

以下のdocker-composeを使う。  
```
version: "3"
services:
  elasticsearch:
    image: docker.elastic.co/elasticsearch/elasticsearch:7.17.8
    container_name: "es-container"
    environment:
      - "discovery.type=single-node"
      - "ES_JAVA_OPTS=-Xms512m -Xmx512m"
    volumes:
      - ./data01:/usr/share/elasticsearch/data
    ports:
      - 9200:9200
  kibana:
    image: docker.elastic.co/kibana/kibana:7.17.8
    container_name: "kibana-container"
    ports: 
      - 5601:5601
    environment:
      - "ELASTICSEARCH_HOSTS=http://elasticsearch:9200"
    depends_on:
      - elasticsearch
```

「discovery.type=single-node」
Elasticsearchを1プロセスで立ち上げるか、複数で立ち上げるかの設定。  
上記の場合だと、1プロセスで立ち上がることになる。  

「depends_on:
      - elasticsearch」
elasticsearchとの依存性表す。  
これがないとelasticsearchとkibanaが同時に立ち上がってしまう。  



