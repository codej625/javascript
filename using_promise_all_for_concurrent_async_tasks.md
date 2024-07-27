# Promise.all을 활용하여 여러 개의 비동기 작업을 동시에 처리해보자.

<br /><br />

```
비동기 작업을 하다 보면 동시에 여러 개의 Promise 객체를 다뤄야 하는데,
이럴 때 Promise.all을 사용하면 비동기 작업을 동시에 여러 개 실행할 수 있다.
```

<br /><br /><br />

1. 예시

```javascript
const p1 = new Promise((resolve, reject) => setTimeout(resolve, 100, 'one')); // 세번째 인자는 호출하는 함수에 전달
const p2 = new Promise((resolve, reject) => setTimeout(resolve, 200, 'two'));
const p3 = new Promise((resolve, reject) => setTimeout(resolve, 300, 'three'));

Promise.all([p1, p2, p3])
  .then((results) => {
    console.log(results); // ['one', 'two', 'three']
  })
  .catch(err => { console.error(err); });
```

<br />

```
100ms, 200ms, 300ms 후에 완료되는 프로미스이다.
Promise.all을 사용하면,
모든 프로미스가 완료된 후 결과를 배열로 얻을 수 있다.
만약 하나라도 에러가 발생하면 catch 블록으로 넘어간다.
```

<br /><br /><br />

2. 예시2

```javascript
// 비동기 함수를 정의합니다.
async function fetchData() {
  try {
    // 여러 비동기 작업을 동시에 실행.
    const [response1, response2, response3] = await Promise.all([
      fetch('https://api.example.com/data1'),
      fetch('https://api.example.com/data2'),
      fetch('https://api.example.com/data3')
    ]);

    // 각 응답을 JSON으로 변환.
    const data1 = await response1.json();
    const data2 = await response2.json();
    const data3 = await response3.json();

    // 결과를 배열로 묶어서 출력.
    console.log([data1, data2, data3]);
  } 
  catch (err) { console.error('err -> ', err); }
}

// 비동기 함수를 호출합니다.
fetchData();
```

<br />

```
aysnc / await를 사용하여,
바동기 작업을 처리하는 로직이 더 직관적이고 읽기 쉬워졌다.
```

<br /><br /><br />

3. 예시3

```
Promise.all을 사용하면 모든 프로미스가 성공적으로 완료되어야 전체 결과를 받을 수 있다.
하나라도 실패하면 전체 프로미스가 실패한 것으로 간주되며,
나머지 프로미스들의 결과를 알 수 없다.

이 문제를 해결하기 위한 예시이다.
```

<br />

```javascript
const promises = [promise1, promise2, promise3]; // Promise를 모아놓은 배열

Promise.allSettled(promises)
  .then(results => {
    results.forEach(result => {
      if (result.status === 'fulfilled') {
        console.log('성공 -> ', result.value);
      } 
      else { console.log('실패 -> ', result.reason); }
    });
  });
```

<br />

```
Promise.allSettled는 모든 프로미스의 성공과 실패를 기다리고,
각 프로미스의 상태를 포함하는 결과를 제공한다.
프로미스가 성공했는지 실패했는지 모든 결과를 모두 알 수 있다.
```

<br />

```
* 반환 값

status -> 프로미스의 상태를 나타내는 문자열로 값은 'fulfilled' (성공) 또는 'rejected' (실패)이다.
value -> (성공한 경우에만 포함) 프로미스가 성공적으로 해결된 경우의 결과 값.
reason -> (실패한 경우에만 포함) 프로미스가 실패한 경우의 에러 원인.
```
```javascript
* fulfilled 예시
{
  "status": "fulfilled",
  "value": 42
}

* rejected 예시
{
  "status": "rejected",
  "reason": "Error occurred"
}
```
