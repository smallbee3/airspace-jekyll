# 보충수업 1/24

### 정규표현식


정규표현식은 잘 안쓰거든요.
크롤링은 어떤 프로젝트에 따라 쓸 수도 있고
웹이 어떻게 통신하는지 이해할 수...


장고는 웹 프레임워크.
파이썬으로 웹으로 뭘 해보려고하는데 가장 적합한게 웹 크롤링.

HTML 모르면 헬
알아서 파싱해주는 패키지.

-------------
그래서 필요한게

1. 클래스를 제일 잘 다뤄야함.
2. 함수.
3. 다중상속, 키워드인자 다쓰고요
   왜냐면 프레임워크 대체제를 잔뜩 만들어놓고 연결해놓는 거라서
   근데 동적바인딩처럼 너무 깊게 들어간것은. 


사실 프레임 워크라는게 
수업시간에는 정말 기초만 알려드림.

----------------

배포가 제일 어렵습니다.
서버사이드의 꽃.
배포가 제일 재미있습니다.

배포는 왜 어렵나면.
그때는 이론을 많이 알아야되요.

웹 / 서버통신 ..
이런 개념들을 알아야되서.
뭔가 만들 수는 있어요.

하나만 만지면 다 변하기 때문에..

-----------------

통신. 
통신 전반..

소켓통신은 통신의 일부잖아요.

HTTP TCCIP 이런 용어와 어떻게 이루어지는지와 개념.

------------------

박사님.
"파이썬 코딩의 기술"
"이펙티브 시리즈"

------------------


### response & requests

파일 형식 중에 하나인데 HTML도 파일인데

예를 볼려면 이 주소로 와야겠죠.

www.melon.com/index.html이라는 파일을 달라고 요청을 해서 받은 파일. 이게 response라는 변수 이름을 명시적으로 지어줌.

### requests.get()
여기서 get 
통신하는 방법 중에 메소드가 있어요. 

4천왕

get : 
post : 데이터베이스에 영향을 주는 요청을 보낼 때.
put : 
delete : 

이게 가장 많이스는 http 통신 메소드.


response = requests.get / put / post / delete 

print(response)

200이 정상.
200 : ok

200이 말고 다른것이 나오면 비정상

404 not found

404는 response객체인데 안에 아무것도 없을 거에요.

--------

ex) 멜론 차트에서 멜론 top100을 클릭하면
엄청 많은게 같이 와요.



---------

여기 request와 response는 둘다 모두 헤더와 바디를 가짐.
헤더에는 요청의 정보
바디에는 주고 받은 파일이 들어감.


200 404같은 것은 헤더 파일에 들어잇음.


헤더를 보시면 

Request URL:http://www.melon.com/chart/index.htm
Request Method:GET
Status Code:200 OK
Remote Address:211.234.237.13:80
Referrer Policy:no-referrer-when-downgrade


제너럴.
리스판스와 리퀘스트와 공통 헤드


아무튼 사람이 하는 것 대신에 해주는것.


안에 바디를 확인해보려면 
콘텐트

print(response.content)
하면 괴상한 문자가 잔뜩 써저있어요.
html이거든요.

여기보시면

b" 제일앞에 스트링이라고 되어있어요.
b"
바이트 스트링이라는 거에요.
바이트 스트링.
컨텐트는 항상 바이트로 보여줘요.
타입을 해보면 바이트가 나오겠죠.

print(type(response.content))
<class 'bytes'>


response.text
>> string으로 돌려줘요.

\t\n

바이트 자료형으로 보면 다 튀어나와요.
텍스트로 보면 공백으로 보이죠.

크롤링하려면 문자열로 바꿔야될거에요.
정규표현식은 문자열 매치.


-----------------------

바이트로 가져와도 
라이트 바이트 배웠잖아요.


Q. 왜 어제 강사님이 get 대신에 파일을 저장하라고 한것?

서버가 부하가 걸릴 수도 있어서요. 연속으로 계속보내면
힘들어하겠죠
비정상적인 요처잉 계속들어오면. ip를 차단을 시킬 수 있어요.
한번 가져온거를 파일로 지정하고 연습.



열은 객체를 f로 가지고 있겠다.

예를 들어 컨텐트를 가져왔는데 write text를 해라 그러면 오류가 나겠죠.

with open("melon.html", "wb") as f:
	f.write(response.content)

저희가 확장자를 html로 했죠. 그래서 저렇게 보여요.

그림같은 거는 다 바이트로 가져와서.
인코딩해주고 그래야되요.
음악파일이나 미디어파일.

어쨌거나 바이트로 통신을 해주기 때문에..


기본값이 wt



예를들어 그림이 오면 
source = open("그림", rb).read()

----------

일단 re.compile(패턴을 써주면 )

re가 파이썬에서 정규표현식을 동작하게 해주는 패키지거든요.
그 패키지의 인스턴스로 하나 뱉어줘요.


print(type(p))
이게 re의 객체.

패턴객체를 만들때 옵션을 줄 수 있어요.

p = re.compile(r'  ', re.DOTALL)

						=
						
						re.S)
						


Match Object가 매치라는 결과를 보여주는 오브젝트
span=(num1, num2)
     시작위치  끝위치


이렇게 출력가능

print(source[95186:95424])
라고 하면 직접 볼 수 있음.

내용을 보려면 .group을 하면 되요.

처음것만 보려고
break 걸었습니다.
 
 
iter가 뱉은 objet이기 때문에 

예를들어 
group(1)
group(2)
group(3)
에서 group(3)이 *? 이면 이것만 엄청 나옴. 


------------


파이참에서

빈줄로 코드로 해놓고

하면 뭐가 떠요.

[pep8]
코딩 스타일 가이드

no newline at end of file.

파이썬의 철학. 깔끔하게.

가이드라인을 써놓은게 pep8

"줄이 너무 길다."
"아래에 빈줄을 넣어라"


듣기로는 장고 신택스하이라이팅인가 해준데요.



----------------



빈리스트 생성할때 pep가 이렇게 말 안하고
비어있는 리스트하면

artist_list = []
위보다 아래로.
artist_list = list()

왜 그런지 모르겠는데 명시적이라서?


하나씩 뽑아와서 리스트로 묶어주는 애 : zip

zip object를 하나 뱉어용.

이게 뭐냐. 이걸 리스트로 바꿔주면 되거든요.

print(list(zip(lista, listb, listc)))

순서대로 똑같이 묶어줌.




이게 왜냐면
얘가 밖에 있어서 그래요.
빈 딕셔너리가 하나 생기고
for 문을 생겨서 계속 갱신을 하는 거죠.

이럴때는 얘를 새로 돌 때 새로 딕셔너리를 하나 만들어서 넣어주면 되겠죠.


이런게 있구나 기억해서 그걸 찾아보면 됨.


문자열이나 리스타나 딕셔너리는 변환이 가능한 객체거든요.
그래서 원래 있던게 사라지지 않고 똑같은 것을 내용을 바꿀 수 있어요.

그래서 바꾸기 때문에 

안에 딕셔너리 들이 같은 id 값을 가리키기 때문에.
다른 객체이지만 같은 id를 가리킴.

---------------------------------


정규표현식 괜찮은 문제사이트.



솔직히 정규표현식보다는 클래스나 함수 만드는 것 연습하는게 도움이 될 것 같아요.



질문 엿듣기

Q. 아이디가 같으면 같은 객체인가요?

ok

Q. 그럼 아까 리스트 안에 딕셔너리가 여러개 잇었지만 다 같은 객체지요?

ok




[.]

Problem 1: Matching a decimal numbers
Task	Text	 
Match	3.14529	Success
Match	-255.34	Success
Match	128	Success
Match	1.9e10	Success
Match	123,340.00	Success
Skip	720p
.*[^p]$


Problem 2: Matching phone numbers
apture	415-555-1234	415	Failed
Capture	650-555-2345	650	Failed
Capture	(416)555-3456	416	Failed
Capture	202 555 4567	202	Failed
Capture	4035555678	403	Failed
Capture	1 416 555 9292
(\d{3})


Problem 3: Matching emails
(.*?)[+]|(.*?)@
1/28 (.*?)[+|@]


Problem 4: Matching HTML
<(\w*?)\W
1/28 <(\w*?)[>|\s]


Problem 5: Matching specific filenames
(.*?)[.](png|jpg|gif)$

1/28 (.*?)\.(png|jpg|gif)$

Problem 6: Trimming whitespace from start and end of line
     \s*(.*?\s.*?\s.*?\s.*)
1/28 \s*(\w*?\s\w*?\s\w*?\s.*)


Problem 7: Extracting information from a log file
.*?List[.](.*?)[(](.*?):(\d*?)[)]


Problem 8: Parsing and extracting data from a URL
(.*?)://(.*?)[:|/]
(.*?)://(.*?)[:|/](\d*)




나중에 장고에서
정규표현식은 거의 url만 씀

---------------------------------------------


왜 파이썬?
다른 프레임워크로 웹 프로그래밍을 해야하는케이스?
보통은 자기기술에 맞춰서.


자바는 중견기업.
안정성 있고 빠르고.

우리나라 공인 웹 프레임워크.




