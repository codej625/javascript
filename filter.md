# filter()

<br />
<br />

* filter() 메서드는 언제 사용하면 좋을까?

```
filter() 함수는 배열에서 주어진 조건을 만족하는 모든 요소를 찾아 새로운 배열로 반환하는 함수이다.

find() 함수와는 달리 조건을 만족하는 모든 요소를 반환하기 때문에,
배열의 모든 해당 요소를 찾을 수 있다.
```

<br />
<br />
<br />
<br />

1. filter() 함수를 사용하여 배열에서 특정 조건을 만족하는 요소를 찾는 예제

```js
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = numbers.filter(element => element % 2 === 0);

console.log(evenNumbers); // [2, 4]
```

```
위의 예제에서 filter() 함수는
배열 numbers에서 조건 element % 2 === 0을 만족하는 모든 요소를 찾아서 evenNumbers 배열에 저장하고 있다.

결과적으로 [2, 4] 배열이 출력되었다.

filter() 함수는 주어진 조건을 만족하는 모든 요소를 새로운 배열로 반환하므로, 
조건에 맞는 모든 요소를 필터링하고자 할 때 유용하게 사용 가능하다.
```

<br />
<br />
<br />

2. 응용

```js
// 예제 데이터
const rows = [
  { id: "A001", cltnmethdcd: "1", name: "A 자산" },
  { id: "A002", cltnmethdcd: "2", name: "B 자산" },
  { id: "A003", cltnmethdcd: "3", name: "C 자산" },
  { id: "A004", cltnmethdcd: "1", name: "A 자산" }
];

const checkedRows = ["A001", "A002", "A004"]; // 사용자가 선택한 자산 ID들
```

```js
// 체이닝을 사용한 자산 검증
const hasPortableAsset = rows
  .filter((d) => checkedRows.includes(d.id)) // 1단계: 선택된 자산만 필터링
  .some((d) => d.cltnmethdcd === "2"); // 2단계: B 자산 존재 여부 확인

console.log(hasPortableAsset); // true (A002가 B 자산 자산)
```

```
rows.filter((d) => checkedRows.includes(d.id))
rows 배열에서 현재 선택된 자산들만 필터링
checkedRows 배열에 포함된 id를 가진 자산들만 추출

.some((d) => d.cltnmethdcd === "2")
필터링된 자산들 중에서 cltnmethdcd 값이 "2"인 자산이 하나라도 있는지 확인

true (B 자산이 있음) 또는 false (B 자산이 없음)
```
