
# JDK 다운로드
```
$ wget http://download.oracle.com/otn-pub/java/jdk/7u45-b18/jdk-7u45-linux-x64.tar.gz
$ wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u20-b26/jdk-8u20-linux-x64.tar.gz
```

# 압축 해제
```
$ tar -xvf jdk-7u45-linux-x64.tar.gz
```

# JDK 디렉토리 이동
```
$ mv /usr/src/jdk1.7.0_45 /usr/local/jdk1.7.0_45
```

# 환경변수 추가
```
$ vi /etc/profile
...
export JAVA_HOME=/usr/java/jdk1.6.0_45
export PATH=$PATH:$JAVA_HOME/bin
...
```

# 적용
```
$ source /etc/profile
```

# 확인
```
$ java -version
$ which java
```
