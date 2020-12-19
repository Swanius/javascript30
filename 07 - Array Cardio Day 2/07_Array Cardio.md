# today's TIL

### Array.some() vs Array.prototype.every()
```javascript
const people = [
  { name: 'Wes', year: 1988 },
  { name: 'Kait', year: 1986 },
  { name: 'Irv', year: 1970 },
  { name: 'Lux', year: 2015 }
];
```
- `some`
  - 배열(or 객체들)에서 하나만 참 => true
  - 배열(or 객체들)에서 모두가 거짓 => false
```javascript
const isAdult = people.some(function(person) {
  const currentYear = (new Date()).getFullYear();
  if(currentYear - person.year >= 19) {
    return true;
  }
});
console.log({isAdult}) // {isAdult:true}

//or

const isAdult = people.some(person => ((new Date()).getFullYear()) - person.year >= 19);

console.log({isAdult}); // {isAdult:true}
```
- `every`
  - 배열(or 객체들)에서 모두가 참 => true
  - 배열(or 객체들)에서 some이 참(or 모두가 거짓) => false
```javascript
const allAdults = people.every(person => ((new Date()).getFullYear()) - person.year >= 19);
console.log({allAdults}); // {allAdult:false}

```

### Array.prototype.find() vs Array.prototype.findIndex()
```javascript
const comments = [
  { text: 'Love this!', id: 523423 },
  { text: 'Super good', id: 823423 },
  { text: 'You are the best', id: 2039842 },
  { text: 'Ramen is my fav food ever', id: 123523 },
  { text: 'Nice Nice Nice!', id: 542328 }
];
```
- `find`
  - 배열에서 첫번째 요소의 값을 반환. 그런 요소가  없다면 `undefined`반환
```javascript
const comment = comments.find(comment => comment.id === 823423);

console.log(comment) // {text: 'Super good', id: 823423}

```
- `findIndex`
  - 배열에서 첫번째 요소의 index를 반환. 그런 요소가 없다면 `-1`반환
```javascript
const index = comments.findIndex(comment => comment.id === 823423);
console.log(index); // 1
```

### Array.prototype.splice() vs Array.prototype.slice()
- `splice`
  - 배열에서 index에 요소를 추가하거나 갯수만큼 요소 삭제.
  - splice(start, deleteCount, item1, item2)
```javascript
comments.splice(index, 0, {text:'javascript', id:123456}) // 아무것도 삭제 x, index에 새로운 요소 삽입
comments.splice(index, 1); //index부터 요소 1개 삭제
comments.splice(index) //index를 포함한 이후의 모든 요소 삭제
```

- `slice`
  - 시작 인덱스부터 끝 인덱스까지 해당 배열을 얕은 복사하여 새로운 배열 반환
```javascript
const newComments = [
  ...comments.slice(0, index), // { text: 'Love this!', id: 523423 }
  ...comments.slice(index + 1) // 위의 comments[0] + comments[2:]
  // { text: 'Love this!', id: 523423 }, === idx0
  // { text: 'You are the best', id: 2039842 }, === idx2
  // { text: 'Ramen is my fav food ever', id: 123523 }, === idx3
  // { text: 'Nice Nice Nice!', id: 542328 }  === idx4
];
```
### 참고
[Array.prototype.some()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/some)

[Array.prototype.every()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/every)

[Array.prototype.find()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/find)

[Array.prototype.findIndex()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)

[Array.prototype.splice()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)

[Array.prototype.slice()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)

