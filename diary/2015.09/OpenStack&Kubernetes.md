

#### 2015.09.19 (sat)
- OpenStack
- Container : http://www.devblog.kr/r/8y0gFPAvJ2v93JJuIjYxxv9CWVs7HEvqs3yvJe4SrAsV9yRgUlfNt3bFMA99ZEy
- Docker
- CoreOS
- Kubernetes
- Golang : c+javascript 기존의 언어와 가르게 실용성을 꾀한 언어, 클래스가 없고 유연한 callback사용
- AtomicOS
- Flannel

---

### Magnum : using OpenStack with Kubernetes
- OpenStack
- Kubernetes
- Magnum 매그넘

#### OpenStack
개발자가 OpenStack을 이용해서 개발을 하는거다.

- OpenStack은 Iaas형태의 클라우드 컴퓨팅 오픈소스 프로젝트
python프로그램, KVM, netns, LVM등.
RESTful로 연계개발이 가능

- Nova : KVM및 libvirt를 제어, compute로 concurrent한 가상머신 생성
- Neutron
- Cinder : LVM을 제어해서 볼룸관리
- Swift : 비정형데이터관리

#### Kubernetes
구글에서 만든 Docker orchestrator / Go언어로 작성됨
기존의 Docker orchestrator(Core OS의 Swarm)의 부족함을 해소
- 왜만들어짐? 구글의 Borg : Master와 Worker의 cluster구조
- Scalability / Scheduling / Availability
- Kubernetes관련 Job은 tast들을 묶는 용도로 제한하고, 이를 위해 임의적인 k/v스토어를 사용하여
스케줄링 타겟을 Label로 명명하여 유연함을 확보 -> borg를 Kubernetes로 구현

- **Kubernetes Architecture**
   - http://arisu1000.tistory.com/27783
   - Master node : API, Scheduler / ETCd(CoreOS k/v스토어) / Replication Controller
   - Slave node : Kubelet / kube-Proxy
   - Pod : 컨테이너 여러개를 묶어서 관리

   - 클러스터(cluster)
      - 어플리케이션 컨테이너들이 배치되고 실행되는 컴퓨팅 자원
   - 파드(pod)
      - 어플리케이션 실행에 필요한 도커 컨테이너들의 집합
      - 생명주기를 같이 하는 컨테이너들의 그룹
      - Kubernetes를 통한 배포(deploy) 및 실행의 최소 단위
   - 리플리케이션(replication) 컨트롤러
      - pod들의 라이프사이클 관리자
      - 사용자의 선언(JSON 파일)에 따라 Pod 숫자(replica 숫자)를 관리
      - Pod들의 health status를 체크
   - 서비스(service)
      - 관련 pod 집합을 대표하는 단일한/안정적인 이름 (IP Addr, ...)
      - 로드밸런서
   - 레이블(label)
      - pod들의 그룹핑/조직화를 위해 관리하는 key-value pair/메타데이터

- Guest Book : Json, XML형태의 Deployment Descriptor

#### Magnum
- Magnum = OpenStack' IaaS + Kubernetes' cluster Mng
- Magnum은 OpenStack이라는 가상머신위에서
- Heat라는 orchestrator를  ( AWS의 CloudFormation을모사)
- OpenStack의 controller 노드에서 명령실행 및 인스턴스 생성
OpenStack 안에서 kubernetes

- Magnum API server
- Magnum Conductor process
- SQL, Broker이용
- Pod : Pod Manifest파일을 사용
