# 04 Python_Crawling

---

#### __TABLE__


>#####_01. Note_
>
>#####_02. Storehouse_
>#####_03. Site_
>#####_04. Bookmark_
>#####_05. Question_

---


1 create


### gitignore.io

macOS, Linux, Python, pycharm+all


HTTP / HTML과 다른것


2진 데이터와도 같아요.
해당 파일에 포맷으로 규칙에 의해서 나타나는 거거든요.

인터넷 랜선을 통해서 나타나는 것도 0101 인데
어떤 순서에 따라서 뭔지
규약을 정해야하는데
그 규약을 프로토콜이라고 불러요. 약속.

보내는쪽 받는 쪽이 같아야.
해석을 할 수 있어요.

HyperText Transfer Protocol

TCP와 UDP라는 더 낮은 규약 위에서 돌아가요.
HTTP요청은 클라이언트와 서버 사이에 이루어지는 요청 응답 프로토콜이다.
구글을 들어가면 요청이 가고 구글에서 응답이 오고 끝남.
# Djangogirls-Turorial
-----

맨날 브라우저에서 복사 붙여넣기하면 귄챃으니까
터미널에서 하죠.
쉘에서 하니까 

파이썬에서 HTTP를 하려면
검색에
python http library

standar library는 불편해서 안씀

보통 스탠다드보다는 리퀘스트를 많이 써요.
처음 써보는 써드파티 라이브러리.
다른 사람이 만든 라이브러리.

하나의 사이트가 구축이 될 정도면 기능이 굉ㅈ아히 많은거에요.
보통 퀵 스타트라고 대표적인 예제 하나가 사이트 처음 들어가면  있음.

복사 붙여넣기해서 되지는 않네요.
밑에 내려가면 

pip install requests
request아닙니다.


파이썬 우측에 빨간 경고 버튼


이 코드를 해석을 할 때
써드파티 패키지를 쓰고 있죠.
fc.python에 깔린건지 어디에 깔린건지 알 수 없어요.
이 코드에 올바른지에 대해서 판단할 수 있게해야줘야 하거든요.
이 파이참에다가 파이썬을 설ㅈ어해주는거에요.
이것도 제가 블로그를 만들어ㅗㅎ긴 햇어요.


preference


### htm
옛날옛날에는 html을 세글자로 표현하려고 htm이라고 한것.



### request.get("https~")로 해야함.

### https에서 s 가 없으면 보안이 전혀 안됨.

###why?
s는 보안의 의미.
s가 없으면 입력한 데이터가 전달되는 과정에서 그대로 다 열어볼 수 있다는 의미.


### alt + shift + e
해당 부분





# pyenv 가상 설정 과정

### 1) pyenv virtualenv 3.6.4 fc-crawler
fc-crawler라는 이름의 3.6.4 버전의 가상환경을 만듦


### 2) pyenv local fc-crawler
해당 폴더에 fc-crawler 가상환경을 적용시킴.


### 1) pyenv version 으로 가상환경 확인
> fc-crawler (set by /Users/smallbee/projects/crawler/.python-version)

### 2) python --version으로 가상환경 적용확인
Python 3.6.4


### 3) pip list
### 4) pip install requests




### PIP
파이썬의 Brew같은놈. 패키지 관리자.
거의 다 이걸로 패키지를 씀
지금까지는 requests 한번 깔아봄


### gst (for .gitignore)
### git add -A
### git commit -m 'first commit'
### git remote add origin https://github.com/smallbee3/Crawler.git
### git push origin master


-----------------------

pip version으로 가상환경 확인하고.

### pip install beautifulsoup4 lxml

깔기.

lxml까지 같이


파이썬에서 html을 해서갈때 쓰는 라이브러리

lxml

파이썬 안에 html파써가 있음.
뷰티플숩을 그냥 쓰면 느림.

그래서 뷰티플숩을 쓸 때 뭘쓸거다가 있음.



지금은 잘 안써요.


관대하지 않다. 구조가 조금이라도 이상하면 못찾음.

lxml은 알아서 수정해서 찾아준다.






-------------

os.getcwd 현재위치

os.path.abspath(   )


absolutepath는 이 경로를 절대경로로 바꿔줘요.

예를들어 __name__을 하면은 이 모듈이 




### 모듈단위 변수는 대문자


### Refactor Rename을 저는 f2로 해놔요.
                                                                                                                             

### .gitignore Custom
/data
-> root 폴더를 기준으로 data폴더 제외

/라고 적으면 가장 루트폴더를 기준으로 데이터 폴더만 제외


# True를 비교하고 싶을 때!
### A is True  또는 A (라고만 적음)


A == True 는 안됨.

== 는 값을 비교하고

is 는 아이디 값을 비교 (메모리에 있는 객체 자체를 비교, 완전히 같은 객체여야만 함.)
v