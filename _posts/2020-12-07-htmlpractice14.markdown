---
layout: post
title: "코딩 기록 14"
date: 2020-12-07
category: [HTML,CSS,Javascript]
tags:[Front-End]
---


<h3>코딩 기록 14_계산기 만들기(덧셈만 출력 주의)</h3>
요즘 js를 열심히 찾아보면서 공부하고 있는데, 각 요소가 매개변수를 받아 function을 실행하게 하는 const 변수를 선언했다.
그리고 그 변수의 요소에 접근해 해당 function들을 실행시켰다. 
<br>
()=>{}와 같은 화살표 함수도 return이 가능해서 처음에는 단순히 console.log();로 콘솔창에 값을 입력했는데, 나중에는 계산 값을 return 받아 
해당 값을 html 태그 안에 출력했다. 재밌는 점은 Number 객체를 쓰지 않으면 각 input 태그에서 받아온 value가 String이라서 3+2인 5를 출력하는 게 아니라 32를 출력해버린다.
그래서 Number()를 사용해 타입 캐스팅을 해준 뒤 해당 값을 함수의 매개 변수로 넣으면 원하는 값(number1+number2 연산값)으로 출력이 되는 걸 확인할 수 있다.
Number()로 타입 캐스팅을 하지 않으면 단순히 텍스트가 나열되어 출력되므로 궁금하다면 타입 캐스팅을 건너 뛰고 각 number1, number2를 매개변수로 주길 바란다. 그럼 "3"+"2" 연산이 실행 돼 32가 출력될 것이다.

<script src="https://gist.github.com/SUPINKIM/49ad1449e153d99ed4f7862c1a592d90.js"></script>
![Kapture 2020-12-07 at 21 48 00](https://user-images.githubusercontent.com/49034615/101352745-f1bfcb00-38d5-11eb-9544-4980e1f7a6d4.gif)
