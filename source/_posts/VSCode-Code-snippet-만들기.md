---
title: VSCode Code snippet 만들기.
date: 2019-04-27 19:07:22
tags: [Javascript, CodeSnippet]
category: [Programming, VSCode]
---

# VSCode Code Snippet 만들기.

내가 사용중인 개발도구인 VSCode를 좀 더 확장하여 쓰고싶은 생각이 들었다.

무엇이 있을까... 생각을 해보다가

자주쓰는 코드 완성 기능을 만들어보자! 라는 생각이 들어서 검색..

VSCode에 적용 하려면 먼저

Mac 기준으로 Command + shift + p 를 입력하고 'snippet' 이라고 입력을 하면 'insert snippet' 항목이 나옴.

![](/image/20190427/1.png)

그리고 'New Global Code snippet' 항목이 나옴! 엔터 누르고 

![](/image/20190427/2.png)

code snippet 파일을 만드는 다이얼로그가 등장!

![](/image/20190427/3.png)

저의 code snippet이름은 Jeungeuny.code-snippets!

![](/image/20190427/4.png)

처음에 만들면 위와 같은 샘플 코드가 들어있음.

나와 같은 경우는 log를 찍을 때 '변수명: 변수값' 이런식으로 자주 사용하기 때문에

![](/image/20190427/5.png)

위와 같이 작성 하였음.

scope => code snippet이 동작할 파일확장자

prefix => 편집화면에서 코드작성시 입력하는 키값이라고 생각하면되고,

body => prefix를 입력했을 때 나오는 코드라고 생각하면 된다.

$1은 캐럿 위치라고 생각하면 된다.

code-snippets 파일을 저장하고 scope에 해당하는 파일에서 prefix를 입력 하면

아래와 같은 다이얼로그가 뜨고, 엔터를 눌를시

![](/image/20190427/6.png)

아래처럼 캐럿이 2개가 생기며 로그에 찍을 변수를 입력하면! 간단하게 사용 할 수 있다!

![](/image/20190427/7.png)

자주쓰는 코드는 등록하여 사용하면 생산성이 증가 할 것 같다!