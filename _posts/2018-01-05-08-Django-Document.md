# 08 Django Document


#### foreign key에는 무조건 _id 가 들어감

- 컬럼 == field

- api : 
python 이랑 연결시켜주는 방법.
"이 모든 것을 통해 Django는 자동으로 생성 된 데이터베이스 액세스 API를 제공합니다."

DB - API
Database - python-sqlite3 - python - ORM -  sql


#### 외부에서 이렇게하면 쉽게 쓸 수 있어 하는게 api.
데이터베이스에 접근하는 쉬운 기능.

* PK - wekipedia
관계형데이터베이스에서 레코드의 식별자로 이용하기에 가장 적합한 것을 테이블마다 한 설계자에 의해 정의된 후보키를 말함.
-> pk는 정렬이 되어있기 때문에 빨리 찾을 수 있음.

* 필드는 모델의 가장 중요한 부분이자 유일한 필수 부분
- 클래스 속성임, 인스턴스 속성이 아님.

* html5 부터 input자체에 max-length를 정할 수 있고, 그것을 장고에서도 똑같이 사용. 
-> 데이터베이스에 넣기 전에 프론트 단에서부터 문제가 발생하게 되어 있음. 


### 커스텀 필드
전화번호 필드나 주소필드같이 없는 필드는 커스텀필드로 만들 수 있음.
-> 어떤 데이터를 입력했을 때 이것이 전화번호 인지 일일이 검사하는 것이 아니라 필드자체에다가 검사 모듈을 넣어서 양식이 틀려요 하고 안받을 수도 있는 것.  
-> 일반 캐릭터 필드를 세개 합쳐서.


* 데이터베이스와 관련
null - 값이 없는 것
blank - 빈값

* 파이썬으로 따지면
null 은 none
blank 는 빈 문자열 ''

* blank는 유효성 검사와 관련이 있음.

* 장고에서는 데이터베이스 차원에서 넌은 허용을 하지 않기 대문에. 접속한 사람은 500 서버에러가 발생,

* 데이터 베이스에서 null을 허용하지 않기 때문.
빈 값을 들어갈 수 있는 필드는 굉장히 제한.
blank=True는 그냥 빈값.

* 폼에서 만 허용하는가는 데이터베이스와는 관계가 없음.

* blank=True 폼에서 빈값
null=true는 데이터베이스에서 빈값.
-> blank=True할거면 null=True도 해주어야함.

* blank=True는 pmmm/pmm을 안해주어도 되지만
  null=True를 하면 pmmm/pmm을 무조건 해야된다.
  -> 왜냐면 blank 설정은 장고내에서 해당 필드에 대한 폼을 생서할 때 required를 빼주는 거고, null은 데이터베이스에서 null값을 받겠다는 변경사항이 있기때문.

* 장고에서는 가능하면 캐릭터필드는 null을 쓰지 않는 것을 추천함.
null=True하면 서버에서만 허용. 프론트단에서는 못함.

* 데이터베이스에서 일반적으로 CharField는 빈값을 허용을 함.


* choices
데이터베이스에서 공간을 엄청나게 아낄 수 있음
ex) 한글 같은 것 저장하고 검색하려면 엄청 걸림

* get__FIELD명__display() 
해당 속성의 choices가 있을경우에는 뒷 부분에 해당하는 것을 가져온다.

* help text 가능하면 적어주면 좋음.

* pk키는 읽기전용
만약 기존 개체의 기본 키 값을 변경한 다음 저장하면 새 개체가 이전 개체와 함께 만들어짐.
pk가 파이썬이 아니라 데이터 베이스 차원에서 복사가 됨.
p.pk = 100으로 바꿔버리면 객체 복사가 되어서 들어감.

* unique = 고유해야함.

* 필드에 무언가 추가되었거나 하면 make migration 해야함.



### verbose_name은 DB에는 영향이 없이 장고에서만 보임.
ForeignKey, ManyToManyField and OneToOneField require the first argument to be a model class, so use the verbose_name keyword argument:
왜냐면 첫번째 인자가 어떤 것을 가리킬지에 대해서 정하고 있기때문에 (+그 인자가 텍스트로 주어지는 경우도 많아서 구분이 안감)



### 관계형 데이터베이스의 힘은 테이블을 연관시키는 것
* 속도는 키 밸류형 데이터베이스가 빠르지만, 연결관계를 정의하기 힘듦.
관계형 데이터베이스는 저장 용량을 아끼는데 최적화.
왜냐하면 15년 전까지만 해도 하드디스크가 1기가만되었기때문.

* 가능하면 공간을 절약하는게 중요했음. 지금은 속도가 우선이 되서 키밸류형 데이터베이스가 나오게 된것.

* 장고는 세가지 모델을 지원.
다대일, 다대다, 일대일
-> 이 세개를 벗어나서 만드는 것은.
일반적인 서비스에서는 필요가 없었음.



### 1) m-t-o : django.db.models.ForeignKey. 라는 클래스 속성을 이용.

- foreignkey는 위치인수가 필요. 

### m-t-o + recursive
: 자기 자신을 다시 참조하는 것.
한쪽이 자기자신이고 다른쪽도 자기 자신.
자기가 자기 자신을 참조하는데 다대일 관계.


ex) person - teacher
    student - tutor

* 'self'로 문자열을 쓰라고 되어있음. 그냥 규약임.
self는 아무 의미가 없음. self를 직접 참조할 수 있는것은 인스턴스 메소드 안에서임.
자기이름 Person 이렇게 써도 안됨.


#### 질문 엿듣기1
pc.teacher = lhy <- 왜 lhy.name으로 안했는지.

-> 다음문서인데, ForeignKey나 ManyToMany 필드에 값을 저장하고 싶다하면 ~~
해당 필드에 객체를 지정하는 방법을 씀~~
"Saving ForeignKey and ManyToManyField fields"

아마 그리고 객체를 넣는 이 방식밖에 안됨.



### 3) m-t-m

1) person <-> post 좋아요
: 좋아요에 누가 눌렀는지 목록 나오고
내가 좋아요한 글도 목록으로 나오고

: person이 post 여러개에 대해서 좋아요 를 누를수 있고
post는 누가 좋아요 눌렀는지에 person목록을 알 수 있음.


* ManyToManyField는 어느쪽에다가 해도 상관없지만(왜냐면 어느쪽이 관계가 더 우선이다가 없음) 피자에다 토핑스하는게 토핑스에 피자 하는 것보다 더 주된 의미.
반대쪽에서는 역참조를 해야함.

* ManyToMany에 추가하거나 삭제하는 동작의 경우 데이터베이스에 save하지 않아도 자동으로 변경이 됨.
-> 왜냐하면 새로운 데이터가 생성되는게 아니라 그냥 연결만 시키는 것이기 때문...

* ManyToManyField는 한 클래스에 여러개 있을 수 있음.
class Shop
- drink
- pizza
  ...


### M-T-M + 추가정보
-> 중간자 모델(or 중개 모델)을 설정해야됨.
-> 자동으로 생성되는 pizza_toppings 안생김.


소스모델: ManyToManyField를 정의한 곳 
대상모델: 타겟모델

중간자모델 : foreignkey 2개 정의(소스모델에 대한 외래키가 하나여야만 함) + 추가정보

ex1) 그룹 <-> 가수
: 년도에 따라 이 그룹 저그룹 속한게 계속 바뀜...

ex2) 클럽 <-> 선수
: 년도에 따라 이 클럽 저 클럽.


* add는 안되고 -> 테이블의 row에 해당하는 부분을 직접 만들어주어야함.


### many_to_many + recursive

ex) 페이스북이나 트위터에서 '친구관계'
내가 친구 여러명 가질 수 있고 친구도 친구를 여러명 가질 수 있음.



#### 질문 엿듣기2
DB에서 검사한 데이터를 넣어주고 꺼내는 것이
꺼내고 나서 파이썬으로 검사하는것보다 훨씬 빠름.



#### 시간 예쁘게 표현

* local타임이 좀 더 직관적
datetime.strftime(timezone.localtime(self.created_date), '%Y.%m.%d')

== 

datetime.strftime( timezone.make_naive(self.created_date), '%Y.%m.%d')


->  tzinfo값으로 Asia/Seoul을 가짐.

----------------------------------

01/06 Tuesday

### shell exit when?
장고 내부 코드의 변화면 shell에서 exit
데이터베이스 내부의 변화면 no exit
장고 내부 코드는 이미 불러온 상태임, exit을 한다고 db에 변화는 없음


* MTM에서 복수형으로 + s 붙일것
ex) 

* self.py에서 튜플에 , 안쓰면 에러
-> 멘붕



* Facebook
-> 자기 자신을 상대로  ManyToMany를 맺을 수 있는 가장 일반적인 모델.
예를들면 누가 친구를 추가하고 그사람이 수락하면 서로 친구관계가 됨.
내가 니 친구면 니도 내 친구다.

* Facebook : symemetrical
  DB 테이블을 보면 a->b했는데 b->a도 되있음
* Instagram : symmetrical=False
  DB 테이블을 보면 a->b만 되어있음


* 트위터
팔로우개념. 서로 대칭적인 관계


* ManyToMany 의 기본값은 페이스북처럼 symmetrical

* 자기 자신을 참조할 때는 related_name 안만듦.


### no such table: ~~~
아 내가 migration을 안했구나.
-> 모델에 대한 정보는 다 들어와있는데 DB정보만 없는 것.


[ManyToManyField.symmetrical]

When Django processes this model, it identifies that it has a ManyToManyField on itself, and as a result, it doesn’t add a person_set attribute to the Person class. Instead, the ManyToManyField is assumed to be symmetrical – that is, if I am your friend, then you are my friend.


팔로우 하면 저사람을 팔로우 하는 것.
내가 팔로잉 하는 것.


A와 B가 각각 인스타그램 계정이 있음

A가 B의 소식을 받고 싶다
	A가 B를 '팔로우'함



* from user : 내가 했으면
* to user : 누군가 나에게 했으면

* symmetrical + intermediate 모델의 경우 (ex Relation) 에서 block이 아닌 friend 목록만을 갖고 싶으면 relations(MTM Field Key)가 아니라 Realation으로 가야하기 때문에 이를 위해서 설정한 역참조 이름 related_name을 이용해야 함
ex) relations_by_from_user

-> relations 와 Relation은 관련없음;;;;


### values()
all()대신에 이것쓰면 쿼리셋이 딕셔너리가 되서 출력됨
q = TwitterUser.objects.values()


### values_list : 쿼리셋api

.values_list('뽑을값', flat=True)

* values_list() -> 키가 없고 value만 나옴
[(1, '이한영'), (2, '박보영'), ...]


* values_list('pk') -> pk만 나옴
[(1,), (2,), (3,), (4, )]

 * values_list('pk', 'name') -> 다나옴, 위에 아무것도 안준 값과 같음
 [(1, '이한영'), (2, '박보영'), ...]

* 뽑을 요소가 한개일때 옵션 flat=True를 주면 튜플이 아닌 하나의 리스트 안애 넣어줍니다.


### .filter(pk__in=리스트)
TwitterUser.objects.filter(pk__in=[1,2,3])
-> 뒤에온 리스트 목록의 'pk'에 해당하는 값을 가져옴

--------------------------------

clear 메소드는 쓸 수 있음.

지우고서 추가할 필요 없잖아요. 

-------------------------------

primary 값 을 바꾸면 객체가 복사.


* shell_plus
django_extensions



* apps name을 바꾸면 apps.py 안에 내용도 수정해야되고 할게 좀 많음.



### FOREIGN KEY constraint failed
-> .save()로 해야됨

### 역참조 related_name으로 할 때 from_user 써줘도 됨
self로 쓰면?


### 테이블 전체에 데이터를 지정하고 싶을 때는 
class Meta: 에다 지정을 함.

* order_by로 한번 씀
* unique_together = (

)
-> 여러개를 한번에 묶은 것을 제약조건으로 삼는 것.

* unique together 속성을 테이블에 줄 때 기존 중복된 데이터가 이미 있을 때는 migration했을 대 db에서 무결성에서 에러가 남.


You are trying to add the field 'created_date' with 'auto_now_add=True' to relation without a default; the database needs something to populate existing rows.

 1) Provide a one-off default now (will be set on all existing rows)
 2) Quit, and let me add a default in models.py
Select an option:
-> 이미 값이 존재할 수도 있는 데이터베이스에 새로운 필드를 추가했는데 디폴트 값이 없음.


u1 디폴트 값이 없는데 어떻게 할 꺼냐?
-> 기존에 있던 데이터들에는 null이 허용이 안되니까 그 이전의 데이터들에는 어떤 값을 넣을꺼냐?

* but if null=True가 있었으면 이 사단이 아예 안낫음;;

1번 지금 이미 존재하던 필드에다가 그 내용을 쓴다는 거에요.
2번 나가서 니가 디폴트 값을 기록해라.
1번 -> 쓸쑤있는 값이 디폴트 timezone.now로 하면 그냥 지금 시간을 넣을 수 있다.
엔터누르면 주어진 디폴트값이 들어감. 

* .Date(auto_now_add=True) 는 처음으로 만들어지는 순간에만 시간을 필드에 기록해줌

* auto_now=True -> 객체가 업데이트, 수정이 될 때마다.



* 중개모델을 통할 때는 삼총사 add(), create(), set() 안됨, 그런데 clear()메소드는 쓸 수 있음.

* add(), create(), set() 


* set
기존에 데이터가 있어도 새로 얘내들만 넣어주는 것.
지우고서 추가하는 동작을 셋으로한번에 
ex)
beatles.members.set([john, paul, ringo, george])


* clear() 
다대다로 연결된 모델 사이에서 그 관계를 전부다 지우고 싶다.


Why? You can’t just create a relationship between a Person and a Group - you need to specify all the detail for the relationship required by the Membership model. The simple add, create and assignment calls don’t provide a way to specify this extra detail. As a result, they are disabled for many-to-many relationships that use an intermediate model. The only way to create this type of relationship is to create instances of the intermediate model.

개인과 그룹사이의 관계 -> 실습한 것중에 Intermediate
Post User PostLike
Post와 User사이의 관계를 얘내만으로 만들 수 없어요. 왜냐면 Post_like를 통해서 created_date를 따로 넣어주어야 되기 때문에.


### One-To_One

객체가 다른 객체를 확장할 때 많이 씀.

예전에는 장고에 내장된 User모델, 을 쓰고 그 외의 정보를 넣고 싶으면 걔를 원천필드를 삼아서 확장하는 필드를 써야되었음.
장고 1.5인가부터는 유저모델을 바꿀 수 있게 되었음.

기존 모델을 그대로 두고 확장하고 싶을 때 씀.


### verbose_name
안에는 그대로 있고 바깥에서의 이름만 바꿔줌. 


### O-T-O는 셋이 아님
p1.restaurant_set -> p1.restaurant
서로 1:1로 밖에 연결이 안되니깐.


### hasattr
어떤 객체가 해당 속성을 가지고 있는지 검사하는 것.

유사한기능이
== 
>>> from django.core.exceptions import ObjectDoesNotExist
>>> try:
>>>     p2.restaurant
>>> except ObjectDoesNotExist:
>>>     print("There is no restaurant here.")
There is no restaurant here.

''.split

hasattr('', 'split') -> 문자열객체가 split이라는 속성이 있니? 라고 물어본것.
>>> True

hasattr(p2, 'restaurant') -> 문자열로 물어봐야되요

hasattr 아니면 getattr/setattr이 존재하는 이유가 프로그램이 동작할때 동적으로 어떤 값을 꺼내오거나 주어주기 위해서임.
*동적
동적이라는 말은 실제 할당되지 않은 객체의 값을 사용하는 것이 잖아요.

p2.restaurant란 말과는 전혀다른 것.
restaurant란 속성을 바로 참조한다. 
hasattr은
이런 이름의 속성이 있는지 물어보는 것

### O-T-O

!!@
'''place값이 pk잖아요. -> Place가 가지는 pk와 같은 pk를 가지게 되는 거죠. 테이블은 다르지만. 이렇게 하면 무슨 장점이 있냐면 Restaurant에서 Place를 참조할때 굳이 Place의 pk가 뭐지 하고 갖고 있을 필요가 없음. 자기 place에 해당하는 pk를 찾아가면 그게 그냥 Place의 pk가 되는 거죠.'''
!!@

r = Restaurant(place=p1, serves_hot_dogs=True, serves_pizza=False)
>>> r.save()

------------------------------------

>>> r.place is p1
True

>>> r.place = p2
>>> r.save()
>>> p2.restaurant
<Restaurant: Ace Hardware the restaurant>
>>> r.place
<Place: Ace Hardware the place>

 p1의 레스토랑은 어딘가요?
 p1에 레스토랑이 있을까요 없을까요?
 
>>> p1.restaurant
>>> p2.restaurant
 
 둘다 있어요.
 
 왜냐면 primary키의 값을 바꾸고 저장하면 db상에서 객체가 복사된다고 그랬죠.
 그래서 db상에서 