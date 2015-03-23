layout: true
class: center, middle

---

# 알아두면 유용한 명령어들

변용훈
[@river](http://twitter.com/river)

---

layout: false
class: center, middle

## @river

Server Side Developer

\- Classic ASP<br>
\- PHP

<img src="/img/profile.jpg" style="border-radius:200px" width="150">


---

class: center, middle

### 기본 명령어 중 제가 자주 사용하는 것들
### 몰라도 되지만 알면 조금이라도 편할 수 있는 것들
### OS X 위주로 설명 및 데모

---

layout: false

## Agenda

* 설치
* 에디터
* 시스템
  - 파일
  - 디렉토리
  - 프로세스
* git
* web 관련
* QnA

---

## homebrew

http://brew.sh/

The missing package manager for OS X .red[*]

- Install

```bash
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

```

- Usage

```bash
$ brew install tree
$ brew uninstall tree
$ brew info tree
$ brew search tree
$ brew update
```

.footnote[.red[*] linuxbrew]

---

## brew cask

http://caskroom.io/

A CLI workflow for the administration of Mac applications distributed as binaries

- Install

```sh
$ brew install caskroom/cask/brew-cask
```

- Usage

```sh
$ brew cask install google-chrome
```

---

class: center, middle

## zsh

---

.left-column[
## zsh
### 설치
]

.right-column[
Install

```
$ brew install zsh

$ sudo vim /etc/shells
/usr/local/bin/zsh 라인 추가

$ chsh -s /usr/local/bin/zsh
```

[oh my zsh](https://github.com/robbyrussell/oh-my-zsh)

- plugin, [theme](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes) 포함

<img src="https://cloud.githubusercontent.com/assets/2618447/6316862/70f58fb6-ba03-11e4-82c9-c083bf9a6574.png" width="100%">

]


---

.left-column[
## zsh
### 설치
### 단축키
]

.right-column[
앞으로 / 뒤로
- `^a` : 맨 앞으로
- `^e` : 맨 뒤로
- `^b` : 한칸 앞으로
- `^f` : 한칸 뒤로 

라인 버리기
- `^u` : 현재 라인 삭제하기
- `^l` : 스크린 클리어

kill / yank
- `^d` : 한 글자 kill
- `^k` : 한 줄 kill
- `^y` : yank

kill / suspend
- `^c` : 현재 프로세스 종료
- `^z` : 현재 프로세스 중단
]

.footnote[```$ bindkey```]

---

.left-column[
## zsh
### 설치
### 단축키
### 디렉토리 이동
]

.right-column[

상위 디렉토리 이동 

```sh
$ ..
$ ...
$ ...
$ cd..
$ cd...
$ cd....
```

디렉토리 이동

```sh
$ cd work
$ work/
$ cd ~
$ cd -      # 이전 디렉토리로 이동
$ cd -<TAB> # 이전 디렉토리 history

```
]

---

.left-column[
## zsh
### 설치
### 단축키
### 디렉토리 이동
### 장점
]

.right-column[

auto completion

```sh
$ cd <TAB>
$ git co<TAB>
$ echo $gop<TAB>
$ kill <TAB>
```

git 상태 prompt 표시


기타 

```sh
$ mkdir directory
$ cd directory

$ mkdir directory && cd $_

$ take directory
```

]

---

## Z

https://github.com/rupa/z

디렉토리 이동을 도와주는 프로그램

- Install

```sh
$ brew install z

.zshrc에 라인 추가

$ vi ~/.zshrc
. `brew --prefix`/etc/profile.d/z.sh
```

- Usage

```sh
$ z directory
```

---

## vim

기본 에디터로 쓰지 않더라도 git commit 로그 작성할 정도는 쓸 수 있어야

참고

- [Vim adventure](http://vim-adventures.com/)
- [Vimium chrome extension](https://chrome.google.com/webstore/detail/vimium/dbepggeogbaibhgnhhndojpepiihcmeb?hl=en)


---

## 파일 내용보는 도구들 

- more
- less
- head
- tail 
- cat


```
$ tail log.txt
$ tail -n 100 log.txt
$ tail -f log.txt
```

---

## 디렉토리

특정 디렉토리의 용량 보기

```
$ du -sh directory
```

파일 시스템 사용량 보기

```
$ df -h
```

디렉토리 구조 트리형태로 출력하기

```
$ tree
```

검색어랑 매칭되는 파일 찾기

```sh
$ find . -name "event.*"
```


검색어랑 매칭되는 내용을 가지고 있는 파일 찾기

```sh
$ grep -ir --inclucde="*.md" map .
```


---

## 프로세스

- top
- htop
  - install
  ```sh
  $ brew install htop
  ```
- fg
- bg
- kill

---

## git

### tig

- Install

```
$ brew install tig
```

- Usage

```
$ tig
$ tig log
$ tig show
$ tig blame
$ tig grep
$ tig stash
$ tig status
```

---

class: center, middle

## 웹관련

---

## curl

```
$ telnet google.com 80
$ curl google.com
$ curl -i google.com
```

API test

```sh
$ curl -i -H "Content-Type: application/json" -X POST \
  -d '{"name":"toy","category":"travel"}' \
  http://example.com/api/item

i – show response headers
H – pass request headers to the resource
X – pass a HTTP method name
d – pass in parameters enclosed in quotes; multiple parameters are separated by ‘&’
```


---

.left-column[
## 로컬 웹사이트 접근
### xipio
]

.right-column[
http://xip.io/ (37Signals)

wildcard DNS for everyone 

```
          `10.0.0.1`.xip.io   resolves to   10.0.0.1
      www.`10.0.0.1`.xip.io   resolves to   10.0.0.1
   mysite.`10.0.0.1`.xip.io   resolves to   10.0.0.1
  foo.bar.`10.0.0.1`.xip.io   resolves to   10.0.0.1
```

- 장점
  - 호스트 파일 수정 없이 사용가능. 특히 모바일 디바이스

- 단점 
  - 지정 `ip`에 접근가능한 디바이스만 사용 가능
]

---

.left-column[
## 로컬 웹사이트 접근
### xipio
### finch
]

.right-column[

https://meetfinch.com/

로컬 웹사이트를 외부에서 접속 가능하게 하는 서비스


```
$ npm install --global finch
$ finch register
$ finch forward http://127.0.0.1:9000
```

- 장점
  - public 하지 않은 `ip`에도 접근 가능

- 단점 
  - 느리다.
]

---

## Simple web server

```
$ python -m SimpleHTTPServer 5000
$ ruby -run -e httpd . -p 5000
$ php -S localhost:5000
```

---

## 기타

- tmux
- vagrant
- markdown
- zen coding

---

class: center, middle

## QnA

---

class: center, middle

## 감사합니다 !!!!
