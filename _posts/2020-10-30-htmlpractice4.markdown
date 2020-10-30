---
layout: post
title:  "코딩 기록 4"
date:   2020-10-30
category : [HTML,CSS]
---


<h3>코딩 공부 기록_<h5>작심삼일은 넘었어</h5></h3>

어제는 급하게 또 막 밤 11시 넘어서 코딩 공부 기록을 하느라 텍스트를 쓸 정신이 없었다.
퇴근하고 2시간 거리를 걸려 집으로 오면 밥 먹고 씻고 치우고 정리하면 진짜로 저녁이 없는 삶이에요... ㅎ
<br> 하여튼 그래서 어제 내가 물음표를 던져놨던 왜 display:flex가 안 먹는가, 왜 그러는 것인가, 화면 창이 작아지면 자연스럽게 아랫줄로 내려 와야지
왜 가만히 있는 것이냐(<s>가마니로 있으니까 내가 가마니로 보여...?</s>)

<br>급하게 포스팅을 마치고 다시 코드를 수정해보니 일단 flex가 먹으려면 상위의 박스가 하나 더 있어야 하는데 각각의 article에다가 display:flex를 백날 줘봐라
되겠냐고,,, 그래서 상위에 <section class="bigbox"></section> 태그를 달아주고 그 안에다 article을 넣었더니 이제 잘 된다... flex-wrap:wrap; 친구가 잘 먹혀요.(기쁨)
<script src="https://gist.github.com/SUPINKIM/256a35c8057c2a5805062b5dc60e125f.js"></script>
<script src="https://gist.github.com/SUPINKIM/e3d06cd935567385a047d95f763da712.js"></script>

![스크린샷 2020-10-30 오후 4 01 55](https://user-images.githubusercontent.com/49034615/97670405-7e9e8a00-1ac9-11eb-8ced-0f817535309c.png)
![스크린샷 2020-10-30 오후 4 02 08](https://user-images.githubusercontent.com/49034615/97670429-9249f080-1ac9-11eb-82f5-1003d8850731.png)


<br><br>
그리고 이제 오늘은 출근을 안 했어요.(<s>갑자기 요체 무엇?</s>) 너무 좋아 주3일 도입이 시급하다..는 농담이고 이번 연도 연차가 너무 많이 남았는데, 11월부터 다시 또 바빠질 예정이라서
그냥 오늘 썼다. 천사이신 내 사수(그저 빛✨✨✨)가 쉬어도 된댔어... 여튼 그래서 느긋하게 일어나서 오늘은 시간에 안 쫓기고 공부도 하고 포스팅도 하는 중이다.
(<s>너무 행복합니다.나는 행복합니다. 행복 행복 행복합니다.</s>)

<br> 예,, 그래서 이제 어제 또 유튜브를 보다보니 HTML5 Cnavas로 재미난 것들을 많이 할 수 있겠더라고... 그래서 공부 목록에 Canvas도 추가한다!


<ul>
  <li>React</li>
  <li>Canvas</li>
</ul>

<img width="604" alt="스크린샷 2020-10-30 오후 4 01 14" src="https://user-images.githubusercontent.com/49034615/97670356-6169bb80-1ac9-11eb-97ee-36458bef5b6d.png">
