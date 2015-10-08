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

---

### contents
- ElasticSearch System
   - 데이터 indexing
   - ElasticSearch 데이터구조 : Index / Type / Document
   - ElasticSearch 시스템구조 : Cluster / node

- Data Handling
   - basic 데이터처리
   - QueryDSL : Query / Filter


---


- 데이터구조
Database -> Index
Table -> Type
Row -> Document : 데이터가 저장되는 최소의 단위


```
//REST API
$ curl -X{methon} http://{hostIP}:{port}/{Index}/{Type}/{Document id} -d '{...data...}'

$ curl localhost:9200  // health check
```
---
- pretty=true  //결과를 JSON형시으로 포매팅해서 보여줌
- _source 필드 : JSON형시으로 데이터가 저장된다.
- _version 필드 : test

---

### CRUD

- 데이터확인
   ```
   - GET
   $ curl -XGET localhost:9200/books/book/1?pretty=true
   $ curl -XGET localhost:9200/books/book/1/_source?pretty=true
   ```

- 데이터입력
   ```
   - POST : 데이터입력 (임의의 Document id를 생성해준다)
   $ curl -XPOST localhost:9200/books/book/1 -d'
      {
         "title" : "ElasticSearch Guide",
         "author" : "Kim",
         "started" : "2014-03-14",
         "pages" : 250
      }'

   - PUT : 데이터수정 /입력
   $ curl -XPUT localhost:9200/books/book/1 -d'
      {
         "title" : "ElasticSearch Guide",
         "author" : ["Kim", "Lee"],
         "started" : "2014-03-14",
         "pages" : 250
      }'
   ```

- 데이터삭제
   ```
   - DELETE : 데이터삭제 ( Type단위삭제 / Document단위삭제)
   $ curl -XDELETE localhost:9200/books/book/1
   $ curl -XDELETE localhost:9200/books/book
   ```

- 업데이트API
   - _update

- 벌크API : 배치작업
   - _bulk
