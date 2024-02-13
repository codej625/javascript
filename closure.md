# 클로저를 알아보자!

<br />

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

<br />

```javascript
/* ex) */

function tbody() {
  let tbody = null;

  function re() {
    tbody = document.querySelectorAll('#tbody tr');
  }
  function reload() {
    re();
  }
  function result() {
    return tbody;
  }
  
  return {
    reload: reload(),
    result: result()
  }
}

tbody().reload;
console.log(tbody().result);
```
```
tbody라는 변수값에 null을 대입해 초기화한다.
re()라는 내부 함수는 외부함수에 접근하여,
tbody 변수의 동적으로 변하는 요소의 값을 가져온다.
그리고 result라는 내부 함수를 통해 외부함수에 접근하여 tbody값을 반환한다.
외부함수에 반환 값으로는 내부 함수를 반환되게 한다.
```

<br />

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
```
fetchData 함수는 비동기적으로 데이터를 가져오는 작업을 수행한다.
이 함수는 콜백 함수를 인자로 받아 데이터를 전달한다.
비동기 작업이 완료되면 콜백 함수가 호출되어 데이터를 처리할 수 있다.

여기서 클로저의 역할은 콜백 함수로 전달된 익명 함수에 있다.
이 익명 함수는 외부 함수인 fetchData의 범위 내의 변수나 인자를 사용할 수 있다.
따라서 data 변수에 접근하여 비동기 작업으로부터 받은 데이터를 처리할 수 있게 된다.
```

<br />

```javascript
/* ex3) */
function outerFunction(outerVariable) {

  return function innerFunction(innerVariable) {
    console.log('outerVariable:', outerVariable);
    console.log('innerVariable:', innerVariable);
  }
}

const newFunction = outerFunction('outside');
newFunction('inside');  /* logs: outerVariable: outside, innerVariable: inside */
```
```
outerFunction은 함수를 반환하는 함수이다.
이 반환된 함수는 innerFunction이다.
outerFunction을 호출하면서 'outside'라는 값을 인자로 전달하면,
이 값은 outerVariable에 할당된다.

그런 다음, outerFunction은 innerFunction을 반환한다.
이 때 innerFunction은 outerVariable에 대한 참조를 유지하게 된다.
이것이 클로저의 핵심 개념이다.

따라서 newFunction은 이제 innerFunction을 참조하는 변수가 된다.
그리고 innerFunction은 outerVariable에 대한 참조를 유지하고 있다.

newFunction('inside')를 호출하면,
이는 사실상 innerFunction('inside')를 호출하는 것과 같다.
이 때 'inside'라는 값은 innerVariable에 할당 된다.
```
