---
layout: post
title: "코딩 기록 19"
date: 2021-01-12
category: [JavaScript]
---


<h4>프론트엔드 개발자로 취준하기 - 본격 스타트. 코딩테스트 준비 기록</h4>


✅ 공부하는 사이트 : 백준, 프로그래머스 (추후에 해커랭크나 코딜리티도 가입해서 공부할 계획 있음)

✅ 사용하는 프로그래밍 언어 : JavaScript(얼마 전까지 Python으로 준비하다가 프론트엔드 개발자는 JS로 시험 보는 경우도 많다고 하고 프론트엔드 개발자라면 응당 JS를 잘해야한다고 생각해서 JS로 준비중)

✅ 코딩테스트를 풀 때 고려해야 할 점 : 클린코딩(더 깔끔하게 쓸 수 없을까? / 가독성 ) / 인풋값의 범위(시간복잡도를 고려해 시간초과 당하지 않기 위해) / 공간 복잡도(변수나 배열을 생성해 저장하는 방법보다
최소한으로 저장하고 나머지는 입력 받고 계산한 뒤 다 버리는 식으로. ✔︎ 예. 변수 생성 없이 바로 return하기)



일단 코딩테스트를 준비해야겠다고 마음 먹은 이유는, 알고리즘과 자료구조에 대단한 자신감도 실력도 없기 때문이다. 최근에 개발자로 취직한 친구의 이야기도 그렇고 여기저기 다 검색해봐도
기본적인 코딩 테스트도 치룰 준비가 안 된 사람은 일을 구할 때도 일을 할 때도 많은 어려움에 직면할 것이라는 생각이 들었다. 그래서 기본적으로 코딩테스트에 주로 나오는 알고리즘들이 무엇인지
알고 최소 200문제 이상의 코딩테스트 문제들을 풀어보면서 감을 익힌 다음 5월이나 6월부터 본격적인 취준을 하면 어떨까 생각 중이다. 그 전에 더 열심히 준비해서 더 빨리 본격적으로 지원할 수 있다면
더 좋겠지만 :)

코딩테스트를 풀다 보니 수능 수학 공부했던 게 생각난다. 문제 풀이를 효과적으로 하기 위해 문제 풀이 오답노트 및 풀이 접근 방식에 대해 기록해두고 공부하려고 한다.



✔︎ 문제가 2차원 배열로 나온다든가 뭔가를 넣고 빼고 쌓는 식이라면(stack), 일단 행렬로 푸는 것일까 하고 적어보기

✔︎ 같은 방식으로 여러번 계산한다면 일단 재귀를 무조건 떠올리기

✔︎ 자료 구조 고민하기 : 어떤 값이 있고 고려해야 되는 조건이 두 개 이상이라면(예. 길이와 무게 모두 고려해야 하는 상황) object를 담은 array 생성을 고려해보기 [{key:value}]

✔︎ 정렬 문제를 풀 때는 시간 복잡도와 공간 복잡도를 기본적으로 생각하고 아예 기본적인 건 외워두기

✔︎ 배열 문제에서 전체 요소를 다 봐야 하는 게 아니라면 find api로 해당하는 값이 있다면 바로 리턴해서 시간 복잡도 줄이기

✔︎ 도형 문제가 나오면 일단 'y=ax'와 같은 형태로 좌표 위의 점과 기울기로 생각해보기

✔︎ 간단한 if-else 구조라면 삼항 연산자를 떠올려보기

