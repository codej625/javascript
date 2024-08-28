# 클로저

<br /><br />

* 클로저의 특징
---

```
* 함수와 환경의 결합

클로저는 함수와 그 함수가 정의된 환경을 함께 캡처하여 저장한다.
따라서 함수가 호출될 때, 원래의 환경에 있던 변수들에 여전히 접근할 수 있다.
```

```
*데이터 은닉

클로저를 사용하면 외부에서 접근할 수 없는 데이터와 메서드를 캡슐화할 수 있다.
이를 통해 데이터와 메서드를 안전하게 보호하고, 외부의 영향을 최소화할 수 있다.
```

```
* 상태 유지

클로저는 함수가 호출된 이후에도 변수의 상태를 유지할 수 있다.
이는 클로저가 생성될 때의 환경을 기억하기 때문에 가능하며,
이를 통해 상태를 유지하면서 함수를 계속 사용할 수 있다.
```

<br /><br /><br />

1. 예시

```javascript
const counter = (function () {
  let privateCounter = 0;

  function changeBy(val) {
    privateCounter += val;
  }

  return {
    increment() {
      changeBy(1);
    },

    decrement() {
      changeBy(-1);
    },

    value() {
      return privateCounter;
    },
  };
})();

console.log(counter.value()); /* 0 */
counter.increment();
console.log(counter.value()); /* 1 */
counter.decrement();
console.log(counter.value()); /* 0 */
```

<br /><br />

2. 예시

```javascript
/* ex) */
function fetchData(callback) {
  setTimeout(function() {
    var data = 'This is the fetched data';
    callback(data);
  }, 2000); /* 2초 후에 실행 */
}

/* fetchData 함수 호출 및 클로저로 구성된 콜백 함수 전달 */
fetchData(function(data) {
  console.log('Fetched data:', data);
});
```

<br />

```
1) fetchData 함수는 비동기적으로 데이터를 가져오는 작업을 수행
   이 함수는 콜백 함수를 인자로 받아 데이터를 전달한다.
2) 비동기 작업이 완료되면 콜백 함수가 호출되어 데이터를 처리할 수 있다.
```

```
* 클로저의 역할

여기서 클로저의 역할은 콜백 함수로 전달된 익명 함수에 있다.
이 익명 함수는 외부 함수인 fetchData의 범위 내의 변수나 인자를 사용할 수 있다.
따라서 data 변수에 접근하여 비동기 작업으로부터 받은 데이터를 처리할 수 있게 된다.
```

<br /><br />

3. 예시

```javascript
const checkId = (() => {
  let save = '';

  return {
    get: function () { return save; },
    set: function (id) { return save = id; },
  }
})();

// #first 선택자 클릭 시 이벤트
document.querySelector('#first').addEventListener('click', () => {
  checkId.set('test');
});

// #second 선택자 클릭 시 이벤트
document.querySelector('#second').addEventListener('click', () => {
  console.log(checkId.get()); // test 출력
});
```

<br />

```
1) checkId라는 상수를 선언하고,
   그 값으로 즉시 실행 함수(IIFE)의 결과를 할당한다.

2) 즉시 실행 함수는 실행 후 객체를 반환하며,
   이 객체는 checkId에 할당된다.
```

```
* 클로저의 역할

즉시 실행 함수(IIFE) 내부에서는 save라는 변수를 선언하고 있다.
이 변수는 함수 외부에서 접근할 수 없지만,
함수 내부에서 정의된 메서드들(get과 set)은 이 변수를 계속해서 접근할 수 있다.
이로 인해 save 변수는 함수의 스코프를 벗어나도 여전히 유지된다.
```
