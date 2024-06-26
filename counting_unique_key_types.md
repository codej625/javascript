# 객체에서 특정 키값의 종류가 몇개인지 구해보자.

<br /><br />

* 예시
```javascript
let arr = [
  { id: 1, name: 'John', age: 30 },
  { id: 2, name: 'Jane', age: 25 },
  { id: 3, name: 'Doe', gender: 'male' },
  { id: 4, name: 'Smith', age: 35 }
];
```

<br />

```javascript
// name 속성의 종류를 담을 Set 생성
const nameSet = new Set();

// 배열의 각 객체를 순회하면서 name 속성을 Set에 추가
arr.forEach(obj => {
    if (obj.hasOwnProperty('name')) {
        nameSet.add(obj.name);
    }
});

// Set의 크기(유니크한 name 속성의 개수)를 구함
const numOfUniqueNames = nameSet.size;

console.log(numOfUniqueNames); // John, Jane, Doe, Smith
```

or

```javascript
  const numOfUniqueNames = [...new Set(reservationInfo.map(obj => obj.name))];
  console.log(numOfUniqueNames); // John, Jane, Doe, Smith
```
