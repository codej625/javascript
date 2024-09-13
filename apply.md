# 자바스크립트의 .apply() 메서드

<br /><br />

```
apply 메서드는 자바스크립트에서 함수의 메서드로,
함수를 호출할 때 this 값과 인수 배열을 설정하는 데 사용된다.

apply는 call과 비슷하지만, 인수를 배열 형태로 전달하는 점에서 다르다.


* apply는 성능상의 이유로 잘못 사용될 경우 느릴 수 있으며,
arguments 객체를 배열로 변환할 때 주의가 필요하다.
```

<br /><br /><br />

1. 기본 문법

```javascript
func.apply(thisArg, [argsArray]);

/**
 *
 * 1) func -> 호출할 함수
 *
 * 2) thisArg -> 함수 호출 시 this로 사용할 값
 *
 * 3) [argsArray] -> 함수에 전달할 인수들이 담긴 배열
 *
 */
```

```
* 주요 특징

1) this 컨텍스트 변경 -> thisArg로 지정한 값을 함수의 this로 설정

2) 배열 형태의 인수 -> argsArray로 전달된 배열의 요소들을 함수의 인수로 사용한다.
   배열 대신 null이나 undefined를 전달하면,
   함수는 인수가 없는 것처럼 동작한다.
```

<br /><br /><br />

1. 예시(메서드의 기본적인 사용)

```javascript
function greet(greeting, name) {
  console.log(greeting + ', ' + name + '!');
}

const args = ['Hello', 'Alice'];
greet.apply(null, args);  // Hello, Alice!

// 여기서 greet.apply(null, args)는 greet('Hello', 'Alice')와 같은 효과를 가진다.
```

<br /><br />

2. 예시(this 컨텍스트 변경)

```javascript
function describe() {
  console.log(this.name);
}

const person = { name: 'Bob' };

// describe 함수의 this를 person 객체로 설정
describe.apply(person);  // Bob
```

<br /><br />

3. 예시(활용)

```javascript
function debounce(func, delay) {
  let timer;

  return function () {
    const args = arguments; // arguments 객체를 사용해 인수를 저장 (여기서는 event 객체)
    clearTimeout(timer);

    timer = setTimeout(() => {
      func.apply(this, args); // 여기서 this는 debounce를 호출한 객체 즉, input
    }, delay);
  }
}

const input = document.querySelector({selector});
input.addEventListener('input', debounce(function(e) {
  console.log(e.target.value);
}, 200));
```
