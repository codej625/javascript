# 자바스크립트 숏 코딩

<br /><br />

```
자바스크립트에서 자주 쓰이는 숏 코딩 예시를 보며,
코드를 줄여보자.
```

<br /><br /><br />

1. true, false 반환 시 활용

```javascript
// Original code

function isPositive(num) {
  if (num > 0) {
    return true;
  } 
  else {
    return false;
  }
}
```

<br />

```javascript
// Short

function isPositive(num) {
  return num > 0;
}
```

<br /><br /><br />

2. true, false 반환 시 활용(2)

```javascript
// Original code

const result = value ? true : false;
```

<br />

```javascript
// Short

const result = !!value;
```

<br /><br /><br />

3. 객체의 메서드

```javascript
// Original code

const person = {
  name: "codej625",
  greet: function() {
    console.log('hello ' + this.name);
  }
}
```

<br />

```javascript
// Short

const person = {
  name: "codej625",
  greet() {
    console.log('hello ' + this.name);
  }
}
```

<br /><br /><br />

4. 화살표 함수 활용

```javascript
// Original code

const add = function(a, b) {
  return a + b;
}
```

<br />

```javascript
// Short

const add = (a, b) => a + b;
```

<br /><br /><br />

5. 구조 분해 할당

```javascript
// Original code

const person = { name: 'codej625', age: 34 };
const name = person.name;
const age = person.age;
```

<br />

```javascript
// Short

const person = { name: 'codej625', age: 34 };
const { name, age } = person;
```

<br /><br /><br />

5. 옵셔널 체이닝과 Null 병합 연산자

```javascript
// Original code

const user = null;
const userName = user !== null && user !== undefind ? user.name : 'Guest';
```

<br />

```javascript
// Short

const user = null;
const userName = user?.name ?? 'Guest'; // Optional Chaining 과 Nullish Coalescing
```

<br /><br /><br />

6. || 연산자 사용

```javascript
// Original code

// 레거시버전 (ES5)
const inputValue = null;

if (inputValue) {
  console.log('truthy');
}
else {
  console.log('falsy');
}
```

<br />

```javascript
// Short

const inputValue = null;

// ||는 논리 연산자로, 왼쪽 값이 falsy(즉, null, undefined, false, 0, NaN, '' 등)라면 오른쪽 값을 사용한다.
const userInput = inputValue || 'Falsy';

console.log(userInput); // 'Falsy'
```
