# 화살표 함수에 대해 알아보자!

<br/>

1. 매개변수 목록 괄호 생략하기
```
화살표 함수가 정확히 하나의 매개변수만 사용하는 경우, 묶는 괄호를 생략할 수 있다.
```

```javascript
(userName) => { ... } 가 아니라

userName => { ... } 라고 쓸 수 있다.
```

```javascript
*참고

함수에 매개변수가 없는 경우에는, 괄호를 생략해서는 안 된다.

() => { ... } 라고 써야 한다.

함수가 둘 이상의 매개변수를 받는 경우에도 괄호를 생략해서는 안 된다.
```

```javascript
userName, userAge => { ... }   X

(userName, userAge) => { ... } O
```

<br/>

2. 함수 본문 중괄호 생략하기
```
화살표 함수에 반환문 외에 다른 로직이 없는 경우, return키워드와 중괄호를 생략할 수 있다.
```
```javascript
number => { return number * 3; } 라고 쓰는 게 아니라

number => number * 3; 라고 쓸 수 있다.
```

```javascript
만약,

number => return number * 3; 이 경우 retrun 키워드는 생략되어야 하므로, 오류가 생긴다.

number => if (number === 2) { return 5 }; 이 경우 if 문은 반환될 수 없으므로 오류가 생긴다. 
```

<br/>

3. 특수한 경우: 객체만 반환하는 경우
```
위에서 설명한 짧은 대안으로 자바스크립트 객체를 반환하려고 하면, 다음과 같이 유효하지 않은 코드가 나올 수 있다.
```

```javascript
number => {age: number}; 객체를 반환하려고 한다.
자바스크립트는 중괄호를 JS 객체를 생성하는 코드가 아닌 함수 본문 래퍼로 취급하기 때문에 이 코드는 유효하지 않다.
```

```javascript
객체를 생성하고 반환해야 한다고 자바스크립트에 "말하려면" 코드를 다음과 같이 수정해야 한다.

number => ({ age: number }); // 추가로 소괄호를 써서 객체를 감싼다.

객체와 중괄호를 소괄호로 감싸면,
자바스크립트는 중괄호가 함수 본문을 정의하는 것이 아니라 객체를 생성하기 위한 것임을 이해하고, 객체가 반환 된다.
```

```
*참고

조금 더 자세히 본문에서 소괄호 ()를 사용하는 이유는 JavaScript에서 화살표 함수(arrow function)의 특별한 동작 때문이다.
화살표 함수는 단일 표현식을 반환하는 함수를 간단하게 작성하기 위한 문법이다.

중괄호 {}를 사용하지 않고 화살표 함수를 정의할 때, 함수는 표현식의 값을 반환한다.
중괄호를 사용하면 명시적인 return 문이 필요하기 때문에 중괄호 {}를 사용하지 않고 객체 리터럴을 반환하려면,
소괄호 ()로 객체 리터럴을 감싸야 한다.

이렇게 하면 JavaScript는 중괄호 {}를 블록으로 처리하는 것이 아니라 객체 리터럴로 해석한다.
```

```javascript
// 중괄호를 사용하면 return 키워드가 필요하다.
const createObjectWithBraces = param => { return { 리턴: param }; };

// 중괄호 없이 소괄호로 감싸 객체 리터럴을 반환할 수 있다.
const createObjectWithParentheses = param => ({ 리턴: param });

console.log(createObjectWithBraces('리턴O'));
console.log(createObjectWithParentheses('리턴X'));
```
