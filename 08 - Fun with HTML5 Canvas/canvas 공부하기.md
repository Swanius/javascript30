# canvas 공부하기

### window 화면 사이즈

**window.innerWidth** : 창 틀을 뺀 스크롤을 포함한 너비 (현재 보이는 화면)
**window.innerHeight** : 창 틀을 뺀 스크롤을 포함한 높이
**window.outerWidth** : 창 틀 포함 너비
**window.outerHeight** : 창 틀 포함 높이



body가 전체의 크기와 같을 때, 전체 스크롤의 높이

- `document.body.clientHeight`
- `document.body.offsetHeight`
- `document.body.scrollHeight`



### canvas 생성

```javascript
// html에 canvas(id="draw)가 있을 경우
const canvas = document.querySelector('#draw')
const ctx = canvas.getContext('2d')

// canvas가 없을 경우 => 새로 생성
const canvas = document.createElement('canvas')
canvas.setAttribute('id', 'draw')
document.body.appendChild(canvas)
const ctx = canvas.getContext('2d')
</script>
```



### 스타일 및 속성 적용

#### 도형 색상

**fillStyle**

`fillStyle = color` : 도형을 채우는 색을 설정

```javascript
function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');
  for (var i = 0; i < 6; i++){
    for (var j = 0; j < 6; j++){
      ctx.fillStyle = 'rgb(' + Math.floor(255 - 42.5 * i) + ', ' +
                       Math.floor(255 - 42.5 * j) + ', 0)';
      ctx.fillRect(j*25,i*25,25,25);
    }
  }
}
```

![image-20201220224559429](canvas%20%EA%B3%B5%EB%B6%80%ED%95%98%EA%B8%B0.assets/image-20201220224559429.png)

**strokeStyle**

```javascript
function draw() {
  var ctx = document.getElementById('canvas').getContext('2d');
  for (var i = 0; i < 6; i++) {
    for (var j = 0; j < 6; j++) {
      ctx.strokeStyle = 'rgb(0, ' + Math.floor(255 - 42.5 * i) + ', ' +
                       Math.floor(255 - 42.5 * j) + ')';
      ctx.beginPath();
      ctx.arc(12.5 + j * 25, 12.5 + i * 25, 10, 0, Math.PI * 2, true);
      ctx.stroke();
    }
  }
}
```

![image-20201220224550579](canvas%20%EA%B3%B5%EB%B6%80%ED%95%98%EA%B8%B0.assets/image-20201220224550579.png)

- 같은 색, 다른 표현

```javascript
ctx.fillStyle = "orange";
ctx.fillStyle = "#FFA500";
ctx.fillStyle = "rgb(255, 165, 0)";
ctx.fillStyle = "rgba(255, 165, 0, 1)";
```



#### 선 스타일

**lineWidth** - 선 두께 지정 ( 기본 1.0 ) 

![image-20201220224922631](canvas%20%EA%B3%B5%EB%B6%80%ED%95%98%EA%B8%B0.assets/image-20201220224922631.png)

**lineCap **- 선 끝 부분의 스타일 지정 ( butt, round, square )

![image-20201220224939572](canvas%20%EA%B3%B5%EB%B6%80%ED%95%98%EA%B8%B0.assets/image-20201220224939572.png)

**lineJoin** - 선이 꺽이는 부분의 스타일 지정 (bevel, round, miter)

![image-20201220225001380](canvas%20%EA%B3%B5%EB%B6%80%ED%95%98%EA%B8%B0.assets/image-20201220225001380.png)

### 경로 그리기

경로를 이용하여 도형을 만들 때에는 몇가지 단계를 거쳐야 함

1. 경로 생성
2. 그리기 명령어를 사용하여 경로상에 그리기
3. 경로가 한번 만들어졌다면, 경로를 렌더링 하기 위해서 윤곽선을 그리거나 도형 내부를 채울 수 있음

**beginPath()** - 새로운 경로를 만듬

**closePath()** - 현재 하위 경로의 시작 부분과 연결된 직선을 추가

**stroke()** - 윤곽선을 이용하여 도형을 그림

**fill()** - 경로의 내부를 채워서 내부가 채워진 도형을 그림



### 선

**lineTo(x, y)** - 현재의 드로잉 위치에서 x와 y로 지정된 위치까지 선을 그림

**moveTo(x, y)** - 펜을 해당 x, y좌표로 옮긴다.

```javascript
function draw() {
  var canvas = document.getElementById('canvas');
  if (canvas.getContext) {
    var ctx = canvas.getContext('2d');

    // Filled triangle
    ctx.beginPath();
    ctx.moveTo(25, 25);
    ctx.lineTo(105, 25);
    ctx.lineTo(25, 105);
    ctx.fill();

    // Stroked triangle
    ctx.beginPath();
    ctx.moveTo(125, 125);
    ctx.lineTo(125, 45);
    ctx.lineTo(45, 125);
    ctx.closePath();
    ctx.stroke();
  }
}
```

![image-20201220230907118](canvas%20%EA%B3%B5%EB%B6%80%ED%95%98%EA%B8%B0.assets/image-20201220230907118.png)

[canvas_스타일과 색 적용하기](https://developer.mozilla.org/ko/docs/Web/HTML/Canvas/Tutorial/Applying_styles_and_colors)

[선 스타일 지정하기](https://m.blog.naver.com/PostView.nhn?blogId=javaking75&logNo=140170244058&proxyReferer=https:%2F%2Fwww.google.com%2F)

