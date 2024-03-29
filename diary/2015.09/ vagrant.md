
# Vagrand
- 간소화된, VM 관리 서비스. Virtual Box와 같은 Hypervisor가 있다고 해도, VM을 생성하는 것 자체가 번거로운 작업.
Hypervisor에서 논리적인 가상 하드웨어 머신을 생성하고 가상머신에 OS를 설치하고, 일일이 설정을 해줘야 한다. 이런 반복적인 작업을 조금더 손쉽게 자동화 할 수 없을까? 하는 아이디어에서 시작한 것이 Vagrant.
- 출처 : http://mobicon.tistory.com/322
http://wiki.opencloudengine.org/pages/viewpage.action?pageId=2852295


### 설치
  - VirtualBox 다운로드 및 설치
  - Vagrant 다운로드 및 설치
  - Vagrant 환경 설정
    + 프로젝트 디렉토리를 하나 만든다. 또는 기존 Project가 있으면 디렉토리로 이동한다. VirtualBox에 원하는 이미지를 다운로드하여 설치한다. 이미지는 Vagrant에서 패키징한 Box를 다운로드할 수 있는 별도 사이트를 제공한다
    + Box는 기본설정과 OS가 설치된 VM 템플릿 이미지이다

- 형식 : vagrant box add [title] [download-url]
```
$ vagrant box add centos64 http://developer.nrel.gov/downloads/vagrant-boxes/CentOS-6.4-x86_64-v20130427.box
```
- 프로젝트를 초기화 한다
```
$ vagrant init centos64
```
---

### 가상머신 기동
  - Vagrant 통해 가상머신 기동하기

- 기동
```
$ vagrant up
```

- VM 들어가기 : 같은 디렉토리면 ssh를 n개까지 open 가능
 ssh를 통하여 별도의 VM 으로 들어갈 수가 있는 것이다.
 단, vagrant init [title] 된 Vagrantfile 파일이 같은 디렉토리에 있어야 함
```
$ vagrant ssh
```

- 정지
```
$ vagrant halt
```

```
id : vagrant / pw : vagrant
$> vagrant box list  // 설치된 Box확인
```
---

### Vagrantfile
- Box가 VM 생성을 위한 기본 템플릿이라면, Vagrant file은 생성될 VM에 대한 세부 설정을 정의

### Box


### Provisioning
- 예제는 VM이 기동될때 마다 shell 명령어를 수행하도록 한것인데, 명령어말고도 shell스크립트를 수행하게 할 수 도 있고, puppet이나 chef와 같은 configuration management 도구를 이용해서, 제품을 설치
```
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "precise32"
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"
  config.vm.provision :shell, :inline => "sudo apt-get install -y apache2"
end
```

### Multi Machine
- https://docs.vagrantup.com/v2/multi-machine/
```
config.vm.define "elastic01"
config.vm.define "elastic01"
```

---

//
http://okky.kr/article/265177


// Linux 포트확인
netstat -anp | grep "LISTEN "
netstat -tnlp | grep -v 127.0.0.1 | sed 's/:::/0 /g' | sed 's/[:\/]/ /g' | awk '{print $5"\t"$10}' | sort -ug

// 특정포트의 방화벽해제
sudo iptables -I INPUT 1 -p tcp --dport 9200 -j ACCEPT
service iptables stop

lsof -i -P | grep -i "listen"


```
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  # dev
  config.vm.define :dev do |dev_config|
     dev_config.vm.host_name = "dev"
     dev_config.vm.network "public_network", ip: "10.0.0.100"
     dev_config.vm.box = "centos64"
     dev_config.vm.network "forwarded_port", guest: 9200, host: 9200, auto_correct: true # elastic
  end

  # elastic01
  config.vm.define :elastic01 do |vm01_config|
     vm01_config.vm.host_name = "elastic01"
     vm01_config.vm.network "public_network", ip: "10.0.0.101"
     vm01_config.vm.box = "centos64"
     vm01_config.vm.network "forwarded_port", guest: 9200, host: 9200, auto_correct: true # elastic
  end

  # elastic02
  config.vm.define :elastic02 do |vm02_config|
     vm02_config.vm.host_name = "elastic02"
     vm02_config.vm.network "public_network", ip: "10.0.0.102"
     vm02_config.vm.box = "centos64"
     vm02_config.vm.network "forwarded_port", guest: 9200, host: 9200, auto_correct: true # elastic
  end

end
```
