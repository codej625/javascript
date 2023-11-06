# 자바스크립트 객체에 대해 알아보자!

<br/>

1. 객체의 기본적인 모습이다.
```javascript
const obj = {
  props1: '하나',
  props2: '둘',
  props3() { /* function 키워드 없이 함수명을 넣는다. */
    return console.log('hello');
  }
};
```
```
위처럼 자바스크립트 객체에는 key-value로 쌍을 이루는 값들과 함수도 넣을수가 있다.
```

<br/>

2. 사용 방법
```javascript
const obj = {
  props1: '하나',
  props2: '둘',
  props3() { /* function 키워드 없이 함수명을 넣는다. */
    return console.log('hello');
  },
  props4() {
    return console.log(this.props1); /* this 키워드도 사용이 가능하다. */
  }
};

console.log(obj.props1) /* 하나 */
console.log(onj.props3) /* hello */
console.log(onj.props4) /* 하나 */
```

<br/>

3. class에 대해 간략하게 알아보자
```javascript
class Obj { // class 명명규칙은 대문자로 시작한다.
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  talk() {
    return console.log('hello');
  }
}
const obj = new Obj('codej625', 33); /* object instance를 하며, constructor의 값을 넣고 초기화 */

console.log(obj.name) /* codej625 */
obj.talk(); /* codej625 */
```
