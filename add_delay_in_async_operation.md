# 비동기 작업 중 지연시간을 넣는 방법

<br /><br />

```
비동기 작업을 하다 보면
의도적으로 중간에 지연시간을 넣어
다음 스크립트의 작동을 늦춰야 할 때가 있다.

그럴때 Promise 활용 방법이다.
```

<br /><br /><br />

```javascript
const delay = (ms) => {
  return new Promise(resolve => {
    console.log('지연 시작');
    setTimeout(resolve, ms);
  });
};
// const delay = (ms) => new Promise(resolve => setTimeout(resolve, ms));

const task = async () => {
  await delay(2000); // 2초 동안 대기
  console.log('지연 끝');
  // ... 로직
}

task();
```

<br />

```
위와 같은 방법으로 비동기 작업 시 지연시간을
의도적으로 주는 게 가능하다.
```
