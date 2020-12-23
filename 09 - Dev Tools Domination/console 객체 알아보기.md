# console

> `console` 객체는 브라우저의 디버깅 콘솔에 접근할 수 있는 메서드를 제공합니다. 

### log(), info(), warn(), error()

![image-20201223220840004](console%20%EA%B0%9D%EC%B2%B4%20%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0.assets/image-20201223220840004.png)

```javascript
// Regular
console.log('기본')
// Info
console.info('정보')
// warning!
console.warn("경고")
// Error :|
console.error('에러 메세지')
// Interpolated
console.log('hellow I am a %s string!', '👨')
// Styled
console.log('%c styling!', 'font-size:50px; background:red')
```

### console.assert(true/false, message)

![image-20201223233232767](console%20%EA%B0%9D%EC%B2%B4%20%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0.assets/image-20201223233232767.png)

```javascript
// assert: 첫 번째 매개변수가 false면, 메시지와 스택 추적
const p = document.querySelector('p');

console.assert(p.classList.contains('ouch'), 'That is wrong!')
```



### console.groupCollapsed() / console.groupEnd()

`console.groupCollapsed()`:새로운 인라인 [그룹](https://developer.mozilla.org/ko/docs/Web/API/Console#그룹)을 생성해, 이후 모든 출력을 한 단계 들여씁니다. 그러나 `group()`과 달리, `groupCollapsed()`로 생성한 그룹은 처음에 접혀 있습니다. 그룹을 나오려면 groupEnd()를 호출하세요.



![image-20201223233509343](console%20%EA%B0%9D%EC%B2%B4%20%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0.assets/image-20201223233509343.png)

```javascript
// Grouping together
dogs.forEach(dog => {
    console.groupCollapsed(`${dog.name}`)
    console.log(`This is ${dog.name}`);
    console.log(`${dog.name} is ${dog.age} years old`);
    console.groupEnd(`${dog.name}`)
})
```



### console.log() vs console.dir()

`console.log`:정보 메시지를 출력합니다. 추가 매개변수와 함께 [문자열 치환](https://developer.mozilla.org/ko/docs/Web/API/Console#문자열_치환)을 사용할 수 있습니다. (`%s`:문자열 치환,  `%c`:css스타일링 부여)

`console.dir`: 주어진 JavaScript 객체의 속성 목록을 상호작용 가능한 형태로 표시합니다. 속성 값이 다른 객체라면 펼쳐서 살펴볼 수 있습니다.

![image-20201223233012098](console%20%EA%B0%9D%EC%B2%B4%20%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0.assets/image-20201223233012098.png)

```javascript
console.log(p)
console.dir(p)
```



### console.count(object)

- 주어진 레이블로 메서드를 호출한 횟수를 출력합니다.

![image-20201223233712813](console%20%EA%B0%9D%EC%B2%B4%20%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0.assets/image-20201223233712813.png)

```javascript
    // counting
    console.count('오');
    console.count('수');
    console.count('완');
    console.count('오');
    console.count('수');
    console.count('완');

```

### console.time() / console.timeEnd()

`console.time()`: 주어진 이름의 [타이머](https://developer.mozilla.org/ko/docs/Web/API/Console#타이머)를 실행합니다. 하나의 페이지에서는 최대 10,000개의 타이머를 동시에 실행할 수 있습니다.

`console.timeEnd()`: 지정한 [타이머](https://developer.mozilla.org/ko/docs/Web/API/Console#타이머)를 멈추고, 소요시간을 출력합니다.

- 코드 수행 시간을 확인할 때 유용!!
- 인자는 타이머의 이름! time과 timeEnd에 같은 타이머 이름을 주어야 정상적으로 작동합니다.



![image-20201223234106659](console%20%EA%B0%9D%EC%B2%B4%20%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0.assets/image-20201223234106659.png)



```javascript
// timing
console.time('fetching data');
fetch('https://api.github.com/users/wesbos')
    .then(data => data.json())
    .then(data => {
    console.timeEnd('fetching data');
    console.log(data);
})
```



[console에 이해](https://developer.mozilla.org/ko/docs/Web/API/Console)

[유용한 console 메서드](https://www.zerocho.com/category/JavaScript/post/5b2b45cf1350f9001b662ba6)