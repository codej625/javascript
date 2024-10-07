# Destructuring assignment

<br /><br />

* 구조 분해 할당이란?
---

```
구조 분해 할당 구문은 배열의 값이나,
객체의 속성을 개별 변수로 풀어서 표현할 수 있는 JavaScript 표현식이다.
```

<br /><br /><br />

1. 예시1

```javascript
const obj = {
  name: 'codej625',
  age: 34
};

const { name, age } = obj;

console.log(name); // 'codej625'
console.log(age); // 34

// 변수명을 변경하는 것도 가능
const { name: name2, age } = obj;

console.log(name2); // 'codej625'
```

<br /><br />

2. 예시2

```javascript
let a, b, rest;
[a, b] = [10, 20];

console.log(a); // 10
console.log(b); // 20

[a, b, ...rest] = [10, 20, 30, 40, 50];

console.log(rest); // [30, 40, 50]
```
