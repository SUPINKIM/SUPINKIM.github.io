---
layout: post
title: "Segment Tree : 세그먼트 트리"
date: 2021-09-13
category: [JavaScript]
---

### Segment Tree 

세그먼트 트리 : 완전 이진 트리에 기반한 자료 구조. 주로 구간합이나 특정 구간 내에서 최솟값 or 최댓값을 구해야 하는 경우 사용하면 용이.

<br>

세그먼트 트리를 이용한 구간합 트리 
  
  : 각 노드의 value는 하위 노드들(즉, 각 노드는 서브 트리의 root)의 value의 합이다.
  
  : 재귀로 구현 가능

<br>
<br>
추천 문제
  
- [백준 온라인 저지 2357. 최솟값과 최댓값](https://www.acmicpc.net/problem/2357)
  
- [백준 온라인 저지 2042. 구간합](https://www.acmicpc.net/problem/2042)

<details>
<summary>2357. 최솟값과 최댓값 문제 풀이 공유</summary>
<div markdown="1">       
  <script src="https://gist.github.com/SUPINKIM/3822c98762e0a0cd48a11c6e9aa926b1.js"></script>
</div>
</details>
