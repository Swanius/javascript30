## Key Event

- window객체를 이벤트 리스너로 조작 및 `keyup`이벤트 활용

window객체를 이벤트 리스너로 조작하면 브라우저 상에서 다양한 이벤트를 발생 시킬 수 있음

```javascript
window.addEventListener('keyup', (e) => {
    console.log(e.key)
```

keyup은 키보드를 눌렀을 경우 발생하는 이벤트로 위 처럼 console.log를 통해 이벤트 `e`의 key 속성을 통해 누른 결과를 볼 수 있음

- `splice` 활용법

```javascript
const pressed = []
const secretCode = 'swanious'
// secretCode의 길이보다 pressed배열의 길이가 늘어나면, pressed배열의 0번째 인덱스 삭제
// queue와 비슷한 방식이라고 보면 됨
pressed.splice(-secretCode.length - 1, pressed.length - secretCode.length)
```

```python
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Key Detection</title>
  <script type="text/javascript" src="https://www.cornify.com/js/cornify.js"></script>
</head>
<body>
<script>
  const pressed = []
  const secretCode = 'swanious'
  window.addEventListener('keyup', (e) => {
    console.log(e.key)
    pressed.push(e.key)
    pressed.splice(-secretCode.length - 1, pressed.length - secretCode.length)
    if (pressed.join('').includes(secretCode)) {
      console.log('Correct!!')
      cornify_add()
    }
    console.log(pressed)
  });
</script>
</body>
</html>

```

## cookie policy `SAMESITE=LAX`

위의 코드를 진행하다보니 Issues 메시지를 받게됐다. 

이게 뭐지.. 처음보는건데..라고 생각해보며 하나씩 찾아봤다.

![image-20210106213342334](keyEvent%20&%20cookie%20policy.assets/image-20210106213342334.png)

위의 내용을 봐도 당최 무슨 내용인지 자세히 알 도리가 없어서 누가봐도 중요한 것처럼보이는 `samesite=strict`와 `samesite=Lax`에 대해 찾아봤다.

그렇게 [web.dev](https://web.dev/samesite-cookies-explained/?utm_source=devtools) 라는 사이트에서 cookie에 대한 정책을 자세히 설명해놨길래 참고했다. 

쿠키는 웹 사이트에 어떠한 상태를 유지시키는데 사용할 수 있는 방법 중 하나인데, 예를 들면,

1. 사용자에게 "새로운 기능"프로모션을 표시하려는 블로그
2. 로그인 세션
3. 쿠팡, 11번가, 위메프 등 다양한 e-commerce 사이트의 장바구니(비 로그인 상태에서 장바구니 유지)

등이 존재할 수 있다.

위의 웹 사이트만 해도 쿠키 허용에 대한 알림창을 볼 수 있었다.

![image-20210106214605388](keyEvent%20&%20cookie%20policy.assets/image-20210106214605388.png)



이처럼 웹 사이트를 방문하면 동일한 페이지에서 다양한 도메인의 쿠키가 발생하는 경우를 종종 발견할 수 있다. 이렇듯 동일한 페이지에서의 cookie의 정책은 크게 세 가지로 분류할 수 있는데, 아래와 같다.

1. samesite = None
2. samesite = Lax
3. samesite = Strict

- `samesite = None`

  웹 사이트(도메인)가 다른 경우에도 쿠키를 전송합니다. Chrome 80의 새로운 기능으로 SameSite를 None으로 설정할 경우 쿠키에 암호화된 HTTPS 연결이 필요함을 나타내는 Secure 특성을 태깅해야 합니다.

- `samesite = Lax`

  GET 요청과 같은 특정한 경우에만 쿠키를 전송합니다.

- `samesite = Strict`

  이름에서 알 수 있듯이 SameSite 규칙이 엄격하게 적용되는 옵션입니다. 해당 옵션으로 설정되면 도메인이 다를 경우 쿠키를 서버로 전송하지 않습니다.

위 처럼 간단하게 요약할 수 있지만, 아래의 사이트를 더 보고 공부해보는 것이 좋겠다.

[web.dev](https://web.dev/samesite-cookies-explained/?utm_source=devtools)

[쿠키 정책에 대한 이해](https://sevendollars.tistory.com/178)

