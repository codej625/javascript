# Computed property name

<br /><br />

```
* Computed property name 란?

객체 리터럴에서 속성 이름을 동적으로 설정하는 방법이다.
예시를 보자.
```

<br /><br /><br />

* 예시
---

```javascript
const key = 'name';
const value = 'John';

const person = {
  [key]: value // 여기서 key는 'name'이 되고, value는 'John'이 된다.
};

console.log(person); // { name: 'John' }
```

<br />

```
여기서 key 변수의 값이 'name'으로 평가되기 때문에 person 객체의 속성 이름은 'name'이 된다.
이 문법은 객체의 속성 이름을 동적으로 생성할 때 유용하다.
```
