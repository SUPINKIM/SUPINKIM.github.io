---
layout: post
title: "Debounce(디바운스)와 Throttle(쓰로틀)에 대해 톺아보기2 with Closure"
date: 2021-06-08
category: [JavaScript]
---

<h4>디바운싱 톺아보기 with Closure in React</h4>

안녕하세요. 오늘은 디바운싱에 대해 더 알아보는 시간을 가져보려고 합니다. 지난 며칠 간, 여행 블로그 프론트 작업 중 API를 호출하는 코드를 짜면서 이번에 공부한 디바운싱을 적용해봐야겠다! 라는 생각에
바로 Timer API(setTimeout)와 closure를 활용해 코드를 짜고 디바운싱이 되겠지 짜-잔 하고 클릭을 하니 디바운싱이 전혀 적용되지 않고 코드가 돌아가는 것을 발견했습니다.

<a href="https://imgflip.com/i/5cj0ld"><img width="400" src="https://i.imgflip.com/5cj0ld.jpg" title="made at imgflip.com"/></a><div><a href="https://imgflip.com/memegenerator">from Imgflip Meme Generator</a></div>

제가 맨 처음 작성한 코드는 다음과 같습니다.

![리액트 디바운싱 실패 코드](https://user-images.githubusercontent.com/49034615/121206249-46f38e00-c8b3-11eb-9331-4745cd50d2f5.png)

아무리 timer를 찍어봐도 이전에 생성된 timer ID가 남아있지 않고 계속 null 값이 출력되는 것을 확인할 수 있었습니다.

그래서 너무 놀란 저는 헐레벌떡 바닐라 자바스크립트에서도 동작하지 않는 것인가 하고 아래의 코드를 작성하여 돌려보았습니다.

결과는....?

<script src="https://gist.github.com/SUPINKIM/cd44eb55eec649f584c767a947db68d7.js"></script>

<img width="650" alt="바닐라 자바스크립트로 구현한 클로저" src="https://user-images.githubusercontent.com/49034615/121207082-f6c8fb80-c8b3-11eb-9720-0a6cc254d529.png">


<strong>네, 다행히 너무 잘 돌아갑니다. 박수 👏 </strong>

자세히 보면, 이전에 마지막으로 생성된 timer값이 console.log('click!!')을 실행하고 다음 이벤트가 발생했을 때에도 살아있고 그 값이 clearTimeout(timer) 함수에 의해 삭제되는 것을 확인할 수 있습니다.
비공개 변수(호출되는 함수의 매개변수도 아니고 그 함수 스코프 내에 생성된 변수도 아닌 변수) 값이 여전히 유효하게 살아서 외부 함수는 호출되지 않아도 스코프 체인을 따라 timer 변수를 찾아서 사용할 수 있는 것이죠.

이제 자바스크립트의 클로저는 조금 더 이해했다고 생각이 들 때쯤, 그럼 왜 리액트에서는 계속 null 값만 남아 있을까? 라는 의문이 생겼습니다.

아직 그 의문은 완벽히 해결되지 못하여 더 찾아볼 예정이지만, Vanilla JS에서 이벤트 발생 시 콘솔에 찍히는 이벤트 객체와 리액트 내에서 이벤트 발생 시 발생하는 이벤트 객체는 성격이 다르다는 점에서 차이가 발생한다고
추측하고 있습니다.

리액트 내에서 이벤트가 발생하면 합성 이벤트(SyntheticEvent)가 전달되는데, 이는 일반 이벤트 객체를 한 번 래핑한 이벤트 객체로써, 이벤트가 발생한 그 때에만 유효하고 그 다음에는 모든 속성 값이 null이 된다고 합니다.
이 부분에 대해서는 다음에 다시 다뤄볼까 합니다.

그래서 그런지, 이전에 분명 이벤트가 발생해서 이벤트 핸들링을 위한 콜백 함수가 이미 여러 차례 실행됐음에도 불구하고 모든 콜백함수가 마치 각각의 독립된 객체마냥 새로이 타이머가 생성되어 delay 내에 이벤트가 발생되어도
모든 timer는 null인 것을 확인할 수 있었습니다.

그래서 이런 방식으로는 debouncing을 리액트에서 할 수 없다는 것을 깨닫고(!) 찾아보니 useCallback()를 사용해 debounce를 구현하거나, 매우 유명한(!) lodash의 debounce 라이브러리를 활용하는 방법으로 많은 사람들이 해결 하고 있었습니다.. 그래서 제가 택한 방법은.. 나만의 커스텀 hook을 만들어보자!는 것이었습니다. 분명 리액트는 자바스크립트로 만든 라이브러리고, 우린 모든 파일을 js로 만드니, 
당연히 clouser를 구현할 수 있는 방법이 있을 것이고, 우리에겐 setState()가 있다 아이가! 

^^

그래서 결론은 디바운싱을 하는 useDebouce라는 커스텀 훅을 만드는 데 성공하였습니다. 해당 코드는 다음 시간에 공유해 보도록 하겠습니다. 리액트의 세계는 무궁무진하답니다. :)

.fin
