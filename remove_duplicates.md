# 중복 제거

<br/>
<br/>

* 배열과 객체의 중복 제거 방법
---

```
배열이나 객체를 다룰떄,
중복제거를 해야 할 때가 있다.

이럴 때 간단하게 하는 방법을 알아보자.
```

<br />
<br />
<br />
<br />

1. for + set 사용

```js
function removeDuplicatesByKeys(arr, keys) {
  /* 중복 제거를 위한 Set 객체 생성 */
  const uniqueSet = new Set();
  /* 중복 제거된 객체들을 담을 배열 */
  const uniqueArray = [];
  
  arr.forEach(obj => {
    /* keys 배열에 정의된 프로퍼티들을 조합한 문자열을 생성하여 중복 여부를 확인 */
    let keyString = keys.map(key => obj[key]).join('-');
    /* Set에 keyString이 없는 경우, 중복이 아니므로 해당 객체를 추가하고 uniqueSet에 keyString 추가 */
    if (!uniqueSet.has(keyString)) {
      uniqueSet.add(keyString);
      uniqueArray.push(obj);
    }
  });
  return uniqueArray;
}
```

```js
try {
  const keys = [ /* 중복 제거 옵션 */
    'ip',
    'name',
    'gender',
    'mobile',
    'birthday'
  ];
  const result = removeDuplicatesByKeys(obj, keys);
} catch {
  ...
}
```

<br />
<br />
<br />

2. 원시 타입 배열의 중복 제거 (가장 간단한 방법)

```js
const numbers = [1, 2, 2, 3, 4, 4, 5];
const uniqueNumbers = [...new Set(numbers)];
console.log(uniqueNumbers); // [1, 2, 3, 4, 5]

const strings = ["apple", "banana", "apple", "orange"];
const uniqueStrings = [...new Set(strings)];
console.log(uniqueStrings); // ["apple", "banana", "orange"]
```

<br />
<br />
<br />

2. 객체 배열의 중복 제거 (내용 기반)

```
객체는 참조 타입이므로,
내용이 같더라도 참조가 다르면 다른 객체로 인식한다.

따라서 객체 배열에서 내용 기반으로 중복을 제거하려면,
각 객체를 고유하게 식별할 수 있는 문자열 키를 생성하여 Set에 저장해야 한다.
```

```js
const objects = [
  { id: 1, name: "Alice" },
  { id: 2, name: "Bob" },
  { id: 1, name: "Alice" },
  { id: 3, name: "Charlie" },
];

const uniqueObjects = Array.from(
  new Map(objects.map((obj) => [JSON.stringify(obj), obj])).values()
);

console.log(uniqueObjects);
// [
//   { id: 1, name: "Alice" },
//   { id: 2, name: "Bob" },
//   { id: 3, name: "Charlie" }
// ]
```

<br />

```
// 다른 방법 (특정 속성 기반 중복 제거)

특정 속성을 기준으로 중복을 제거하고 싶다면 다음과 같이 할 수 있다.
```

```js
const items = [
  { id: 1, value: "A" },
  { id: 2, value: "B" },
  { id: 1, value: "C" },
  { id: 3, value: "A" },
];

const uniqueItemsById = Array.from(
  new Map(items.map((item) => [item.id, item])).values()
);
console.log(uniqueItemsById);
// [ { id: 1, value: 'C' }, { id: 2, value: 'B' }, { id: 3, value: 'A' } ]
// (id가 같은 경우 마지막 요소가 유지됨)

const uniqueItemsByValue = Array.from(
  new Map(items.map((item) => [item.value, item])).values()
);
console.log(uniqueItemsByValue);
// [ { id: 1, value: 'A' }, { id: 2, value: 'B' }, { id: 1, value: 'C' } ]
// (value가 같은 경우 마지막 요소가 유지됨)
```
