# Nginx
- HTTP
- Load Balancing
- HTTP video Streaming


- Nginx Plus : http://demo.nginx.com/status.html
   - 프록시 서버로 사용하는 일이 많다보니, 뒤의서버들의
- senginx : http://demo.senginx.org/
   - 보안이강화됨, 여러가지 보안이슈의 공격에 대한 모니터링 / OpenSource
- Tenginx : http://tengine.taobao.org/


- Graceful re-configuration
- 1 worker <-> 1 CPU core : CPU 코어수에 맞게 worker개수를 맞춘다.
- Single Thread / Asynchronous한동작은 Event-driven, callback함수, Non-blockingIO
- Master : config관리만함. worker를 관리하는 일만한다.
- worker : 직접, 모든걸다함
- AIO : http://djkeh.github.io/articles/Boost-application-performance-using-asynchronous-IO-kor/
- nginx -V : 설정정보
- Gzip모듈 : On the fly로 압축을해서보냄  / curl -compressed옵션을사용하면
- Upstream Module
   - failover : backup모듈
   - IP / local(UnixDomainSocket)
- Network Stack
   - 시스템레벨에서 설정해야하는 것
