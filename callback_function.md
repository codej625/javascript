# 콜백 함수(Callback function)

<br /><br />

```
콜백 함수는 다른 함수의 인자로 전달되어 호출되는 함수를 말한다.
(특정 작업이 완료된 후, 실행할 코드를 정의하는 방법)
```

<br /><br /><br />

1. 기본적인 콜백 함수

```javascript
function greet(name) {
  console.log(`Hello, ${name}`);
}

function processUserInput(callback) {
  const name = 'codej625';
  callback(name); // greet 함수를 호출
}

processUserInput(greet); // Hello, codej625
```

<br /><br />

2. 비동기 작업에서의 콜백

```javascript
function fetchData(callback) {
  setTimeout(() => {
    const data = { id: 1, title: 'callback' };
    callback(data); // 데이터가 준비되면 콜백 호출
  }, 1000);
}

fetchData((data) => {
  console.log('Fetched data:', data); // 1초 후에 실행
});
```

<br /><br />

3. 모듈화 및 재사용성

```javascript
function processUserInput(callback) {
  const name = 'Alice';
  callback(name); // 사용자 입력을 처리하는 콜백
}

processUserInput((name) => {
  console.log(`Hello, ${name}!`); // 다른 곳에서도 동일한 콜백을 사용할 수 있음
});

// 다른 작업에 대해 같은 콜백을 재사용
processUserInput((name) => {
  console.log(`Welcome, ${name}!`);
});
```

<br /><br /><br />

```
콜백 함수는 비동기 프로그래밍(서버에서 데이터를 가져오거나 파일을 읽는 등의 작업이 완료된 후 실행),
이벤트 처리에서 자주 사용된다.

또한 함수를 모듈화하여 재사용성을 높일 수 있다.
```
