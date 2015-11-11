# Codecpetion

```
php codecept.phar bootstrap
php codecept.phar generate:suite api
php codecept.phar generate:cept api FilePost
php codecept.phar generate:cept api FileDel
php codecept.phar build
php codecept.phar run
php codecept.phar run api 파일

// run test
$ php codecept.phar run
$ php codecept.phar run acceptance
$ php codecept.phar run acceptance SigninCept.php
$ php codecept.phar run tests/acceptance/SigninCept.php
$ php codecept.phar run tests/acceptance/SignInCest.php:anonymousLogin
$ php codecept.phar run tests/acceptance/backend

//Report
$ php codecept.phar run --steps --xml --html       //  -> _output/report.html
$ php codecept.phar run --coverage --coverage-xml --coverage-html  // ->
```
---

- Acceptance Test : http://codeception.com/docs/03-AcceptanceTests
   - vi tests/acceptance/...Cept.php
   - vi tests/acceptance.suite.yml
   - cept 시나리오기반
   ```
   $> php codecept.phar generate:cept acceptance Signin // cept시나리오기반 Signin으로 만들어짐
   $> php codecept.phar run  // 실행
   $> php codecept.phar run acceptance --steps  // acceptance만 디테일하게
   ```
   -cest 클래스기반
   ```
   $> php codecept.phar generate:cest acceptance PageCrud
   ```

- Functional Test : http://codeception.com/docs/04-FunctionalTests
- Unit Test : http://codeception.com/docs/05-UnitTests

- REST WebService Test
   - http://codeception.com/docs/10-WebServices
   - http://codeception.com/docs/modules/REST

   - vi codeception.yml
   ```
   coverage:
       enabled: true
       include:
        - main.php
       c3_url: 'http://localhost:9000/ich/api'
   ```

   - vi tests/api.suite.yml :
   ```
   modules:
    enabled:
        - PhpBrowser:
            url: http://localhost:9000/ich/api/
        - \Helper\Acceptance
   ```
   - 명령어
   ```
   $> php codecept.phar generate:suite api   // api만들기
   $> php codecept.phar generate:cept api FilePost  // POST테스트
   $> php codecept.phar run
   $> php codecept.phar run api
   $> php codecept.phar run --coverage --coverage-xml --coverage-html
   ```
