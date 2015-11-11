# re:Invent2015 RECAP
- http://onoffmix.com/event/55782

- re:Invent 2015 신규 서비스 소개- 데이터 관점에서
- re:Invent 주요 신규 기술 소개 - 모바일, IoT 중심으로
- re:Invent 행사 후기 - 사용자 관점에서

- re:Invent 앵콜세션 DAT202 – Managed Database Options on AWS
- re:Invent 앵콜세션 GAM201 – Cloud Gaming Architectures from Mobile to Social to MMO

- re:Invent 행사 후기 - 파트너사 관점에서    
- re:Invent 주요 서비스 요약 - 인프라 및 보안 기술 변화  

---

# re:Invent 2015 신규 서비스 소개- 데이터 /모바일 /  /윤석찬
- Amazon QuickSight, Kinesis Firehose : 빅데이터 분석 서비스 확대
- MariaDB, ElasticSearch : 오픈 소스를 기반한 DB 및 검색 서비스
- in the Cloud : 빅데이터 / 모바일 / IoT
- 빅데이터에서 실지적인 가치를 찾아라

## 데이터기반 개발
- 과거데이터 분석 + 실시간데이터분석 + 데이터기반예측

### 과거데이터 분석
- ElasticSearch : 실시간데이터 검색 및분석을 위한 LogStash / Kibana와 연계
- Amazon ElasticSearch : 손쉬운 클러스터생성 .

### 실시간 데이터분서
- Amazon Kinesis Firehose : Easily load streaming, 실시간데이터를 자동처리
- Amazon Kinesis Analytics :

### 데이터기반예측
- BI : 비지니스 인텔리전스 .. 고비용..오랜시간..
- Amazon QuickSight : 다양한AWS데이터소스사용, 인메모리기반병렬연산엔진으로 쿼리, 시각화,
   - SPICE : 인메모리 기반 병렬 연산 엔진 (행기반으로 데이터압축 / 다중경로연산)

## 클라우드기반의 모바일앱
- AWS MobileHub

## IoT
- 인터넷으로 연결된 기기들, 대량의 센서나 로그데이터 발생
- AWS IoT Device Shadows : 각각의 기기들을 클라우드에
- AWS IoT Hardware 파트너들이 Kit
- MQTT 경량 메세지 프로토콜 : http://www.joinc.co.kr/modules/moniwiki/wiki.php/man/12/MQTT/Tutorial

---

# re:Invent 2015 신규 서비스 소개- Computing관점에서 /정민영
- Instance - Container - Serverless
### Instance
- T2 Nano / X1 /

- T2 Instance : Burstable performance
   - T2 Nano : 매우낮은 부하를 담당, 1시간정도 최대 CPU를 사용할수있는 credit제공
- X1 : 메모리최대2TB / 100개이상의 CPU -> Apache Spark, Presto등에 사용..
- Dedicated Host : Instance가 구동되는 물리장비의 지정가능
- EC2 Spot Block
   - Spot Instance : AWS에서 남는 자원을 경매방식으로 저렴하게
   - 기존의 Spot과는 다르게
### Container
- Container : Docker / ECS()

- Amazon EC2 Container Registry : 완전한 관리형 private Docker이미지 저장소
- ECS CLI : compose
- AZ Aware Scheduler : 기존의 Service Scheduler개선 / 분산된 AZ에 Task를 균형있게 배치 / 가용성향상과 좀더 효율적인 분산
- 향상된 Docker옵션

### Serverless
- 하드웨어가 소프트웨어의 리소스중의 하나로
- AWS Lambda : Serverless / Event-Driven Scale / Subsecond billing
   - node.js / Python
   - Versioning
   - Lambda cron : Scheduled Event
- API Gateway Lambda : 접점(Endpoint) 제공서비스 / 인증, 캐싱, 모니터링

---

# re:Invent 행사 후기 - 사용자 관점에서

---

# re:Invent 앵콜세션 : DAT202 – Managed Database Options on AWS
- AWS 데이터베이스 서비스은 RDS, DynamoDB, ElastiCache 및 Redshift를 통해 어떻게 IGAWorks가 모바일 비지니스 플랫폼을 AWS 아키텍쳐를 통해 구성하여 신뢰성 높고 비용 효율적으로 운영

## Adpopcon
- Ad Inventroy
- Participation log
- DB
   - RDS
   - DynamoDB
   - ElastiCache
   - RedShift : 내부 BI, 시간별 분석! Hive4시간-> 분단위로!

---

# re:Invent 앵콜세션 GAM201 – Cloud Gaming Architectures from Mobile to Social to MMO
-  AWS에서 게임 서비스를 위해 수천에서 수백만명의 사용자를 감당할 수 있는 확장성 높은 아키텍쳐를 구성하는 방법과 자동화 방법 등 쿠키런을 운영하고 있는 데브시스터즈의 개발 및 운영 경험을 오토스케일링 및 데이터 분석에 걸쳐 상세하게

## 데브시스터즈 / 라인쿠키런 Cookie Run 1000만 DAU
- Highly Reliable / Quality assured / auto scaling /

- redesigning the backend
   - heart : MySQL -> NoSQL(Couchbase) : MySQL for game data / NoSQL for user data
- Improving Logging System
   - need real-time log querying capability -> ELK stack
   - adopted BigData platform EMR(hadoop) -> Spark on EC2
- Improving Game Patch System
   - based on S3 & CloudFront (CDN) / Resource Manager
- Adding Global User Ranking System
   - redis with ElastiCache

## test
- Auto scaling Gotchas
   - 미리예측해서 늘러놓는게 필요하다.
   - dont set minimum instance of 1 or 2
   - Use mutiple AZ(Availability Zones)

QUIC
