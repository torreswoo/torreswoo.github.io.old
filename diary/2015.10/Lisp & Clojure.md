# Lisp & Clojure

---
### ClojureScript HTML5 Game Programming with phaser.js
- https://github.com/philoskim/cs-game
- Clojure 소개
- ClojureScript 소개
- HTML5 Game Programming with phaser.js

---
### ClojureScript로하는 함수형 UI 프로그래밍
- 클라이언트단에서 사용되는 함수형프로그래밍인 ClojureScript
- UI프로그래밍은 어렵다 - 복잡성
   - 복잡성 : UI컴포넌트, 비동기입력, 비즈니스로직상의 상태를관리해야함
   - 지금까지는 OOP / MVC패턴 / 콜백 등을 사용해서 대처

#### 그복잡성은 어떻게 제거되는가
- 콜백의 복잡성을 제거 -> CSP / FRP
- CSP는 경량 멀티스레드기반, low-level라이브러리기반 / FRP는 보다 추상화수준이 높다.
- CSP (Communicating Sequential Processes)
   - 예전의 람다나 튜링머신에서는 동시성에 대한 고려가 없는 시퀀셜하게 설계가됨
   - Processes라는 수학의 한분과로 concurrency를 수학으로 정식화
   - parellel process를 마치 Sequential하게 보이게하는 것
   - chennel
   - 이용 : Go / Clojure(core.async라이브러리)
- FRP (Functional Reactive Programming)
   - Signal(Behavior)
   - Observable Stream, EventStream

#### 함수형프로그래밍(Functional Programming)
- 상태를 격리 immutable vale를 입력
- "Are We There Yet?" - Rich Hickey
   - value / Identity / State / Time
   - Epochal Time Model
- ***방법론마다 전역변수는 좋을수도 나쁠수도있다. 함수형에서 전역변수는 좋을수도있다.***

#### FRP - Signal(Behavior)
- **time-varing value**, 즉 상태를 하나의 값으로 추상화, 그러면 상태는
- Haskell

#### UI컴포넌트상에서의 복잡성
- OOP 복잡성 -> "Local State is Poison"
- MVC 복잡성 -> ReactJS
   - Just UI
   - One-way Data flow
   - Component : just function -> reusable / declarable
   - Virtual DOM
      - Observation이 필요없이 전체를 빠짐없이 다그린다.
      - No more dirty checking! / No Data Binding
      - Virtual DOM은 메모리상에서 diff를하고 변경된부분만 Browser DOM에 반영
- Flux : 단방향데이터흐름을 활용해 뷰컴포넌트를 구성하는 React를 보호
- **ClojureScript는 ReactJS의 랩퍼들**
   - Om
   - Reagent : http://reagent-project.github.io/
   - Quiescent
   - Rum

#### HTML5크로스 플랫폼
- NW.js
- Electron
- CER3

- Cordova
- Crosswalk
- React Native

---
### iOS 앱 개발 with React Native + ClojureScript
- http://www.slideshare.net/cheolhee/ios-app-with-react-native-clojurescript
- iOS app dev with Clojure
   - Native App : RoboVM -> **Swift**
   - Hybrid App + ClojureScript -> 하이브리드앱은...
   - **React Native** : View가 webview가아니라 native이다

#### React Native + ClojureScript
- Om => natal : https://github.com/dmotz/natal
- Reagent => : https://github.com/chendesheng/ReagentNativeDemo


---
### Clojure HTTP API 서버 구현을 위한 라이브러리 / Kakao 김은민
- http://www.slideshare.net/eunminn/clojure-http-api

#### HTTP Server Application
- Framework
   - Application Server
   - Routing
   - Database ORM / Migration
   - View Template

#### Clojure HTTP API Server Application
- Clojure는 작은 함수를 조합해 큰기능을 완성
- Clojure HTTP API서버
   - Application Server
   - Routing + Servlet Abstraction (Java)
   - SQL사용
---

- Micro Framework : Clojure에서는 라이브러리의 모음
   - Luminus
   - Duct
- Lumos
   - API서버 구성을 위한 lein template

- (1) Application Server library - immutant2
   - immutant/web : Netty와같은 비동기 애플리케이션서버
- (2) Servlet Abstraction library
   - Ring : Servlet Wrapper라이브러리, 기본컨테이너로 jetty사용 / Servlet 2.5
   - Pedestal : Servlet Wrapper + Routing + .., 기본컨테이너로 jetty, tomcat, immutant사용 / Servlet 3.1
- (3) Routing library
   - compojure :
   - Pedestal : 트리형태로 Routing표현 / REST URL을 구성하기에 좋음
   - liberator : REST URL을 구성하기에 좋음
- (4) SQL library
   - sqlkorma : SQL에대응하는 매크로를제공, clojure.jdbc를 직접 호출할 필요가 없음
   - honeysql : .., clojure.jdbc를 직접 호출, 결과가 SQL의 스트링이므로 좀더 자유롭게 사용할수있다.
- (5) Database Connection Pool library
   - Apache DBCP
   - HikariCP : 자바를 쓰기보다 한번 랩핑이되어있음
   - c3p0
- (6) Database Migration library
   - migratus
   - ragtime : weavejester의 라이브러리
- (7) Lifecycle library
   - Clojure var!, Server에서 사용하는 상테있는 resource가 많다.
   - Connection Pool / Server resource Lifecycle 관리
   - Stuart Sierra Component : 시스템으로 Component의 의존관계를 정의하고..
   - component
- (8) API Document library
   - Swagger : HTTP API를 정의하는 Spec
   - fnhouse 문서제공보다는 request/response체크에 중점
   - Pedestal-swagger

#### library선택의 고민
- Contextual vs Composable
   - Composable : 유연, 유지보수, 다목적 / 큰책임, 훈력이필요, 정해진규칙이없음
   - Contextual : 문제가 해결되어있음, 사용이편리함 / 다른문제를 해결하지못함, 유지보수가필요

---
### CommonLisp으로 하는 실시간 WebGL 프로그래밍
