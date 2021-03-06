---
layout: post
title: "[코딩테스트 문제풀이] Programmers 메뉴 리뉴얼"
date: 2021-03-25
category: [JavaScript]
---

<h4>Programmers Lv.2 메뉴 리뉴얼 <small>#kakao#2021 KAKAO BLIND RECRUITMENT</small></h4>

<h5>[문제]</h5>
~~~
어떤 단품메뉴들을 조합해서 코스요리 메뉴로 구성하면 좋을 지 고민하던 "스카피"는 이전에 각 손님들이 주문할 때 가장 많이 함께 주문한 단품메뉴들을 코스요리 메뉴로 구성하기로 했습니다.
단, 코스요리 메뉴는 최소 2가지 이상의 단품메뉴로 구성하려고 합니다. 또한, 최소 2명 이상의 손님으로부터 주문된 단품메뉴 조합에 대해서만 코스요리 메뉴 후보에 포함하기로 했습니다.

예를 들어, 손님 6명이 주문한 단품메뉴들의 조합이 다음과 같다면,
(각 손님은 단품메뉴를 2개 이상 주문해야 하며, 각 단품메뉴는 A ~ Z의 알파벳 대문자로 표기합니다.)
(중략)
각 손님들이 주문한 단품메뉴들이 문자열 형식으로 담긴 배열 orders, "스카피"가 추가하고 싶어하는 코스요리를 구성하는 단품메뉴들의 갯수가 담긴 배열 course가 매개변수로 주어질 때, 
"스카피"가 새로 추가하게 될 코스요리의 메뉴 구성을 문자열 형태로 배열에 담아 return 하도록 solution 함수를 완성해 주세요.
~~~

<h5>[접근 방법]</h5>
일단 보자마자 무슨 자료구조를 써야 할 지 아이디어가 전혀 떠오르지 않아 다른 사람들의 힌트를 조금 보고 감을 잡았다. 알고리즘은 완전 탐색인 브루트 포스 알고리즘을 사용해서 문자열의 조합을 만들고
이 조합들이 각 문자열 내 포함되어 있는 개수를 센 뒤 각 길이에서 가장 많이 나타난 문자열만 출력하는 문제였다. 
처음에는 2명 이상이 시키면 무조건 포함해도 되는 줄 알았는데, 각 길이별로 최대 빈도수의 서브 스트링만 출력하는 거였다. 카카오 코테 문제의 경우, 문제가 길어서 읽는데만 해도 
시간이 많이 걸렸다. 그래서 미리미리 연습해두자라는 마음으로 카카오 코테 문제 위주로 봤는데 진짜 읽고 이해하는 데만 해도 시간이 꽤 걸리는 거 같다. 연습이 더 필요할 것 같다.

코테 연습할 때 Map 자료 구조를 한번도 사용해 본 적이 없는데, Map은 Set과 마찬가지로 ES6에 추가된 새로운 문법이다. 기존의 Object랑 비슷하긴 한데 iterator를 제공하는 게 좋다.(Object는 키에 대해 정렬이 안 됨.) 그래서 각 substring 조합을 Map의 키로, 나온 횟수를 value로 지정해서 저장해두고 나중에 문자 길이 별로 비교해주면 된다.

그리고 Map은 forEach문을 사용할 수 있는데, 기존 Object는 사용 불가라서 이 점이 진짜 좋다. forEach문의 callback 함수는 기본적으로 Map의 value,key,map을 매개변수로 받는데 이 밖에 
다른 매개변수를 전달하고 싶다면 callback 함수를 넘길 때 전체 매개변수를 다 써주면 잘 넘어간다.(기본 매개 변수만 넘겨줄 거라면 callback 호출 시에 굳이 써주지 않아도 되지만 명시해주는 것이 
개인적으로 봤을 때 코드를 이해하는 데는 더 좋은 것 같다.)

이 문제를 풀면서 두 번째 난관에 부딪혔던 건, 나는 처음에 orders의 메뉴 주문에 대해 알파벳 순으로 정렬을 안 해줬는데 어차피 key를 저장할 때 그 조합에 대해 sort를 해줬기 때문에 
상관 없다고 생각했다. 그런데 orders의 요소들을 정렬하지 않고 처리하니 통과하지 못하는 몇 몇 케이스가 발생했다.(아직도 왜 그런지 명쾌하게 떠오르는 반례가 없다.) 

그래서 혹시나 하고 orders의 요소들을 맨 처음에 정렬하는 코드를 추가하니 바로 통과가 되어서 조금 의아하다. 어차피 'AC'의 경우 B가 중간에 있다면 'ABC'의 형태로 되어서 key 하나하나 비교해줄 때
'BCA'나 'ABC'나 똑같은 거 아닌가 싶은데 아닌가보다.

여튼 문자열을 담은 배열의 길이가 20이하이고, 각 문자열의 최대 길이는 10이기 때문에 재귀함수로 조합을 만들어도 콜스택 에러에 걸리지 않는다.
이런 문제만 나오면 좋겠다.(재귀로 풀면 쉬운데 입력값이 10000을 넘어가면 결국 반복문으로 푸는 방법밖에 없다.)

오늘 Map을 쓰면서 처음 안 사실인데, <b>Map의 iterator는 한 번 iterator.next().value로 사용하면 마치 pop()과 같아서 전체 map.size만큼 반복해서 돌았을 때 들어있는 요소가 아무 것도 없다.
그래서 각 반복문 안에서 iterator를 만들어 줘야 한다.</b> Map 자료구조를 쓰는 모든 사람들이 이 점을 유의해서 사용하면 좋을 것 같다.

<h5>[해결 코드]</h5>
<script src="https://gist.github.com/SUPINKIM/ee67e9a40c940fa7c21a3cccdef56359.js"></script>

