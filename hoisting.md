# 호이스팅(Hoisting)

<br /><br />

```
변수를 선언하기 전에 참조할 수 있는 기능이다. 

자바스크립트는 코드 실행 전에 변수 선언을 끌어올리는(hoist) 동작을 수행하는데, 
변수의 초기화는 끌어올리지 않는다.
(실제 값이 할당되는 부분은 호이스팅되지 않기 때문에, 변수를 선언한 후에 그 값을 할당해야 한다.)
```

<br /><br /><br />

1. 변수, 함수 선언

```
var로 선언된 변수는 함수 스코프 또는 전역 스코프에서 호이스팅된다.

즉, 변수를 선언하기 전에 사용할 수 있다.
하지만 초기화는 호이스팅되지 않기 때문에, 변수는 undefined로 초기화된다.
```

<br />

```javascript
// var 사용 예시
console.log(myVar); // undefined
var myVar = 5;
console.log(myVar); // 5


// 함수 선언 예시
console.log(myFunc()); // Hello, World!
function myFunc() {
  return "Hello, World!";
}
```

<br /><br /><br />

2. let, const, function expression

```
ES6부터 도입된 let과 const는 블록 스코프를 가지며,
호이스팅되지만 초기화되지 않은 상태로 접근할 경우 ReferenceError가 발생한다.

+ 함수 표현식의 경우 변수에 대한 호이스팅은 있지만,
  초기화는 이루어지지 않아 undefined 상태로 남아 있기 때문에 에러 발생.
```

<br />

```javascript
// let, const 사용 예시
console.log(myLet); // ReferenceError
let myLet = 10;

console.log(myConst); // ReferenceError
const myConst = 20;


// 함수 선언식 예시
console.log(myFunction()); // TypeError

const myFunction = function() {
  return "Hello, World!";
};
// 함수는 변수에 할당됐기 때문에 위와 같이 선언 전에 호출하면 오류가 발생.
```
