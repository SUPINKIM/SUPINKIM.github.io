---
layout: post
title: "코딩 기록 6"
date: 2020-11-01
category: [Javascript]
---


<h3>코딩 기록 6_canvas 2탄</h3>

오늘도 어제에 이어 canvas를 이어서 공부했다. 
원을 생성하고 마우스 포인터를 따라 움직이는 원 그리기 등 javascript로 코드를 작성해보았다.
일단 javascript는 script 언어라서 배우기 전부터 되게 겁 먹고 함수를 매개변수로 받아버리는 그 능력에 기겁해 
배우기 쉽지 않을 거라고 생각했는데 의외로 자바와 비슷한 모양의 문법이 많아서 (역시 객체지향)
걱정한 것보다 쉽게 배우고 있다. 확실히 javascript가 있으면 다양한 이벤트 처리도 가능해서 훨씬 인터랙티브해서 재밌다. 점점 더 그 동적 매력에 빠져들고 있다.
<p>
  어제는 단순히 animate()로 코드를 쭉 나열해서 canvas에 그렸다면 오늘은 Circle 함수를 만들어 x,y,radius,color로 기본 틀을 잡고 
  this.upate() => this.draw()로 draw() 함수에서 원을 그리고 init() 함수에서 circle 객체를 생성하고 animate() 함수에서 각 circle의 update()를 호출하는
  식으로 코드를 작성했다. class로 선언한 게 아닌데 객체로 생성할 수 있다는 점이 신기하면서도 편했다. 그냥 코드를 쭉쭉 나열하는 것보다 훨씬 코드 재사용성이 높아져서 
  여러 개의 원을 생성하는 데도 어려움이 없다는 게 제일 장점인 것 같다. 앞으로 javascript를 더 연구해 나가야겠다.
  <script src="https://gist.github.com/SUPINKIM/7df773c2f94724474f1b679dc17a98d1.js"></script>
</p>

![화면-기록-2020-11-01-오후-10 47 46](https://user-images.githubusercontent.com/49034615/97804656-aa21a000-1c94-11eb-8a1f-604a4edea5c0.gif)
