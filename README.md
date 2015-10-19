# torreswoo.github.io


### Cloud Computing
- AWS
- OpenStack
- Docker
- kubernetes
- vagrant
- Chef
- Puppet


---

#### 2015.09
- [Magnum : using OpenStack with Kubernete]( )
- [URL 설계 : RPC, REST, elegant]()
- study_python : WebProgramming (web server & client module)
- [vagrant & Chef : 개발환경관리]()

#### 2015.10
- ElasticSearch -> study_ElasticSearch
   - ElasticSearch REST API : https://www.elastic.co/guide/en/elasticsearch/reference/current/getting-started.html
   - ElasticSearch Java API : https://www.elastic.co/guide/en/elasticsearch/client/java-api/current/java-api.html
- Meteor.js -> study_meteorjs
- Linux : iptables / du & df
- [install] JDK
- Java
   - Effective Java : 객체생성 / TO설계 / Collection
   - Java8
   - Design Pattern
   - Generic & Collection Framework

- Git
   - bitbucket
   - git remote : https://git-scm.com/book/ko/v1/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EB%A6%AC%EB%AA%A8%ED%8A%B8-%EC%A0%80%EC%9E%A5%EC%86%8C

- SpringBoot -> study_SpringBoot
   - Controller / Service / Configuration
- lombok : 애노테이션으로 자바코드를 간단하게
   - https://www.lesstif.com/display/JAVA/Lombok+-+Java+annotation+library
- Java Json Parser
   - Gson
   - Jackson

### Slack & Hubot & Heroku
- http://haruair.com/blog/2617
- http://blog.naver.com/lestat85/220410949456
- Slack
   - http://blog.hivearena.com/archives/3396
   - 협업을 위한 채팅 도구로 Github, Trello 등 다양한 Integration, 여러 체널의 Push notification 지원 등 편리한 기능을 많이 제공한다. 이전까지는 몰랐는데 내부적으로는 IRC로 구현되어 있는 모양이다. IRC에 친숙하다면 쉽게 적응해서 사용할 수 있을 정도로 유사한 부분이 많다
   - Slack에서 Integration을 통해 Hubot을 추가하면 API키를 발급해줘서 쉽게 연동이 가능한데 무료 정책 내에서는 연동할 수 있는 서비스 수가 제한되어 있기 때문에 여기서는 IRC gateway를 활용했다. IRC Gateway는 보안상 기본 설정에서는 사용할 수 없다. 사용하려면 slack의 primary owner에게 요청해 기능을 사용할 수 있도록 활성화 해야 한다. 다만 이 gateway를 사용하게 되면 채팅방의 내용이 외부로 노출될 가능성이 있다는 요지의 안내를 받을 수 있는데 보안성에 민감한 slack이라면 이 방법보다 앞서 얘기한 hubot integration을 사용하는 편이 낫다
- Hubot
   - Github에서 공개한, 자동화를 위한 채팅봇이다. Node.js 기반에 CoffeeScript로 짜여져 있고 Heroku와 같은 곳에 손쉽게 디플로이 해서 활용 가능하며 확장도 간편하게 가능하도록 구성되어 있다. 또한 이미 많은 기능들이 구현되어 있어서 npm에서 hubot-script을 내려받고 설정하는 것으로도 강력하게 활용
   - http://nodeqa.com/nodejs_ref/92
   - https://github.com/slackhq/hubot-slack
- Heroku
