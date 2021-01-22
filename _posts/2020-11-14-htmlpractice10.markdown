---
layout: post
title: "코딩 기록 10"
date: 2020-11-14
category: [HTML,CSS,JavaScript]
---

<h3>코딩 기록 10_일주일만에 컴백</h3>

일주일간 공부를 소홀히 한 건 아니지만, 그래도 3일에 한 번은 쓸 줄 알았는데... (<s>여튼 또 반성합니다.</s>) 그래서 주말을 맞이하여 변명 + 캡처본을 올리면서 어떤 점을 공부했는지 적어보도록 하겠다.

코드 연습을 위해 어떤 것을 주제로 연습할까 고민하다가 여행 갔을 떄의 사진을 활용해보자는 생각이 들어서 런던, 파리, 홍콩 여행 갔을 때 찍은 사진을 넣어 웹 사이트 주제를 잡았다.
<ul>
  <li>11월 9일 코딩<br>
  <img width="700" alt="스크린샷 2020-11-09 오후 11 13 19" src="https://user-images.githubusercontent.com/49034615/99142385-d6c3b780-2697-11eb-9432-399653a70920.png">
  <img width="700" alt="스크린샷 2020-11-09 오후 11 52 56" src="https://user-images.githubusercontent.com/49034615/99142386-d88d7b00-2697-11eb-8b56-18336a0c7bef.png">
  </li>

  9일에 연습 중 의도대로 잘 안 됐던 부분은 hover 상태일 때 img 위에 span으로 감싸진 텍스트가 중앙 정렬되어 노출되면 좋겠는데 도저히 중앙 정렬이 안 됐다. img와 span을 감싸고 있는 div를 display: flex 속성값을 줘서 
  나란히 정렬을 하고 position: relative, left: -50%를 단순히 하면 가운데에 올 줄 알았는데 span의 텍스트 길이에 따라 가운데 정렬로 보이는 것도 있고 아닌 것도 있었다.
  - solution : position을 relative 값을 주고 flex 속성으로 나란히 있는 상태에서 x축만 -50% 이동하고 transform: translate 값으로 x축만 이동하게끔 값을 줬다. translate에 대해서 더 자세하게 
  알아보려고 MDN에서 찾아봤는데 (x,y)로 이동하게 하는 api인 것 같았다. (<s>잘 이해한 거지?</s>)
  ```
    position: relative;
    left: -50%;
    transform: translate(-50%, 0);
  ```

  <li> 11월 10/11일 코딩(10일은 늦게 퇴근해서 하다보니 11일 새벽이 되어버렸다.)<br>
  <img width="700" alt="스크린샷 2020-11-11 오전 12 34 09" src="https://user-images.githubusercontent.com/49034615/99142905-aaf70080-269c-11eb-8505-67a3c1a80918.png">
  <img width="700" alt="스크린샷 2020-11-11 오후 11 34 19" src="https://user-images.githubusercontent.com/49034615/99142891-961a6d00-269c-11eb-845a-c4d995d74c73.png">
  </li>

  이미지 slider를 만들고 싶어서 w3c에 있는 예제를 찾아서 해봤는데, html, css, javascript 모두 이용했다. 그런데 생각보다 술술 잘 풀리지 않아서 html과 css로만 이용해서 하는 예제도 따라해 봤는데 
  뭐가 더 좋다 이렇게 말할 수는 없겠지만, 간단하게 그 이미지들만 한정적으로 보여준다면 굳이 javascript를 이용할 필요는 없겠지만, 많은 이미지를 보여주고 click이벤트를 사용할 거라면 javascript로
  작성하는 편이 더 좋겠다는 생각이 들었다. 그렇지만 예제처럼 예쁘게 인디케이터 부분이 디자인되지 않아서 그 점은 더 연습을 해야 될 것 같다.

  <br>
  
</ul>

![Kapture 2020-11-14 at 17 25 15](https://user-images.githubusercontent.com/49034615/99143229-31acdd00-269f-11eb-86bc-5e5f86e75812.gif)
