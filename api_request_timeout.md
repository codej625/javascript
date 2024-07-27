# API 요청 시 타임아웃 기능을 구현해보자.

<br /><br />

```
API 요청 시 간혹 타임아웃을 강제해야 할 때가 있다.

이럴 때 Promise.race의 활용할 수 있다.
Promise.race는 여러 프로미스를 받아 가장 먼저 완료된 프로미스의 결과를 반환한다.
```

<br /><br /><br />

* 예시
---

```javascript
const result = Promise.race([
  fetch('/get-data-api'),
  new Promise((resolve, reject) => {
    setTimeout(() => reject(new Error('Timeout')), 5000); // 5초
  })
]);

result // 먼저 도착한 Promise를 사용
  .then(result => {
    console.log(result); // 타임아웃 전에 완료된 경우
  })
  .catch(err => {
    console.error(err.message); // 타임아웃 발생 시
  });
```
