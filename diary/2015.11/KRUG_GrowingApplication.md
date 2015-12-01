# 객체지향 아키택쳐 /조용호

## 아키텍처
- 프로젝트에 참여하는 개발자들이 설계에
- 서로다르고 관련있는 관심사를 분리

## 레이어 아키텍쳐
- 일반적 : Presentaion(사용자의 ) / Domain(비즈니스와 관련된) / DataSource(데이터를 조작하는 모든)
- 가장 중요한 레이어는 Domain Layer : 그 시스템이 다른 서비스와 차별화되는 부분, 가장적절하게 반영되었는가.
- Domain Layer설계방법 : 절차지향(TranscationScript패턴) / 객체지향(DomainModel패턴)
   - 이둘의 차이와 어떤점이 DomainModel패턴이 더 좋은가?

### TranscationScript패턴

### DomainModel패턴

### Project 온라인 영화예매시스템
- Domain Concept : 영화 Movie, 상영 Showing, 할인규칙 Rule, 할인정책 Discount(Amount Discount / Percent Discount) , 예매 Reservation

#### TranscationScript패턴 : 절차지향
- 1.DBtable
- 2.Anemic Domain DB테이블에 매칭되는 class를 만듬
- 3.DAO
- 4.절차적인 예매로직
- 중앙집중식 제어스타일 / Sequence를 나타낼때 하나가 모든것을 관리

#### DomainModel패턴 : 객체지향
- 객체 : 프로세스와 데이터가 하나의 덩어리
- 객체지향설계 : 협력하는 객체들의 공동체
- 협력 : Message sending

- CRC card : 책임과 협력을 표현하기위한 객체지향 설계도구 Candidate / Responsibility / Collaborator

- Service Layer : 어플리케이션로직
   - 어플리케이션 경계 / 로직 / 도매인로직의 재사용성 촉진
   - Transcation boundary를 결정
- Domain Layer : 도매인로직을 관리

- DataSource 는 왠만하면 RDB
   - ***객체-관계 임피던스 불일치***
   - Data Mapper : 객체모델과 DB스키마간의 독립성을 유지 => ORM / JPA표준
   - DAO 테이블 데이터 게이트웨이

---

# 애플리케이션 / 최범균

## DIP

## Aggragate
- 요구사항에 따라 Aggragate경계정의 : 규칙, 트랜잭션 범위를 고려 / SRP
- 고정되어있는 것이 아니다. 로직이 바뀌고 트랜잭션의 범위가 바뀌고하면 변할 수 있다.
- ID참조 : Aggragate간에 ID를가지고, application계층에서 이것을 조합하고 연결해줌
   - 다 끝어주니까 전체적인 복잡도는 낮아진다. 확장가능한 상태로 바꿀때 사용하면 좋다

## CQRS
- 당장 바꾸기힘든 DB조인 중심표준... 한방쿼리 / left조인 / DB전용기능....
- 상태변경 모델과 조회모델 분리
   - 상태변경 모델 : Controller | application | Domain | JPA
   - 조회모델 : Controller | DAO(MyBatis, SQL) / View모델

- CQRS의 장점 : 모델의 복잡도 감소
- CQRS의 부담 : 더 많은 구현, 데이터동기화 필요

## Event
- 성능문제가 있다.. blocking..등등..
- 이벤트의 용도
   - trigger : 다른기능을하기위한 트리러로 이벤트를 사용
   - 데이터 동기화 : 다른시스템간 데이터 동기화 목적으로 이벤트 사용
- Domain & Event
   - Domain의 상태변경을 Event로 나타냄

- Event 장점
   - 서로다른 도메인영역이 로직을 끓어줌. coupling을 끓음
   - 이벤트 핸들러 추가로 기능확장 : OCP(Open Close Principle) "나를 바꾸지 않고 기능을 추가"
- 동기 Event 단점 : 성능문제..
- 비동기 : 이벤트처리 시간, "A할때, B해라" 요구사항에서 A와 B의 일관성
   - 비동기이벤트처리방식1 : Event Dispatcher에서 Message Queue에전송
   - 비동기이벤트처리방식2
   - 비동기이벤트처리방식3 : Message Queue : RabbitMQ와는 다르게 Kafka처러 땡겨가는 방식으로
- 이벤트도입시고려사항 :

- CQRS + Event 조합

---
