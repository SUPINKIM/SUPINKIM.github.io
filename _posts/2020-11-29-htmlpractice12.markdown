---
layout: post
title: "코딩 기록 12"
date: 2020-11-29
category: [HTML,CSS,JavaScript]
---

<h3>코딩기록 12</h3>

20일 이후의 코딩 기록을 하기에 앞서 요즘 javascript를 열심히 공부 중인데 input값에 따라 텍스트를 다르게 노출하는 간단한 함수를 만들어
이를 먼저 소개하려고 한다.
<br> 
코드는 어려운 게 없고, 기본 javascript를 아는 사람이라면 누구나 빠르게 이해할 수 있다. 
먼저 기본적으로 작성해 놓은 span text를 전역 변수에 담고,input 값에 text가 입력되면 해당 text를 받아 인사를 건네는 텍스트로 변경한다.
만약, text를 적었다가 지웠다면 맨 처음 default text를 노출하고 다시 text가 적히는 것에 대해 해당 변수 값을 받아 인사말을 노출한다. 
해당 함수를 2초에 한 번씩 새로고침해서 값을 노출하는 것으로 작성했다.
try-catch 문으로 예외처리도 해줘서 만약 UncaughtTypeError가 발생하면 'Sorry, try again..'이라는 문구가 노출된다.

![Kapture 2020-11-29 at 16 36 46](https://user-images.githubusercontent.com/49034615/100537233-ec290c00-3269-11eb-93a6-89dcf7112dbb.gif)

<script src="https://gist.github.com/SUPINKIM/bbbe781cd3ebb2085d80c8af89989a1b.js"></script>
