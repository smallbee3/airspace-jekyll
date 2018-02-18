# 01-30-07-Djangogirl-Tutorial

---

> python manage.py startapp 앱이름
-> 


blog라는 패키지 하나가 애플리케이션이라고 이해하면 됩니다.


-----------------------

urlconf = urlresolver 역할

일치하는 함수룰 찾아주는 역할
정규표현식을 쓰는게 기본값에서 없어짐.

from django.http import HttpResponse
from django.shortcuts import render



### Create your views here.


def post_list(request):
    # 1. 브라우저에서 요청 -> runserver
    # 2. 요청이 runserver로 실행중인 서버에 도착
    # 3. runserver는 요청을 Django code로 전달
    # 4. Django code중 config.ruls모듈이 해당 요청을 받음
    # 5. config.urls모듈은 ''(admin/를 제외한 모든 요청)을 blog.urls모듈로 전달
    # 6. blog.urls모듈은 받은 요청의 URL과 일치하는 패턴이 있는지 검사
    # 7. 있다면 일차하는 패턴과 연결된 함수(view)를 실행
    #  7-1. settings모듈의 TEMPLATES속성 내의 DIRS목록에서
    #       blog/post_list.html파일의 내용을 가져옴
    #  7-2. 가져온 내용을 적절히 처리(렌더링, render()함수)하여 리턴
    # 8. 함수의 실행 결과(리턴값)를 브라우저로 다시 전달
    # HTTP 프로토콜로 텍스트 데이터 응답을 반환
    # return HttpResponse('Post List')
    # return HttpResponse('<html><body><h1>Post List</h1></body></html>')

    # 'blog/post_list.html'템플릿 파일을 이용해 HTTP프로토콜
    return render(request, 'blog/post_list.html')



로컬호스트는 고유주소

아이피 주소는 컴퓨터다라고 하면은

특정 아이피주소는 한대의 컴퓨터와 매칭.


한대의 컴퓨터에 여러개 프로그램이 돌아감.
이 컴퓨터에서 메일도 처리하고 htp도 처리하고.
많은 작업을 하고 싶을때

실행중인 프로그램들은 포트와 매핑

* IP주소
-> 1대의 컴퓨터와 매칭
   실행중이 프로그램들은 '포트'와 매핑
   
   
runserver는 서버 이름.

localhost:8000은 도메인인데 뒤에 /admin이라고 붙였다 하면 path에서 admin요청이 되는건데 

여기에 해당하지 안ㅇㅎ고 아무것도 없는 패턴  




오류는 둘 중에 하나

1. 바로 보여줌.
localhost:8000에서 보여줌


다른것은 없고 장고 모듈을 실행할 수 있는 코드들이 실행가능
쿼리셋은 이터러블한 객체라서 포문이 가능


--------------


템플릿 태그 (template tags)


없는 속성에 접근하면 오류가 안나고 렌더링이 아예 안됩니다.

{{  }}
안에는 파이썬에서 넣을 수 있는 내용은 거의 다 넣을 수 있음.

그냥 숫자를 전달해도 됨.



<p>{{ post.content|linebreaksbr }}</p>
문단마다 한줄 씩 띠우기

<p>{{ post.content|truncatewords:30 }}</p>
30 단어로 짜름.

truncatechar은 한 글자 단위로 짜르기 때문에 자연스럽지 않음.


/ 부터 시작하면 루트부터 시작한다고 그랬ㅈ


장고에서 정적파일을 제공하는 것은 일반적이니 뷰 루틴과 달라요.

해당 파일을 찾아서 리텉ㄴ.


함수에서 파일을 ㅊ자아서 리턴하는 것과 다른 결과에요.

정적파일을  리턴하는 것은 그냥 보내주면 끝이란 말이에요.

장고에서 예외사항을 내장으로 제공.

맨밑에 static_URL = '/static/'




장고걸스에서는 로드 css를 동적으로 함.
우리가 스태틱으로 가져오면 되겠다.

우리 스태틱은 쓰지 맙시다.
ddd로 쓰자. -> 그러면 html모든 부분을 전부다 바꿔야되니까.
동적으로

---------------

100에 해당하는 쿼리를 남겼을때 데이터베이스에 그 내용이 없다.

주석까지 렌더링해버리끼 때문에 html 주석을 달면 안됨.
-> 장고 렌더링 주석으로 달아야함.

--------------------

프로버전만 템플릿 주석처리가 먹힘.

URL: /post/3/

얘가 해석되는 과정이 지금

Path: /post/<int:pk>/

얘가 어떤 이름을 갖냐면

URL name: post-detail
			kwargs: {'pk': <int

----- 거꾸로 ----

URL name: post-list
Path:     list
URL:      localhost:8000/list


* url을 만드는 과정에서 아래는 제외가 됨.
view function: post_detail(request, pk)


URL:      localhost:8000/post/3/
Path:     post/<int:pk>/
URL name: post-detail
                kwargs: {'pk': <int value>}

---거꾸로---
URL name: post-list
Path:     list
URL:      localhost:8000/list

--거꾸로(post-detail)---
URL name: post-detail
          kwargs: {pk: <int value>}
Path:     post/<int:pk>/
URL:      localhost:8000/post/<int value>/


장고에서 정적파일을 다루는 것은 조금 다름.
일반 함수에서 리턴해주는 것과 다른 결과에요.

뷰에서 어떤 결과를 거치는게 아니라
우리가 가진 파일 데이터를 보내면 끝.
이런 상황을 내장으로 갖고 있는것.


--------------------------
* redirect 과정 설명
( 장고 내부에서 이뤄지는게 아니라 해당 주소를 바로 브라우져로 보내주면 브라우져는 다시 찾아가는 과정을 반복)

1. post_add페이지를 보여줌 (GET)
2. post_add페이지에서 글 작성 (POST요청)
3. post_add view에서 POST요청에 대한 처리 완료후, 브라우저에는 post-detail(pk=...)에 해당하는 주소로 redirect를 하도록 응답 (301 redirect, URL: /3)
4. 브라우저는 301 redirect코드를 갖는 HTTP response를 받고, 해당 URL로 GET 요청을 보냄
    (새로만든 Post의 pk가 3일때) 브라우저는 '/3'주소로 GET요청
5. '/3'주소로 온 요청은 다시 runserver -> Django코드 -> urls.py -> blog/urls.py -> def post_detail(request, pk)로 도착, post_detail뷰 처리가 완료된 post_detail.html의 내용을 응답 -> 브라우저는 해당 내용을 보여줌





GET 요청  -> 
POST 요청 -> 서버의 데이터를 변화시키는 작업




MVC패턴


Model
	데이터
View
	사용자가 보는 화면
Controller
	데이터를 사용자가 보는 화면에 전달해주기 위한 로직
	

Model -> models.py
View -> template
Controller -> views.py


Model
Template
View




* {#        템플릿 태그에서는 없는 것을 참조한다고 에러가 나지 않아요. #}


### Django 내부에는 UTC 시간이 저장됨.
세팅에서 어떻게 적용을 시켜도 데이터베이스에는 UTC로 들어가있음.



### render() 함수는 
request 객체를 첫번째 인수로 받고, template 이름을 두번째 인수로 받으며, context 사전형 객체를 세전째 선택적(optional) 인수로 받습니다. 인수로 지정된 context 로 표현된 template 의 HttpResponse 객체가 반환됩니다.








### migration에 대해서 말이 많음.

디비에 민감하면 장고를 쓰지도 않음.
시니어분들.asdkjlsj



### ./manage.py showmigrations
migration 내역을 볼 수 있음.



q 는 그냥 인스턴스.

만드는 방식이 다르죠.


q는 pk나 아이디도 다 되요.




queryset vs get

get에서 없는 것을 하면 에러가 남.

쿼리셋은 빈 리스트를 반환.

## get error
1 doesnotexist
2 두개 이상 존재할 때 꺼내려고 할 때




choice_set


Question 이름은 가능하다면
1관계인 모델의 소문자즐ㄹ 쓰게 되어 있음.

연결된 모델의 소문자로 바꾼다음에 _ set하면
접근할 수 ㅣ있는 통로가 되요.

* Question.objects
< ~~~~ .manager.Manager at ~~~~>

Question.objects가
퀘스쳔이라는 경로에 접근할 수 있는 매니져.


* q.choice_set
< ~~~~ .RelatedManager ~~~~~>

역으로 초이스 테이블에 접근할 수 있도록 하는 매니저는 
Related Manager

### form의 action은 입력이 안되있으면 현재페이지에 보냄.



### choice_set으로 create할 때는 question 값을 안 넣어주어도 됨.
q2.choice_set.create(choice_text='멜론',)
Choice.objects.create(question=q, choice_text='바나나')

### 장고에서 인스턴스가 몇개인지 궁금하면 .count()
q2.choice_set.count()

len(q2.choice_set.all()) 이렇게 쓰지마세요.
위에가 데이터베이스상에서 훨씬 빨리 움직입니다.


### 모든 장고뷰는 HttpResponse 객체나, 혹은 예외(exception)을 원합니다.


### 장고템플릿 언어 안에서는 호출하는게 전혀없음.
- 딕셔너리 키로 값 호출할 때도 .으로 그냥 붙여줌
- all() -> all

### {{ forloop.counter }}
- for문 안쪽에서 쓸 수 있는 특수변수
- 

### 라디오 버튼이 여러개가 있을 때 구분하는 방법이 name
- 라디오 버튼이 같으면 하나만 선택이 됨.

### 라디오버튼의 value
- POST 방식으로 서버에 보낼 때
- Get방식으로 


* 기사 한개가 있으면 기사 한개에서만 쓰는게 아니라 여러 사이트에 출력이 된다.


스타트업이면 어지간한것은 다  해결이 되고.



네임이 같아요.
다르지 않아요.
타입이 네임이 같을 때 한개만  선택가능
네임이 다르면 전부다 선택가능.

라디오 버튼이 여러개일때 그룹을 구분하는게 네임.

밸류는 서버쪽에서. 받을 대

겟으로 한다음 보내보면.
choice=2 라고 달리죠.
초이스의 pk값이 밸류로 들어감.

post로 하면 url이 포함안되고 보내지고 끝

초이스란 이름으로 뭔가 전달이 되요.
받아서 이걸 받아서 해야 되요.


----- 


-----

4장 제너릭뷰
함수에 좀 더 익숙해지면 할 것

5장
기존 50개의 코드를 모두 확인할 수 없음.

50개의 버튼이
눌렀을 때 적절하게 반응하는지 테스트 코드.

테스트용 도서. 과제

6장
스태틱 이미 한것

7장
관리자 사이트 커스터마이징 필요해지면 할 것



-------

