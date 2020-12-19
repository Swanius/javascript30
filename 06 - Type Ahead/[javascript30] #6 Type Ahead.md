# [javascript30] #5 

### 결과 화면

![image-20201219180959140](%5Bjavascript30%5D%20#6%20Type%20Ahead.assets/image-20201219180959140.png)

### 진행 과정

1. fetch를 통해 데이터 받아오기

   - 데이터를 받을 배열 생성(cities)

   - 1000개의 데이터를 fetch를 통해 추출
   - `...data`를 하는 이유는 각 인덱스에 각 데이터를 받아오기 위함 !
     - `data`를 `push` 하면 cities[0]에 1000개의 데이터가 들어간다

![fetch_1](%5Bjavascript30%5D%20#6%20Type%20Ahead.assets/fetch_1.png)

![fetch_2](%5Bjavascript30%5D%20#6%20Type%20Ahead.assets/fetch_2.png)

2. `findMatches` - user가 기입한 input에 해당하는 `city || state`를 return 해 줄 함수 

![f_findMatches_numberwithCommas](%5Bjavascript30%5D%20#6%20Type%20Ahead.assets/f_findMatches_numberwithCommas.png)

3. `displayMatches`- `findMaches`에서 추출한 데이터 정제

   - regex - 유저가 기입한 input을 정규 표현식으로 변환
   - cityName, stateName을 span태그에 넣어줌
   - `numberWithCommas`함수를 통해 poplulation의 천 자리수에 `,`삽입

   - `join('')`으로 데이터 연결

     - 없을 경우, 추출한 데이터 사이 `,`로 분리됨

     ![image-20201219180807329](%5Bjavascript30%5D%20#6%20Type%20Ahead.assets/image-20201219180807329.png)

   - `suggestions.innerHTML = html` 구문으로 형식에 맞게 데이터 삽입

[Using_fetch](https://developer.mozilla.org/ko/docs/Web/API/Fetch_API/Fetch%EC%9D%98_%EC%82%AC%EC%9A%A9%EB%B2%95)

[정규표현식의_이해](https://heropy.blog/2018/10/28/regexp/)