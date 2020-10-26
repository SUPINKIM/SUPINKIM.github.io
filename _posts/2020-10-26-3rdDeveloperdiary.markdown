---
layout: post
title:  "개발일지 3"
date:   2020-10-26
category : [Java,UXUI]

---


<h3><"아친-mbti로 아이돌 친구 찾기" 개발일지3_The end></h3>

오늘은 내가 제일 공을 들인 결과 페이지에 대해 이야기해보도록 하겠다.
중간 페이지인 mbti 선택 dropbox는 spinner를 이용해서 작성했고, spinner에 들어갈 값은 array 폴더에서 확인 가능하다.
<br>자신의 mbti를 모르는 경우에는 검사가 가능하도록 검사 웹 페이지를 연결했고, v 1.1에서 웹뷰로 코드를 수정했다.(back버튼을 눌렀을 시 다시 앱으로 돌아오게 하기 위해!)
<br>중간 로딩 부분도 오픈 소스를 가져다 사용했고, 색깔과 위치 정도만 커스터마이징 했으므로 깃에서 확인 바란다.<br>

[아친 개발 repository 보러 가기](https://github.com/SUPINKIM/MBTI_TEST.git)

<p>
<h4> 마지막 결과 페이지 </h4>
<br>
일단은 크게 두 부분으로 나누자면 "나와 잘 맞는 mbti 설명 부분"과 "해당 mbti를 가진 아이돌 카드뷰"라고 할 수 있다.<br>
두 부분 모두 recyclerview로 만들었고, 아이돌 카드뷰의 경우에는 카드뷰와 인디케이터 부분으로 나눌 수 있다. 일단 빠르게 제작하고 싶은 마음에 대다수의 화면 레이아웃을 짜는 코드는 오픈소스를 활용했다.<br>
다음에 또 모바일 애플리케이션을 제작하게 된다면 그 때는 개발 시간이 조금 더 걸리더라도 오픈 소스 사용을 최대한 자제하고 직접 코드를 짜는 방향으로 제작해보도록 하겠다.😂
<br>
mbti 설명의 경우에는 처음에는 설명이 보이지 않는 것을 default 화면으로 설정하고 개발했었는데 앱 배포 후 주변에서 사용하는 모습을 보니 
아이돌 카드뷰에 시선이 몰려 설명 부분을 전혀 눌러보지 않는 것을 확인하고 설명을 펼쳐보이는 것으로 변경하여 업데이트 했다.
<br>
카드뷰의 경우에는 일단 json파일에 아이돌 이름 및 그룹, 이미지, mbti 정보를 저장하고 각 mbti 별로 배열을 뽑아 배열 크기를 확인한 뒤 8보다 큰 경우 랜덤으로 8명만 추출하고 
8명보다 적은 경우는 전체 아이돌 출력하는 코드를 작성해 recyclerview와 연결했다. 중복을 막기 위해 for문을 중첩해 이전에 뽑힌 인덱스 값(j)과 현재 뽑힌 인덱스 값(i)이 동일하면 
i--를 해 다시 랜덤 인덱스를 뽑도록 코드를 작성했다.
</p> 

```
        ArrayList<MyData> list = (ArrayList<MyData>) intent.getSerializableExtra("allData");

        if(list.size()>8){ //8개 넘으면 개수 8개만
            Random random = new Random();
            int a[] = new int[8];

            for(int i=0; i<8; i++){
                a[i]=random.nextInt(list.size()); //랜덤으로 숫자 하나 생성
                for(int j=0;j<i;j++){
                    if(a[j]==a[i]){
                        i--;
                    }
                }
            }

            for(int i=0; i<8; i++){
                System.out.println(a[i]);
                myDataset.add(list.get(a[i]));
            }


        }
        else{  //8개보다 적으면 다 출력
            myDataset=list;
        }


        mAdapter = new MyAdapter(myDataset);
        mRecyclerView.setAdapter(mAdapter);


        SnapHelper snapHelper = new GravitySnapHelper(Gravity.CENTER);
        snapHelper.attachToRecyclerView(mRecyclerView);
```

해당 코드가 핵심이고, DB가 백업되면 개수를 더 많이 출력하는 방향으로 업데이트 할 수 있을 것이다.
<br>
최근에 프론트엔드 직무에 관심이 생겨 앞으로는 반응형 웹 제작 연습을 많이 하게 될 것 같다. 더불어 학부 때 친구들과 함께 헀던 편프로 웹 페이지를 새롭게 작성해보려고 한다. 
<br>파이썬 코드는 남아 있으니 ,,, 코드를 좀 손 봐서 더 괜찮은 웹 크롤러를 만들 수 있을 지도? ... html/css 공부를 하다보니 내가 학부 때 만들었던 웹 크롤러는 진짜 야매 중의 야매가 아니었나 
반성하게 된다. :) ...ㅎ... 앞으로도 더 개발 공부를 열심히 하는 내가 되길 바라며 아친 개발 일지는 여기서 마무리 한다! 안녕~ <br>

![ezgif com-video-to-gif](https://user-images.githubusercontent.com/49034615/97169851-181a2300-17ce-11eb-8797-2e541cbbace8.gif)
