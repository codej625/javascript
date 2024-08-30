# 함수에 전달된 인수(arguments)를 다루는 객체

<br /><br />

```
JavaScript 함수 내에서는 arguments라는 특별한 객체를 사용할 수 있다.
해당 객체는 모든 함수 내에서 이용 가능한 지역 변수의 모음이다.

함수 내에서 모든 인수를 참조할 수 있으며,
호출할 때 제공한 인수 각각에 대한 항목을 갖고 있다.

항목의 인덱스는 0부터 시작한다.
(유사 배열처럼 Array 객체를 사용해 변환 가능)
```

<br /><br /><br />

1. 예시

```javascript
// 예를 들어, 함수가 세 개의 인수를 받은 경우 다음과 같이 접근할 수 있다.

arguments[0];
arguments[1];
arguments[2];

// 각 인수를 설정하거나 재할당할 수도 있다.
arguments[1] = "new value";
```

<br /><br />

2. 예시 (Array 변환)

```javascript
1) const args = Array.from(arguments);

2) const args = [...arguments];
```

<br /><br />

3. 예시(매개 변수)

```javascript
function foo(...args) { // 객체가 아닌 값도 객체형식으로 표현
  return arguments;
}
foo(1, 2, 3); // { "0": 1, "1": 2, "2": 3 }
```

<br />

```javascript
// mapped 기본값이 있을 시 내부에서 대입된 값을 무시
function bar(a = 1) {
  arguments[0] = 100;
  return a;
}
bar(10); // 10


// mapped 기본값이 없을 시 내부에서 대입된 값을 허용
function zoo(a) {
  arguments[0] = 100;
  return a;
}
zoo(10); // 100
```
