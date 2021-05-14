---
layout: post
title: "simple infinite-scroll 만들어보기 with Intersection Observer API"
date: 2021-05-14
category: [JavaScript]
---

#### IneterSection Observer API를 활용한 간단 무한 스크롤 예제 만들기

프로그래머스 과제관에서 고양이 검색 사진 사이트 만들기 테스트 문제를 풀다보니 lazy load라는 개념과 무한 스크롤 구현에 대한 문제를 보게 되었다.
이 두 개념 이외에도 내가 딱 문제를 읽자 마자 구현하는 방법이 쉽게 떠오른 지점이 있었냐 하면 거의 없었다가 맞을 것 같다. 정말 코딩의 세계는 넓고 내가 아직도 많이 부족하다는 것을 실감하게 된다.

lazy load는 찾아보니, 주로 인스타그램과 같은 이미지 게시물이 많은 경우 이미지 리소스를 서버에서 한 번에 받아오는 것이 아니라 사용자에게 보이는 부분만 리소스를 받아와 보여주고
그 외의 부분은 사용자가 스크롤을 내리거나 선택하는 등 어떠한 액션이 있어 viewport가 바뀌면 다시 그 부분을 받아오는 식으로 동작하는 것을 말하는 것 같다. lazy load도 구현하는 방식이 여러 개이고
이전에 많은 양의 이미지를 처리하는 작업을 해본 적이 없어 한 번에 이해가 잘 가진 않았다. 그래서 lazy load 부분은 좀 더 시간을 두고 천천히 공부해야 할 것 같다.

무한 스크롤의 경우 역시 이 전에 한 번도 구현한 적은 없지만 이번에 블로그 프로젝트를 진행하면서 블로그 포스팅 개수가 많아지면 한 번에 전체 블로그 포스트를 다 불러 오는 것이 아니라 단위를 끊어서
서버에 데이터를 요청하도록 비동기 방식으로 구현해야 되지 않나 하는 생각이 들었고, 참고 사이트로 보았던 브런치 역시 그런 식으로 무한 스크롤을 구현하고 있는 것 같아 머지 않아 구현해야 할 기능이라 판단해
간단한 예제를 통해 원리를 이해해 보고자 했다.


##### Intersection Observer란
- Intersection Observer API는 타겟 요소와 상위 요소 또는 최상위 document 의 viewport 사이의 intersection 내의 변화를 비동기적으로 관찰하는 방법입니다.(출처 [MDN](https://developer.mozilla.org/ko/docs/Web/API/Intersection_Observer_API))

즉, 관찰 대상이 있고 그 관찰 대상과 비교 기준이 되는 요소는 그 관찰 대상의 상위 요소 또는 최상위 요소(option의 root 요소를 지정해 주지 않으면 기본적으로 브라우저 viewport 값이 비교 기준이 된다.)
```
let observer = new IntersectionObserver(callback, options);
```
IntersectionObserver가 갖는 매개 변수는 2가지이다. callback function과 option. 

option에는 3가지를 정의해 줄 수 있다. 
1. root : 비교 기준 ex. document.querySelector('ul')
2. rootMargin : root의 margin 속성
3. threshold : callback 함수의 호출 시점을 조작할 수 있는 요소. 콜백이 실행될 대상 요소가 현재 비교 대상 내에서 얼마큼 보여질 때 callback 함수를 호출할 것이냐를 0~1사이의 값으로 정해줄 수 있음.

callback 함수는 entry,observer 2가지 매개 변수를 기본적으로 가진다.
1. entry : 관찰 대상 정보 => array를 반환(관찰 대상이 여러 개일 수 있으므로 각 관찰 대상 속성이 array의 요소들)하므로 그 안의 속성값을 사용할 때는 entry[0].target과 같은 방식으로 사용해야 함.
2. observer : IntersectionObserver 참조 객체 

entry.target 내의 isIntersecting(boolean) 속성을 통해 현재 두 대상이 교차하고 있는지 아닌지 확인할 수 있음.

구현한 코드는 스크롤 시 ul 내 li 요소를 무한하게 생성하도록 간단하게 구현해보았다. 두 개의 코드 모두 결과 값은 동일하며 브라우저 viewport와 ul요소, li요소들 중 어떤 것을 비교 대상과 관찰 대상으로 삼았는가의 
차이만 있을 뿐이다. 

<script src="https://gist.github.com/SUPINKIM/7eef1cb296ffd4866c75cedfa7ab18bd.js"></script>
<script src="https://gist.github.com/SUPINKIM/6dc79c221ed04a540bd251016e4eb58e.js"></script>
