# 콜백 함수가 뭘까?

<br />

```
콜백 함수는 전달인자로 다른 함수에 전달되는 함수다.
이는 일종의 루틴이나 동작을 완료하기 위해 외부 함수 내부에서 호출된다.
```

```javascript
let value = 1;

doSomething(() => {
  value = 2;
});

console.log(value);
```

```
doSomething이 동기식으로 콜백을 호출하는 경우,
value = 2가 동기식으로 실행되기 때문에 마지막 코드 실행문(console.log 문)은 2를 기록한다.
그렇지 않고, 콜백 함수가 비동기인 경우
value = 2가 console.log 문 다음에 실행되기 때문에 마지막 코드 실행문(console.log 문)은 1를 기록한다.
```
