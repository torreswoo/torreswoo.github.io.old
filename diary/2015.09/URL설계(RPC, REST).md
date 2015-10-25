## URL 설계
- URL은 웹 클라이언트에서 호출한다는 시정에서 보면, 웹서버에 존재하는 애플리케이션에 대한 API이라고 볼수있다.
   - RPC(Remote Procedure Call)
   - REST(REpresentational State Transfer)

#### RPC(Remote Procedure Call)
- 클라이언트가 네트워크상에서 원격에 있는 서버가 제공하는 API함수를 호출하는 방식
- URL설게와 API설계를 동시에 도려하여 URL경로를 API함수명으로 쿼리 파라미터를 함수의 인자로 간주한다.
- 그래서 클라이언트는 URL을 전송하는 것이 웹서버의 API함수를 호출한다고 인식하는것
```
http://blog.example.com/search?q=test&debug=true
```

#### REST(REpresentational State Transfer)
- 웹서버에 존재하는 요소들을 모두 리소스라고 정의하고, URL을 통해 웹서버의 특정 리소스를 표현한다는 개념
- 리소스는 시간이 지남에따라 상태state가 변할수 있기 때문에 클라이언트와 서버간의 데이터 교한을 **리소스 상태의 교환** 으로 간주한다.
```
http://blog.example.com/search/test
```

---

---

## 간편 URL ( Searc engine friendly URL, user friendly URL)
- REST방식의 URL개념을 기반으로 간다하면서도 사용자에게 친숙한 URL을 표현하려고 노력.
기존의 URL방식에서 사용되는 문자(?, =, &, #)등을 제거, 뭬리 스트링 없이 경로만가진 간단한 구조의 URL

## 파이썬의 Elegant URL
- 파이썬은 간편URL체계를 도입하였다.
- 그외에도 정규표현식을 추가적으로 사용
- Django 에서 사용

```
from django.conf.urls import patterns, url, include

urlpatterns = patterns('',
    (r'^articles/(\d{4})/$', 'news.views.year_archive'),
    (r'^articles/(\d{4})/(\d{2})/$', 'news.views.month_archive'),
    (r'^articles/(\d{4})/(\d{2})/(\d+)/$', 'news.views.article_detail'),
)

For example, if a user requested the URL “/articles/2005/05/39323/”,
Django would call the function news.views.article_detail(request, '2005', '05', '39323').
```
