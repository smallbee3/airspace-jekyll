# 00 MacSetting
### (Jeykll & BLOG) 

---


> bundle install에서 충돌나도 bundle update 그냥 하면 됨.

<br>



> 127.0.0.1:4000은 포트번호


> config.yaml



제목에 규칙존재
vim 연도네자리-달두자리-일두자리-제목


정적 웹사이트를 
github를 백엔드로 해서 만들어주는 서비스


유저사이트는 각 계정마다 하나.


프로젝트 사이트는 용량제한이 1g있음.


Github에서는 웬만하면 수정하지말고. 

vim _config.yml



<br><br>
##04 Bookmark
<br>


#####rbenv환경에서 Jekyll 블로그 생성하고 GitHub Pages에 배포하기
[https://lhy.kr/create-jekyll-blog-using-rbenv-and-github-pages](https://lhy.kr/create-jekyll-blog-using-rbenv-and-github-pages)


#####Jekyll 블로그 시작하기 - Ubuntu 환경
[https://nachwon.github.io/etc/2018/01/17/jekyllblog.html](https://nachwon.github.io/etc/2018/01/17/jekyllblog.html)


---



###blog 만들기

방법 1 clone

1. blog 폴더생성
2. git init로 초기화
3. git clone https://github.com/smallbee3/smallbee3.github.io.git
4. git remote add blog https://github.com/smallbee3/smallbee3.github.io.git
5. vim _config.yml에서 수정
6. commit
7. git push blog master



방법 2 pull (fetch/merge)

1. blog 폴더생성
2. git init으로 초기화
3. git remote add blog https://github.com/smallbee3/smallbee3.github.io.git
4. (HEAD는 master에 있음)
   git fetch blog
   git merge blog/master
or
   git pull blog master 

5. git push blog master



----


### python 설정관련


1) pyenv 설치 영문 매뉴얼
[https://github.com/pyenv/pyenv/blob/master/README.md](https://github.com/pyenv/pyenv/blob/master/README.md)

1. pyenv와 pyenv-virtualenv 설치

2. 그 다음 vim ~/.zshrc에서

export PYENV_ROOT=/usr/local/var/pyenv
if which pyenv > /dev/null; then eval "$(pyenv init -)"; fi
if which pyenv-virtualenv-init > /dev/null; then eval "$(pyenv virtualenv-init -)"; fi

그 이후 (Mac유저는)
brew upgrade pyenv 명령어.

pyenv --version 로 버전확인
수업시간에는 pyenv 1.2.1로 설치


3. *brew install readline xz 로 설치를 안하면 문제가 발생하는데 위의 영문 매뉴얼에서는 아주 조그맣게 숨겨놓음.*


4. 이후 pyenv install list로 설치된 버전 확인.
현재 없는 3.6.4 버전 설치

수업시간에는
pyenv install 3.6.4로 설치 후 진행함


5. (pyenv 시스템 기본 버전은 건드렸다 문제되면 os 전체를 들어내야함.)
pyenv version 하면
  ~ pyenv version
system (set by /usr/local/var/pyenv/version)

pyenv global 3.6.4

➜  ~ python --version
Python 2.7.10

창 닫았다 키면

➜  ~ python --version
Python 3.6.4


6. 경로 설정은 

7 pip list 치면 
pip (9.0.1)
setuptools (28.8.0)

빨간색은 무시

7. pyenv virtualenv 3.6.4 fc-python
이 폴더 안에는 가상환경 3.6.4를 쓰고 이 환경이름이 fc-python이다.

8. pyenv local fc-python
만든 가상환경을 적용을 해줌.



2) iPython
내용을 편하게 볼 수 있도록.
이것만 설치하는게 아니라 몇개 더 설치.

pip install ipython jupyter

이것은 컴퓨터에 까는게 아니라 fc-python이라는 가상환경에 설치하는 것.



----

ctrl + enter : 입력 결과 출력.

art + enter :  다음창



