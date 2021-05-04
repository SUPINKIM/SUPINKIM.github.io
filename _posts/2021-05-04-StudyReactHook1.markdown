---
layout: post
title: "Context API in React"
date: 2021-05-04
category: [React]
---

<h4>Context API with React Hook (ft.nomad coders)</h4>

vue.js로 진행하려던 프로젝트가 무산되고 새롭게 React.js를 활용해 여행 블로그 사이트(+todo, diary)
작업을 진행 중이다. 팀원 분들이 다들 열심히 해주셔서 다행히 이번 프로젝트는 끝까지 잘 마무리 될 것 같다는 좋은 예감이 든다. 
일단 1주차에는 블로그 화면을 만들었고 이번 2주차에는 todolist 화면을 각자 나눠 작업하기로 했는데
생각보다 블로그보다 손이 많이 갈 것 같다는 예감이 들어서 부지런히 공부해서 코드를 작성해야 될 것 같다.

구현할 기능 중 로그인 기능이 있으므로, 아직 구현하지는 않았지만 유저 정보를 받아와 전체 모든 페이지에서 필요한 데이터를 받아와 렌더링 해야 하므로 
context api를 활용해야 할 것 같다. 미리 공부하자는 마음에서 프로젝트 병행과 동시에 틈틈이 react와 관련해서 공부한 것들을 정리해 보고자 한다.

##### Context API와 useContext
###### 상태 관리 라이브러리의 필요성
 
 - 로그인 한 유저 정보를 필요로 하는 화면이 여러 개라면, 이 때 매번 API를 불러오는 것이 아니라 하나의 component에서 유저 정보를 불러온 뒤 저장해 놓고 필요할 때마다 props로 전달해주는 것이 효율적이다.
 - 여러 개의 컴포넌트가 계층 구조로 이루어져 있을 때, 최상위 컴포넌트에서 최하위 컴포넌트(해당 정보를 실제로 사용하는)로 전달한다고 가정하자. 
   이 때 컴포넌트의 개수가 5개, 6개 혹은 그 이상으로 props를 전달해줘야 한다면 해당 데이터를 사용하지 않음에도 불구하고 거쳐야 하는 컴포넌트 개수가 많아 가독성을 떨어뜨리고 비효율적으로 코드를 작성하게 된다. 
   이를 방지하기 위해서 state management(redux 등)의 필요성이 생겼다.
 - 기존에는 redux 등 잘 만들어진 상태 관리 라이브러리를 따로 사용했지만, Context API의 성능이 좋아지면서 굳이 Redux를 쓰지 않아도 커버할 수 있는 기능이 많아졌다.


<script src="https://gist.github.com/SUPINKIM/69546cdac7e3fc57e66c34e29e990fbe.js"></script>

<script src="https://gist.github.com/SUPINKIM/d89b36c35137a9c589710ca6f3287c41.js"></script>

<script src="https://gist.github.com/SUPINKIM/3e00aa11d54b460e81533b071e2ff1d0.js"></script>


<b>여기서 주의할 점은 다른 컴포넌트에서 useContext(defaultContext)를 사용할 때 defaultContext는 반드시 React.createContext()로 생성된 객체를 불러와서 사용해야 한다.
defaultContext.Provider 또는 defaultContext.Consumer는 틀린 사용이라고 공식문서에 명시되어 있음!</b>

- (공식문서 tip) "useContext(MyContext)는 클래스에서의 static contextType = MyContext 또는 <MyContext.Consumer>와 같다고 보면 됩니다." 

fin.
