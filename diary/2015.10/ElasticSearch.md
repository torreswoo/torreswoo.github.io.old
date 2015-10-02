## ElasticSearch  9200

1. 다운&설치
```
 wget https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-1.5.2.tar.gz
```

2. 기본적인 plugin설치 http://develop.sunshiny.co.kr/1010
```
$> bin/plugin --list
$> bin/plugin --remove head
$> bin/plugin --install mobz/elasticsearch-head   //http://localhost:9200/_plugin/head/
$> bin/plugin --install lukas-vlcek/bigdesk     //http://localhost:9200/_plugin/bigdesk/
$> bin/plugin --install enezes/elasticsearch-kopf  // http://localhost:9200/_plugin/kopf/
```

3. 실행
```
$> bin/elasticsearch -d (d는 백그라운드로)
```
 curl 'http://localhost:9200/?pretty' 를 입력해서 결과가 제대로 오는지 체크
설
