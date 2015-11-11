- 버전확인 https://packagist.org/
- php 5.5.27
- Codecption 2.1.3
- xdebug 2.3.3
- c3.php 2.0
- media.so (php5.5)

# Codecpetion 설치

## php 5.5.27설치
- mbstring필요
   ```
   $> yum install php-mbstring

   $> ./configure \
       --prefix=/app/php \
       --with-config-file-path=/app/php/etc \
       --enable-fpm \
       --enable-pcntl \
       --enable-sigchild \
       --enable-sockets \
       --enable-mbstring \
       --with-openssl \
       --with-zlib \
       --with-curl \
       --with-mcrypt=/usr/local \
       --with-mysql=mysqlnd \
       --with-libxml-dir=/usr/local
   $> make
   $> make install
   ```
- php.ini 설정(php초기설정)
   ```
   $> cd /app/php/etc/
   $> cp /app/src/php-5.5.27/php.ini-production php.ini
   $> vi php.ini
           ( 부분 찾아서 수정 )
      short_open_tag = On
      expose_php = Off
      date.timezone = Asia/Seoul
   ```
- php-fpm.conf(php-fpm설정)

   ```
   $> cd /app/php/etc/
   $> cp php-fpm.conf.default php-fpm.conf
   $> vi php-fpm.conf
            ( 부분 찾아서 수정 )
           [global]
           error_log = log/php_fpm.log
           rlimit_files = 65535
           [www]
           user = ids      //ids계정으로
           group = ids     //ids그룹
           listen = /tmp/php-fpm.sock
           pm = dynamic
           pm.max_children = 4096
           pm.start_servers = 18
           pm.min_spare_servers = 12
           pm.max_spare_servers = 24
           pm.max_requests = 64
           rlimit_files = 65535
   ```
- so파일 추가
   ```
   $> cd /app/php/lib/php/extensions/no-debug-non-zts-20121212/
   $> cp /app/src/media.so media.so
   $> cp /app/src/dcf.so dcf.so
   $> chmod 755 *.so  (/app/src/, /app/php/lib/php/extensions/no-debug-non-zts-20121212/ )

   $> vi /app/php/etc/php.ini
      extension=media.so (모듈추가)
      extension=dcf.so  (모듈추가)
      extension_dir=/app/php/lib/php/extensions/no-debug-non-zts-20121212/
   ```

## Codecption 2.1.3
- Quickstart : http://codeception.com/quickstart
   ```
   1.다운
   $> wget http://codeception.com/codecept.phar
   2.설치
   $> php codecept.phar bootstrap
   3.Acceptance Test  
   $> php codecept.phar generate:cept acceptance Welcome
   4.test작성
   $> vi tests/acceptance/WelcomeCept.php
   5. Configure Acceptance Tests  
   $> vi tests/acceptance.suite.yml
   6.실행
   $> php codecept.phar run
   ```

## Code Coverage
- code Coverage : http://codeception.com/docs/11-Codecoverage
   - Remote CodeCoverage :: Local Server
- xdebug 2.3.3
- c3.php 2.0

#### xdebug 2.3.3
   - http://xdebug.org/docs/install
   - http://blog.esukmean.com/post/Install_XDebug_on_server
   - https://opentutorials.org/course/62/2546
      ```
      $> yum install php-pear  
      $> pecl install xdebug

      $> wget http://xdebug.org/download.php#releases
      $> phpize
      $> ./configure --enable-xdebug
      $> make
      $> make install

      $> vi /app/php/etc/php.ini
      [xdebug]
      zend_extension=/app/php/lib/php/extensions/no-debug-non-zts-20090626/xdebug.so
      xdebug.remote_enable=1
      ;xdebug.remote_handler=dbgp
      ;xdebug.remote_host=
      ;xdebug.remote_port=9000
      ;xdebug.remote_log="/var/log/xdebug/xdebug.log"
      ```

#### c3.php 2.0
   - https://github.com/Codeception/c3
   - 다운 $ wget https://raw.github.com/Codeception/c3/2.0/c3.php
   - $ vi main.php // 코드에 추가
      ```
      include 'c3.php';
      define('MY_APP_STARTED', true);
      ```
   - $ vi codeception.yml // 설정에 c3.php 경로로 설정
      ```
      coverage:
         enabled: true
         include:
              - main.php
         c3_url: 'http://localhost:9000/ich/api'
      ```
