# 메소드 축약표현에 대해 알아보자

<br />

```
Javascript의 메서드 선언방식은 ES5와 ES6가 다르다.
현재 ECMAScript 사양에서는 ES5의 방식은 메소드로 인정하지 않으며, 오로지 ES6 방식만을 메소드로 인정한다.
```

<br /><br />

1. ES5 메소드 표현
```javascript
// ES5
var obj = {
  name: 'codej625',
  /* 프로퍼티 sayHello의 값으로 할당된 것은 일반 함수(constructor)로 정의된 함수이다. */
  /* 현재 ECMAScript 사양에서 메서드로 인정되지 않는다. */
  sayHello: function() {
    console.log('Hello! ' + this.name);
  }
};

obj.sayHello(); /* 일반함수 호출 -> Hello! codej625 */

/* ES5의 메서드 선언 방식은 현재 ECMAScript 사양에서는 일반 함수로 정의된다. */
/* 일반 함수는 constructor이므로 new로 인스턴스를 생성할 수 있다. */
new obj.sayHello(); /* 인스턴스 생성 -> sayHello {} */
```

<br />

2. ES6 메소드 축약 표현
```
S6에서는 메소드를 선언할 때,
function 키워드를 생략한 축약 표현을 사용할 수 있다.
현재 ECMAScript에서는 ES6 메서드 축약표현만 메서드로 인정한다.
```
```javascript
/* ES6 메서드 축약표현만 메서드로 인정된다. */
const obj = {
  name: 'codej625',
  /* 메소드 축약 표현 */
  sayHello() {
    console.log('Hello! ' + this.name);
  }
};

obj.sayHello(); /* 일반함수 호출 -> Hello! codej625 */

/* 메소드는 non-constructor이므로 생성자 함수로 호출할 수 없다. */
new obj.sayHello(); /* 인스턴스 생성 -> Uncaught TypeError */
```
