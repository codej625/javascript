# Event object

<br /><br />

```
자바스크립트 이벤트 객체는 브라우저에서 발생하는 이벤트에 대한 정보를 담고 있는 객체이다.

이벤트가 발생할 때, 이 객체가 생성되어 이벤트 핸들러에 전달된다.
이벤트 객체를 통해 이벤트의 세부 정보에 접근할 수 있다.
```

<br /><br /><br />

1. type

```
발생한 이벤트의 종류를 나타낸다.
("click", "keydown" 등)
```

<br />

2. target

```

이벤트가 발생한 DOM 요소를 참조한다.

```

<br />

3. currentTarget

```
현재 이벤트 핸들러가 바인딩된 요소를 참조한다.
(이벤트 캡처링이나 버블링 중에 다를 수 있다.)
```

<br />

4. preventDefault()

```
기본 동작을 막는다.
예를 들어, 링크 클릭 시 페이지 이동을 방지할 수 있다.
```

<br />

5. stopPropagation()

```
이벤트 전파를 중단한다.
이는 이벤트가 더 이상 부모 요소로 전파되지 않도록 한다.
```

<br />

6. clientX, clientY

```
마우스 이벤트의 경우,
클릭한 위치의 X, Y 좌표를 반환.
```

<br /><br /><br />

* 예시
---

```javascript
document.getElementById('myButton').addEventListener('click', function(event) {
  console.log('Button clicked!');
  console.log('Event type ', event.type);
  console.log('Target element ', event.target);
  
  // 기본 동작 방지
  event.preventDefault();
});
```
