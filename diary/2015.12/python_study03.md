# Backbone.js
- template engine이 없으므로 underscopre.js / jQuery

## Backbone structure
- Model : Django models
- Collections : Django queryset
- Views : Django template
- Routers : Django URL

## Backbone MVC
- config JSON

## View
var TemplateView = Backbone.View.extend
- templateName
- initialize
- render : 본격적으로 HTML로 렌더링
- getContext

## Router

## Template


## url.py
- 장고와 연결

## User Authentication
- Session Model

## TemplateView
- Homepage View
- Header View

## FormView
- Login View


---

# Django
- Project: 개발대상이되는 전체 프로그램 / Application : 서브
- 하나의 애플리케이션이 여러개의 프로젝트에 포함될수있기때문에 애플리케이션을 한번 개발하고 재사용하여 개발

## MTV패턴
- Model : DB에 저장되는 데이터
- Template : 사용자에게 보여주는 부분
- View : 실질적으로 프로그램 로직이 동작하여 데이터를 가져오고 적절하게 처리한 결과를 템플릿에 전달

## 프로젝트 뼈대 만들기
- Db.sqlite3 : SQLite3 데이터베이스 파일
- Manage.py : 장고의 명령어를 처리하는 파일
- Mysite 디렉토리: 프로젝트명으로 만들어진 디렉토리. 프로젝트 관련 파일
- Polls 디렉토리: 애플리케이션명으로 만들어진 디렉토리

- Templates 디렉토리 : 템플릿 파일들이 들어 있음. 보통은 프로젝트 레벨과 애플리케이션 레벨의 템플릿으로 구분하여 생성
- Static 디렉토리 : CSS, Image, Js 파일들이 들어 있음. 보통은 프로젝트 레벨과 애플리케이션 레벨로 구분하여 생성.
- Logs 디렉토리 : 로그 파일들이 들어 있음. 로그 파일의 위치는 settings.py파일의 LOGGING 항목으로 지정함.

## 실습
$ pyenv shell my-virtual-env-2.7.8
$ django-admin.py startproject proj_mysite  // proj_mysite라는 프로젝트를 생성.
$ python manage.py startapp polls // polls라는 애플리케이션을 생성.
$ python manage.py migrate  // DB에 변경사항을 반영.
$ python manage.py runserver //현재까지의 작업을 개발용 웹서버로 확인.

http://localhost:8000/admin

$ python manage.py createsuperuser // 관리자(슈퍼유저) 계정 등록.
