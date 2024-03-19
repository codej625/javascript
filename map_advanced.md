# map에 대해 알아보자

<br />

```
Map (맵)은 자바스크립트에서는 키-값(key-value) 쌍을 저장하는 데 사용되는 자료구조이다.
```

<br />

```javascript
/* ex) */

/* 맵 생성 */
const myMap = new Map();

/* 값 추가 */
myMap.set('key1', 'value1');
myMap.set('key2', 'value2');

/* 값 조회 */
console.log(myMap.get('key1')); // 출력: 'value1'

/* 맵 순회 */
myMap.forEach((value, key) => {
  console.log(`${key}: ${value}`);
});

/* 맵의 모든 요소 삭제 */
myMap.clear();

/* 맵의 크기 반환 */
myMap.size;
```

<br />

```
*알아두면 도움이 되는 메서드
Object.fromEntries는 주어진 키-값 배열을 사용하여 새로운 객체를 만드는 정적 메서드이다.

보통 객체를 만들 때는 중괄호({})를 사용하고, 키-값 쌍을 지정한다.
하지만 때로는 배열 형태로 키-값 쌍을 가지고 있는 경우가 있다.
이러한 배열을 객체로 변환해주는 역할을 한다.
```
```javascript
/* ex) */
const map = new Map([
  ['a', 1],
  ['b', 2],
  ['c', 3]
]);

const obj = Object.fromEntries(map);
console.log(obj); /* 결과 {a: 1, b: 2, c: 3} */
```
