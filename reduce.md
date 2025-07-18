# reduce

<br />
<br />

* 언제 쓰는 메서드일까?

---

```
reduce는 배열의 각 요소를 순회하며 단일 값을 생성하는 메서드이다.

배열을 "축소"하여 하나의 결과값을 반환한다.

주로 데이터 집계(합계, 평균, 객체 변환 등)에 사용된다.
```

<br />
<br />
<br />
<br />

1. 문법

```js
array.reduce(callback(accumulator, currentValue[, index[, array]])[, initialValue])


// 배열이 비어 있고 initialValue가 없으면 에러 발생한다.
// initialValue를 지정하지 않으면 배열의 첫 번째 요소가 초기값으로 사용되며, 두 번째 요소부터 순회한다.
```

<br />

`accumulator - 이전 호출의 결과값(누적값)`

`currentValue(callback) - 각 요소에 대해 실행되는 함수 (현재 처리 중인 배열 요소)`

`index (선택) - 현재 요소의 인덱스`

`array (선택) - 원본 배열`

`initialValue (선택) - 초기 누적값. 생략 시 배열의 첫 번째 요소가 초기값으로 사용`

<br />
<br />
<br />

2. 예시

<br />

`배열 요소의 합계 구하기`

```js
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce((acc, curr) => acc + curr, 0);

console.log(sum); // 15
```

<br />

`객체 배열에서 특정 속성의 합계`

```js
const items = [
  { name: 'Apple', price: 100 },
  { name: 'Banana', price: 200 },
  { name: 'Orange', price: 150 }
];
const totalPrice = items.reduce((acc, curr) => acc + curr.price, 0);

console.log(totalPrice); // 450
```

<br />

`배열을 객체로 변환`

```js
const fruits = ['Apple', 'Banana', 'Apple', 'Orange'];
const count = fruits.reduce((acc, curr) => {
  acc[curr] = (acc[curr] || 0) + 1;
  return acc;
}, {});

console.log(count); // { Apple: 2, Banana: 1, Orange: 1 }
```

<br />

`배열 평탄화`

```js
// reduce로 평탄화
const flatArrayReduce = nestedArray.reduce((acc, curr) => acc.concat(curr), []);

console.log(flatArrayReduce); // 출력: [1, 2, 3, 4, 5, 6]


// flatMap으로 평탄화
const flatArrayFlatMap = nestedArray.flatMap(item => item);

console.log(flatArrayFlatMap); // 출력: [1, 2, 3, 4, 5, 6]
```

<br />

`객체 값을 연산`

```js
const prices = { apple: 100, banana: 200, orange: 150 };

// 모든 값에 10% 할인
const discounted = Object.entries(prices).reduce((acc, [key, value]) => {
  acc[key] = value * 0.9;
  return acc;
}, {});

console.log(discounted); // { apple: 90, banana: 180, orange: 135 }
```
