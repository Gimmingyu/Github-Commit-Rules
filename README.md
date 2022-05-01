
# Github-Commit-Rules
8 rules for making awesome commit message

공부 출처: https://djkeh.github.io/articles/How-to-write-a-git-commit-message-kor/

# 커밋 메세지를 올바르게 작성하기 위한 8가지 유의사항.

~~~
커밋을 할 때마다 깃허브 커밋 메세지를 작성하지만, 혼자 공부하거나 진행하는 프로젝트를 넘어서
다른 사람들과 협업을 할 때 좋은 커밋 메세지는 코드 유지보수에도 도움이 되고 여러 방면에서 프로젝트 관리와 협업에 도움이 된다.
~~~

---------------------------------------------------------------
> 이하 약속은 commit message를 English로 작성하는 경우에 최적화 되어있다. 
---------------------------------------------------------------

<br />

### 1. 제목과 본문을 한줄 띄워 분리하기.

제목과 본문 사이에 공백 한 줄을 추가하는 것은 생각보다 상당히 가독성을 높여준다. 
git commit의 man 페이지를 참조하면, 50자 이내의 요약 문장과 빈 줄 하나, 그리고 설명문으로 구성하면 좋다는 내용이 있다.
강제사항은 아니지만, 자잘한 커밋이 아닌 잘 갖춰진 커밋 메세지를 작성할 때에는 이 규칙을 따르는 것이 좋을 것 같다.
이를테면 다음과 같다.

<br />

~~~
Derezz the master control program

MCP turned out to be evil and had become intent on world domination.
This commit throws Tron's disc into MCP (causing its deresolution)
and turns it back into a chess game.
~~~

<br />

git log --oneline을 사용하면 이 커밋 메세지를 다음과 같이 보여준다. 

<br />

~~~
$ git log --oneline
42e769 Derezz the master control program
~~~

<br />

깔끔하게 제목만 나오는 모습이다. git short log를 사용해서 확인하게 되면 더욱 가독성이 올라간 모습을 볼 수 있다. 

<br />

~~~
$ git shortlog
Kevin Flynn (1):
    Derezz the master control program

Alan Bradley (1):
    Introduce security program "Tron"

Ed Dillinger (3):
    Rename chess program to "MCP"
    Modify chess program
    Upgrade chess program

Walter Gibbs (1):
    Introduce protoype chess program
~~~

<br />

### 2. 제목은 영문기준 50자 이내로

제목이 50자 이내라는 기준은 굉장히 널널하다. 우리는 커밋의 제목을 어떻게 하면 더 직관적이고 파악하기 쉽게 작성할 지
고민할 필요가 있다. 그러나 너무 성의없는 제목보다는, 제목만 보고도 무엇에 관한 커밋인지 알 수 있다면 더 좋겠다.

<br />

### 3. 제목 첫글자를 대문자로

문법의 문제이다. 첫 글자가 대문자인 것은 당연하다. 나도 커밋을 할 때 귀찮아서 대충 쓰는 경우가 많았는데, 
사소한 부분이지만 지켜보도록 하자. 

<br />

### 4. 제목 끝에 . 금지

그렇다고 한다.

<br />

### 5. 제목은 ***명령조***로

첫 단어를 동사원형으로 써서 git의 Built-in Convention을 그대로 따라주자. 
git에서는 "Merge pull request #123 from someuser/somebranch" 와 같이 
메세지를 보여주는데, 이와 같은 규칙을을 따라줌으로서 나의 커밋 메세지도 자연스레 녹아들어 
잘 어울릴뿐더러 log를 찍어볼 때도 어떤 변경점이 있었는 지 알아보기 더욱 쉽다. 
예시는 다음과 같다. 

<br />

~~~
Good Example
(If applied, this commit will) Refactor subsystem X for readability
(If applied, this commit will) Update getting started documentation
(If applied, this commit will) Remove deprecated methods
(If applied, this commit will) Release version 1.0.0
(If applied, this commit will) Merge pull request #123 from user/branch

Bad Example
(If applied, this commit will) Fixed bug with Y
(If applied, this commit will) Changing behavior of X
(If applied, this commit will) More fixes for broken stuff
(If applied, this commit will) Sweet new API methods
~~~

<br />

### 6. Github 제목(이나 본문)에 이슈 번호 붙이기

이슈 번호를 사용하는 테크닉이 있다. 
~~~
Merge pull request #123 from someuser/somebranch
~~~

<br />

와 같은 예시에서 github는 "#번호"로 된 부분을 해당 github 저장소의 이슈 번호로 인식하고, 클릭할 수 있는 링크로 바꿔준다. 
이를 통해 우리는 개발 내역 관리 기능을 제대로 사용할 수 있다.
포매팅은 다음과 같이 하는 것이 좋다.

<br />

~~~
{동작} #번호 - 내용
~~~

<br />

이 포맷으로 작성한 제목의 예시
~~~
Refactor #28 - getPersonID()
Test #411 - Company class and its public methods
Implement #58 - Company 클래스 메소드 3개
~~~

<br />

이렇게 작성하게 되면 제목 한 줄만 보고도 해당 커밋이 github의 어느 이슈와 연관된 
작업물인지 빠르게 알 수 있다. github는 이슈 번호가 메세지에 포함된 커밋을 자동으로 이슈 페이지에 정리해준다.

<br />

### 7. 본문은 영문 기준 72자마다 줄 바꾸기

git은 자동으로 커밋 메세지 줄바꿈을 해주지 않는다. 적당한 위치에서 줄바꿈을 해주는 것은 가독성을 높여준다.

> tip: ~/.gitconfig 파일에 다음과 같이 작성해두면, 스타일 옵션이 지정되어 예뻐진 git log를 확인할 수 있다. 

~~~
$ git config --global alias.lg "log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold red)%h%C(reset) : %C(bold green)(%ar)%C(reset) - %C(cyan)<%an>%C(reset)%C(bold yellow)%d%C(reset)%n%n%w(90,1,2)%C(white)%B%C(reset)%n'"
~~~

<br />

### 8. 본문은 **어떻게** 보다 **무엇을, 왜**에 맞춰 작성하기

제목이 내용을 충분히 전달해준다. 그렇다면 우리는 해당 작업을 왜 했는지, 어느 파일 혹은 어느 객체 등
무엇에 왜 그런 작업을 했는 지를 본문에 작성해주면 될 것이다. 





