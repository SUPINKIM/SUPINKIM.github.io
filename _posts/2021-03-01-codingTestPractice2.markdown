---
layout: post
title: "[코딩테스트 문제풀이] Programmers 이중우선순위큐"
date: 2021-03-01
category: [JavaScript]
---

<h4>[프로그래머스] 이중우선순위큐</h4>

<h5>문제</h5>
![스크린샷 2021-03-01 오후 7 50 22](https://user-images.githubusercontent.com/49034615/109488558-125c8300-7ac9-11eb-8a24-9ba6e6ed7b9b.png)


<h5>접근 방식</h5>
오늘은 간단한 문제 하나를 들고 왔다. 문제 분류는 힙(heap)으로 되어 있지만, 힙에 대해서 잘 몰랐던 나는 일단 <b>이진 탐색</b>이 바로 떠올랐고 30분 안짝으로 풀었다.
그래도 문제의 의도대로 풀어야지 하고 힙에 대해서 공부한다음 Max Heap까지는 구현하였지만, Heap의 성질이 부모 노드가 자식 노드보다 크거나 같기만 하면 되고 같은 부모 노드의 자식 노드끼리는
원래 값을 비교해 줄 필요가 없기 때문에 거기서 다시 sort를 하려면 코드가 더 필요하고, 노드 삽입과 삭제 구현 역시 더 추가 코드가 필요했으므로 결국 나는 Max heap을 구현한 것에
만족하고 heap sort로 구현하는 것은 포기.


<h5>정답 코드</h5>
<script src="https://gist.github.com/SUPINKIM/5901c13948e7148840a4a99c52f941a3.js"></script>

이진 탐색으로 풀었기 때문에 시간 복잡도도 O(logN)이다.

<h6> * 시간 복잡도</h6>
![스크린샷 2021-03-01 오후 3 13 57](https://user-images.githubusercontent.com/49034615/109488350-cc9fba80-7ac8-11eb-8efa-c47ff5e3c325.png)
