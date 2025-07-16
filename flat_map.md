# flatMap

<br />
<br />

* flatMap 사용 이유
---

```
flatMap 메서드는 배열의 각 요소에 대해 주어진 콜백 함수를 적용한 후,
결과를 단일 배열로 평탄화(flatten)하여 반환한다.

이는 map과 flat 메서드를 결합한 동작으로,
중첩 배열을 한 단계 평탄화하면서 매핑을 수행할 때 유용하다.
```

<br />
<br />
<br />
<br />

1. 기본 사용 - 배열을 매핑하고 평탄화

```js
const numbers = [1, 2, 3, 4];

// 각 요소를 두 배로 만들고, 배열로 감싸서 반환
const result = numbers.flatMap(num => [num, num * 2]);
console.log(result); // 출력: [1, 2, 2, 4, 3, 6, 4, 8]

// map만 사용했을 경우 (비교)
const mapped = numbers.map(num => [num, num * 2]);
console.log(mapped); // 출력: [[1, 2], [2, 4], [3, 6], [4, 8]]
```

<br />
<br />
<br />

2. 문자열 분리 및 평탄화

```js
const sentences = ['안녕하세요', '자바스크립트 재밌어요'];

// 각 문장을 단어로 분리
const words = sentences.flatMap(sentence => sentence.split(' '));
console.log(words); // 출력: ['안녕하세요', '자바스크립트', '재밌어요']
```

<br />
<br />
<br />

3. 객체 배열 처리

```js
const users = [
  { name: '철수', hobbies: ['축구', '게임'] },
  { name: '영희', hobbies: ['독서', '요리'] }
];

// 모든 취미를 단일 배열로 추출
const hobbies = users.flatMap(user => user.hobbies);
console.log(hobbies); // 출력: ['축구', '게임', '독서', '요리']
```

<br />
<br />
<br />

4. 빈 배열이나 단일 값 반환

```js
const data = [1, 2, 3, 4];

// 홀수일 때는 빈 배열, 짝수일 때는 값 반환
const filtered = data.flatMap(num => (num % 2 === 0 ? [num] : []));
console.log(filtered); // 출력: [2, 4]
```

<br />
<br />
<br />

5. 깊은 중첩 배열의 한계

```js
const nested = [1, [2, [3, 4]], 5];

// 한 단계만 평탄화
const result = nested.flatMap(x => x);
console.log(result); // 출력: [1, 2, [3, 4], 5]

// 깊은 평탄화가 필요하면 flat()을 추가로 사용
console.log(nested.flatMap(x => x).flat()); // 출력: [1, 2, 3, 4, 5]
```
