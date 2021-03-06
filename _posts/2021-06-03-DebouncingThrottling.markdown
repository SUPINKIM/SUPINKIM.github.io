---
layout: post
title: "Debounce(디바운스)와 Throttle(쓰로틀)에 대해 톺아보기"
date: 2021-06-03
category: [JavaScript]
---

<h4>Debounce & Throttle</h4>

이번 시간에는 디바운싱과 스로틀링에 대해 알아보려고 합니다. 일단 단어는 많이 들어봤는데 두 개념의 차이점은 무엇인지 여러 방식으로 코드를 구현해 보면서 그 개념을 완벽히 익히는 연습을 해보겠습니다.

디바운싱과 스로틀링 구현 예제를 구글에 검색 해보면 스코프와 클로저를 활용해 구현한 코드가 아주 많은데요, 클로저가 무엇인지는 알지만 한 번도 구현해 본 적이 없어서 이번에 그 개념을 실제로 코드를 구현해 보면서
공부할 수 있는 좋은 기회가 될 것 같습니다.

일단, 디바운싱과 스로틀링의 개념에 대해 알아보고 그 개념을 기반으로 작성한 디바운싱 코드와 스로틀링 코드를 살펴보겠습니다. 
그리고 해당 코드의 문제점이 무엇인지 Timer api의 개념과 함꼐 생각해 본 뒤, 마지막으로 클로저를 활용해 디바운싱과 스로틀링을 구현해보도록 하겠습니다.

<h5>1. 디바운싱과 스로틀링이란?</h5>

- Debounce : 마지막으로(처음) 함수가 호출된 시점을 기준으로 특정 시간 내 해당 함수가 계속 호출되면 그 시점을 계속 갱신해서 시간 내에 딱 한 번만 실행하도록 한다. 즉, '언제 원하는 처리가 실행됐는가'보다 '언제 마지막으로
함수가 호출됐는가'가 더 중요하다.
- Throttle : 마지막으로(처음) 함수가 호출된 시점을 기준으로 특정 시간 내에 요청된 처리는 모두 무시한다. 특정 시간이 지나면 해당 함수를 처리하고 마지막 함수 처리 시간을 갱신한다. 즉, '언제 원하는 처리가 실행됐는가'가 중요하다.

- Debounce와 Throttle의 공통점 : 동일한 처리를 빠른 시간 내 여러 번 처리하게 되거나 부하가 많이 걸리는 작업을 할 때 유용하다.

<h5>2. 개념을 기반으로 작성해 본 디바운싱과 스로틀링</h5>

먼저,아무 기법도 적용하지 않은 경우 콘솔에 input 이벤트 핸들러 콜백 함수 호출 시 콘솔에 찍히는 text입니다.

![스크린샷 2021-06-03 오후 10 38 21](https://user-images.githubusercontent.com/49034615/120665804-108acd00-c4c7-11eb-9bca-7c1fa3e37fb3.png)

_______________________________________________________________________________________________________________________________________

스로틀링 기법을 사용하면 다음과 같이 콘솔에 찍히게 됩니다.console.log(e.target.value) 함수가 실행된 경우(우리가 원하는 처리)에만 lastTime을 갱신해 주었습니다. 여기서 제가 활용하고 있는 값은 
event 객체 내 timeStamp 속성입니다. 스로틀링은 마지막 함수 처리 시간을 기준으로 원하는 함수 실행을 해줄 것인지 말 것인지를 정하기 때문에 아래와 같이 구현해 보았습니다.

![스크린샷 2021-06-03 오후 10 38 51](https://user-images.githubusercontent.com/49034615/120665847-184a7180-c4c7-11eb-866c-430fbf3f670f.png)

<script src="https://gist.github.com/SUPINKIM/0abae1c47c96d4ca53e6d0385a126e1e.js"></script>

_______________________________________________________________________________________________________________________________________

디바운싱 기법을 사용하면 다음과 같이 콘솔에 찍히게 됩니다. 보통 단어 작성의 경우 하나의 단어를 사람들이 다 작성하기 전까지는 계속 이벤트가 일어나다가 원하는 단어를 작성하면 중간에 잠깐 텀이 생기겠죠?
정확한 단어 완성 측면에서는 제 생각에 단어 작성 이벤트 처리를 스로틀링과 디바운싱 중 하나를 택해야 한다면 디바운싱이 조금 더 적합해 보입니다. 하지만 성능 면에서 봤을 때는 매 입력마다 마지막 콜을 갱신해줘야 하는 디바운싱이 조금 더 불리할 수 있겠다는 생각은 듭니다. (그렇지만 ,, 웬만한 예제에서는 큰 차이 없으리라 생각합니다.)

![스크린샷 2021-06-04 오전 12 05 42](https://user-images.githubusercontent.com/49034615/120667603-9f4c1980-c4c8-11eb-8652-459daab9c4b6.png)

<script src="https://gist.github.com/SUPINKIM/deb63635b345072489a3f49dd74411c1.js"></script>

스로틀링과 달리 각 조건절 내에서 동일하게 lastCall을 갱신하고 있는 것을 확인할 수 있습니다. 원하는 실행인 console.log()와 관계 없이 함수 호출이 기준이 되어야 하니까요. 

그러나 이렇게 코드를 작성하고 보니 썩 좋은 코드 같지는 않습니다. 왜일까요? 

1. 첫 번째는 이벤트 핸들러 함수에서 굳이 setInterval을 사용할 필요가 있었을까? 라는 생각이 듭니다. 이벤트가 발생하면 무조건 각 콜백은 실행이 됩니다. 그러므로 setTimeout을 호출해 특정 시간(위의 코드에서는 time이 되겠죠?) 내에 한 번만 호출하도록 해주면 됩니다. 굳이 setInterval로 매 타임마다 실행을 시킬 필요는 없겠죠.
2. setInterval로 이미 timer 객체가 생성이 되는데 이를 활용하지 않고 굳이 event 객체 내 timeStamp를 가지고 시간을 계산하는 코드를 작성했습니다. 이건 아마 timer api에 대한 이해도가 떨어지기 때문이겠죠? 그래서 다음으로는 timer api에 대해 살펴봐야 할 것 같습니다.
3. time을 전역 변수로 사용했네요. 전역 변수를 남용하지 않고 클로저를 이용하면 time 스코프를 한 단계 내릴 수 있겠죠? 다른 곳에서 굳이 time 변수를 쓸 필요는 없으니까요. 그래서 timer api를 살펴본 다음 클로저로 디바운싱과 스로틀링을 구현해 보도록 하겠습니다.(조금 더 공부가 필요할 것 같네요.)

디바운싱과 스로틀링에 대해 단순히 피상적으로만 이해하고 있었는데 확실히 직접 구현해 보는 것이 도움이 됩니다! 그럼 timer api와 클로저에 대해 조금 더 공부한 뒤 돌아오도록 할게요. 

.fin

