---
layout: post
title: "[코딩테스트 문제풀이] BOJ 1202.보석도둑"
date: 2021-03-14
category: [JavaScript]
---


<h4> [백준] 코딩테스트 문제 풀이 : 1202.보석 도둑 <small>#greedy#Heap#PriorityQueue</small></h4>


오늘 가지고 온 문제는 보석 도둑이다. 알고리즘은 그리디, 자료 구조는 Heap을 이용한 우선순위 큐를 활용하는 것이 정석.

일단은 JavaScript의 특성상 내 논리와 동일해도 이걸 읽고 계시는 분 역시 자바스크립트로는 이 문제를 백준에서 통과 하시기 어려울 가능성이 큽니다.

하하 눈물이 앞을 가리네.. 정말 엄청난 시도 끝에 자바스크립트로 제출하는 것을 포기하고 다른 언어로 제출해서 node.js로 푸신 분들 통과 코드를 봤는데
대다수가(대다수라고 해봤자 한 자리 숫자 ㅎ) class로 PriorityQueue를 구현했다. 나는 일단 그냥 MaxHeap, MinHeap 다 구현해서 풀었는데 시간 초과가 계속 나서 결국엔 포기했다.

솔직히 왜 시간 초과 나는지도 모르겠고 7%가 첫 번째 고비, 15%가 두 번째 고비였는데 일단 15%를 못 넘겼고, 꼭 MaxHeap이나 MinHeap으로 구현하지 않아도 15%까지 갔던 코드도 있어서
다 소개해보려고 한다.

(왜냐면 솔직히 억울함^^ 한 문제에 이렇게 많은 풀이법이 나올 수 있나 싶은데 나도 오기가 생겨서 진짜 열심히 풀었지만 자바스크립트로는 실패. 같은 논리, 다른 언어로 통과될 때마다 화딱지가🔥
제 코드 그대로 복붙한다고 해서 아마 백준에서는 통과하시기 어려울 겁니다..아 다시 파이썬 해야 되나..😂)

그래서 첫 번째 문제 읽자마자 생각한 코드는 반복문 두 번 돌려서 각 가방 무게보다 작은 보석 중 가치가 가장 큰 걸 찾아서 더 하는 식으로 했는데 O(n^2)의 시간 복잡도이기 때문에 단박에 안 될 줄 알았음.

<img width="400" alt="스크린샷 2021-03-14 오후 11 37 08" src="https://user-images.githubusercontent.com/49034615/111072502-3931a500-851e-11eb-933d-e47224b48713.png">
<br>입력이 좀 커서 sum의 최대값이 2^31 - 1 값을 넘어감.

그래서 두 번째 생각한 건 splice()와 pop()을 써서 탐색 범위를 줄여보자라는 거였는데 이거 역시 시간 초과로 실패.

그래서 좀 찾아보니 PriorityQueue 자료구조를 활용하라고 하는데 하하 JavaScript에는 c++이나 Python과 달리 pq 모듈 같은 건 없다. 직접 구현해야 한다는 소리..
그래서 공부하는 마음으로(<s>아니 공부 맞음</s>) 이번에 우선순위 큐를 진짜 익혀보자는 마음으로 도전. 일단 MaxHeap이나 MinHeap은 다들 아시다시피 배열로 구현할 수 있지만 느슨한 트리구조라서
꼭 내 앞에 있는 배열(윗 레벨의 자식 노드나 나의 형제)이 나보다 큰 값(MaxHeap일 때)이라는 보장이 없음. 그냥 자식 노드와 부모 노드만 비교하기 때문에 bubbleUp만 구현하면 안되고 트리의 루트 노드를 
선택하면 전체 트리의 가장 마지막 값을 heap[0]에 덮어 씌워 bubbleDown()(자식 노드와 비교해서 자식이 더 큰 경우 교환) 다시 자리를 찾아주는 작업을 꼭 해줘야 함. 그렇지 않으면 원치 않는 값이 최대값인냥
나를 속이고 뽑힐 수 있음 ^^

<h5>구현 방법 1 - 가방 무게를 전체 순회하며 해당 가방 무게보다 작거나 같은 보석은 모두 heap에 넣고 보석 가치가 큰 기준으로 MaxHeap을 구현해서 루트를 선택함</h5>
<script src="https://gist.github.com/SUPINKIM/c22bb3994fbc65d8a8eb3421cb6dea6b.js"></script>

<h5>구현 방법 2 - 보석 가치가 큰 기준으로 보석 배열 정렬하고 가방 무게는 오름차순으로 정렬한 뒤, 보석 배열 맨 앞에서부터 선택해 이진탐색으로 각 악세사리가 담길 수 있는 가방 크기를 구해서 더해주는 방법</h5>
<script src="https://gist.github.com/SUPINKIM/f4d14f4c72ea465a6ccd5d55679b6901.js"></script>


일단 몇 개의 테스트 케이스는 다 통과하는 코드이고, 혹시나 코드에서 오류를 발견하신다면 이 무지몽매한 필자에게 가르침을 주십시오..ㅠㅠ 빠른 시일 안에 코멘트 달 수 있게끔 블로그 설정 수정하겠습니다.
감사합니다~~
