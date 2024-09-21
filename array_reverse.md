# 배열의 순서를 반대로 바꾸는 방법

<br /><br />

```
간혹 배열의 순서를 반대로 바꿔야 할 때가 있다.
이럴 때 간편하게 사용할 수 있는 메서드를 알아보자.
```

<br /><br /><br />

1. reverse() 사용 예시

```
reverse() 메서드는 배열의 요소 순서를
반대로 바꾸는 데 사용된다.
```

<br />

```javascript
const arr = [1, 2, 3, 4, 5];

// 원본 배열 출력
console.log("원본 -> ", arr); // [1, 2, 3, 4, 5]

// 배열을 역순으로 변경
arr.reverse();

// 역순 배열 출력
console.log("역순 -> ", arr); // [5, 4, 3, 2, 1]
```

<br /><br />

2. 원본 배열 유지

```
reverse() 메서드는 원본의 배열을 조작하기 때문에
원본 배열을 유지하고 싶다면 slice()와 함께 사용할 수 있다.

예를 들면 slice() 메서드를 조건 없이 사용해서 얕은 복사를 하고
reverse() 메서드를 사용하는 것.
```

<br />

```javascript
const arr = [1, 2, 3, 4, 5];

// 원본 배열 출력
console.log("원본 -> ", arr); // [1, 2, 3, 4, 5]

// 복사본을 역순으로 변경
const reversedArr = arr.slice().reverse();

// 역순 배열과 원본 배열 출력
console.log("역순 -> ", reversedArr); // [5, 4, 3, 2, 1]
console.log("원본 -> ", arr); // [1, 2, 3, 4, 5]
```
