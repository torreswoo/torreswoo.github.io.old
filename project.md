# PHP



# Nginx





---

## Test
aws : EC2

0_0. [setting] yum설정
- vi  /etc/yum.repos.d/epel.repo 에서 baseurl을주석해제하고, mirrorlist를 주석

0_1. [setting] linux terminal
# vi ~/.bashr
# Source global definitions
if [ -f /etc/bashrc ]; then
        . /etc/bashrc
fi
# User specific aliases and functions
export PS1="\e[1;37m[\e[36m\D{%Y-%m-%d %H:%M:%S}\e[37m] \
[\e[32m\u\e[31m@\e[33m\h\e[37m] \e[34m\w\e[m\n\$ "

0_2. [setting] vim
# yum -y install vim
# vi /etc/bashrc
alias vi='vim'   /usr/bin/vim

0_3. [setting] java


0_4. [setting]
0. 계정 생성
# mkdir /app (애플리케이션 모든정보)
# groupadd -g 501 ids
# useradd -u 501 -g 501 -d /app/ids -s /bin/bash ids
(# useradd -d /app/ids ids)
# passwd ids
# cat /etc/passwd (확인)

0. 권한부여
# chown ids . (/app에서 파일의 소유권을 ids사용자에게)
# chgrp ids . (/app에서 파일의 소유권을 ids그룹에게)
!!!!! chown -R ids:ids /app/

//////////////

1. solr설치

/////////////////
2. nginx설치
- nginx
- pcre :
$> wget ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre/pcre-8.36.tar.gz
yum -y install gcc-c++
yum -y install pcre pcre-devel    // PCRE : NGINX는 Perl5에서 사용하는 정규표현식 라이브러리인 PCRE
yum -y install zlib zlib-devel    // zlib : Nginx모듈에서 gzip압축사용시에 zlib필요
yum -y install openssl openssl-devel  // OpenSSL : 고성능 범용 해석알고리즘
yum -y install libevent-devel libxml2-devel //기존의 XML 파서들보다 다양한 인터페이스를 가지고 다양한 언어그룹에서 사용할 수 있는 기능을 포함
yum -y install curl curl-devel
yum -y install libtool-ltdl-devel


2_1. 다운로드  wget http://nginx.org/download/nginx-1.6.3.tar.gz
2_2. 의존성설치  wget ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre/pcre-8.37.tar.gz
PCRE    wget ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre/pcre-8.37.tar.gz
OpenSSL  wget http://www.openssl.org/source/openssl-1.0.1e.tar.gz
zlib  wget http://zlib.net/zlib128.zip

2_3. configure => make => make install

./configure \
--prefix=/home/ec2-user/app/nginx \
--with-debug \
--with-http_ssl_module \
--with-http_realip_module \
--with-pcre=/home/ec2-user/app/src/nginx/pcre-8.36

## nginx log
mkdir -p /home/ec2-user/app/log/nginx/accesslog
mkdir -p /home/ec2-user/app/log/nginx/errorlog

## nginx.conf
...
log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                  '$status $body_bytes_sent ($request_time sec) "$http_referer" '
                  '"$http_user_agent" "$http_x_forwarded_for"';
...
access_log  /home/ec2-user/app/log/nginx/accesslog/access.log combined;
error_log   /home/ec2-user/app/log/nginx/errorlog/error.log error;

http://52.69.115.72:9000

//////////////////////

3. apache : http://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_%EC%95%84%ED%8C%8C%EC%B9%98_%EC%B5%9C%EC%8B%A0%EB%B2%84%EC%A0%84_%EC%84%A4%EC%B9%98_(%EC%BB%B4%ED%8C%8C%EC%9D%BC)
3_1. 다운로드
- wget http://ftp.neowiz.com/apache/httpd/httpd-2.4.16.tar.gz
- wget http://ftp.neowiz.com/apache/apr/apr-1.5.2.tar.gz
- wget http://ftp.neowiz.com/apache/apr/apr-util-1.5.4.tar.gz
- wget http://downloads.sourceforge.net/project/pcre/pcre/8.33/pcre-8.33.tar.gz
$ mv apr-1.5.2 ./httpd-2.4.16/srclib/apr
$ mv apr-util-1.5.4 ./httpd-2.4.16/srclib/apr-util

pcre폴더에서 ./configure / make / make install

3_2.
./configure  \
--prefix=/home/ec2-user/app/apache \

3_3.
bin/httpd -k start
bin/httpd -k stop
## apache log
mkdir -p /home/ec2-user/app/log/apache/accesslog
mkdir -p /home/ec2-user/app/log/apache/errorlog


//
- 로그위치수정 httpd.conf
ErrorLog "/home/ec2-user/app/log/apache/errorlog/error_log"
CustomLog "/home/ec2-user/app/log/apache/accesslog/access_log" common

- User/Group ec2-user로

- 호홈디렉터리까지 각각의 디렉터리를 755 로
DocumentRoot "/home/ec2-user/app/apache/htdocs"

http://52.69.115.72:80


---

##
