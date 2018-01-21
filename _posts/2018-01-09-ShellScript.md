# 01 ShellScript

---

####__TABLE__


>#####_01. Notetaking_
>#####_02. Storehouse_
>#####_03. Site_
>#####_04. Bookmark_
>#####_05. Question_

---






<br><br>
##01 Notetaking
<br>


> .으로 시작하는 폴더나 파일은 숨기는것으로 인식되서 안보임

<br>



> echo는 printf랑 같은 단어

<br>








<br><br>
##02 Storehouse
<br>


- __echo 'abc' > README.md__

 ```
 abc라는 내용을 README.md에 추가한다.
 echo 'abc' >> README.md 라고 하면
 README.md에 가장 마지막에 해당 내용을 추가.
 ```
<br>


- __rm -rf__

 ```
 디렉토리 안의 파일을 지울 때 사용.
 휴지통에 담기지 않고 완전삭제되니 주의.
 ```
 <br>


- __control + C__
 
  ```
  1) 작업중에 안되는게 있으면 모두 다 취소하고 나오는 명령어
  2) 명령어를 작성하고 실행하지 않을 때 다 지우는 대신 사용할 수도 있다. 
  ```
<br>


- __"~"는 사용자디렉토리, "."은 현재 디렉토리__  

<br>


 
- __mv Git-Practice git-practice__

 ```
 폴더이름을 바꾸는 손쉬운 방법
 git에서는 clone 또는 fetch 이후 폴더
 이름을 바꿀 수 있음.
 ```
 <br>

 
- __CLI 명령설명__

 ```
man :	명령에 대한 설명 출력  
clear : 화면을 깨끗이 지움  
ls :	디렉토리의 목록을 보여줌  
mkdir : 디렉토리를 생성함  
cd :	디렉토리의 위치를 바꿈  
rm :	파일 혹은 디렉토리를 지움  
cp :	파일 혹은 디렉토리를 복사  
mv :	파일의 이름을 변경하거나 옮길때 사용  
cat : 파일의 내용을 보여줌  
pwd : 현재의 위치를 출력
-m : 명령어의 그 다음 부분을 메시지로 읽어야 한다는 의미 
-a : application
touch : create 만드는 것을 의미. 
open . : 현재 폴더를 열어라
.. : (zschr에서만) 상위폴더로 이동

 ```
 <br>

 
 
 






<br><br>
##03 Sites
<br>

*본격 macOS에 개발 환경 구축하기*
[https://subicura.com/2017/11/22/mac-os-development-environment-setup.html](https://subicura.com/2017/11/22/mac-os-development-environment-setup.html)  
<br>


*터미널 명령어*  
[https://github.com/tadkim/infra/wiki/Mac-::-%ED%84%B0%EB%AF%B8%EB%84%90-%EB%AA%85%EB%A0%B9%EC%96%B4]
(https://github.com/tadkim/infra/wiki/Mac-::-%ED%84%B0%EB%AF%B8%EB%84%90-%EB%AA%85%EB%A0%B9%EC%96%B4)  
<br>


*Vim 명령어*
[https://github.com/Fastcampus-WPS-7th/Tips/blob/master/vim.md](https://github.com/Fastcampus-WPS-7th/Tips/blob/master/vim.md)



<br><br>
##04 Bookmark
<br>

###*01 oh-my-zsh의 플러그인*

- 명령어 하이라이팅 플러그인 zsh-syntax-highlighting
*zsh-syntax-highlighting*

git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

<br>

- 자동완성 플러그인 zsh-autosuggestions
 
*zsh-autosuggestions*   
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions

(vi ~/.zschr 이것은 안되는데 모르겠음.)

<br>

###*02 syntax hylight를 위한 작업*

vi ~/.vimrc 열어서 추가.

syntax on
set tabstop=4
set expandtab
set softtabstop=4
set shiftwidth=4
set number
set backspace=2
filetype indent on
colorscheme industry


<br>
###*03 Terminal에서 프로그램 실행 단축키 설정법*


shift + g : 가장 하단으로 이동

 92 # Example aliases
 93 # alias zshconfig="mate ~/.zshrc"
 94 # alias ohmyzsh="mate ~/.oh-my-zsh"
 95 alias atom="open -a /Applications/Atom.app/Contents/MacOS/Atom"
-- INSERT --
 95 alias atom="open -a /Applications/Atom.app/Contents/MacOS/Atom"


아톰주소를 위와 같이 ~/.vimrc의 가장 하단에 추가
/Applications/Atom.app/Contents/MacOS/Atom


zschr syntax highlighting
따로 정리해놓음.






<br><br>
##05 Question
<br>

1.  
2.  
3.  
4.  


