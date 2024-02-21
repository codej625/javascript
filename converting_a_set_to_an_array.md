# set을 배열로 변환해보자!

<br />

```javascript
const mySet = new Set([1, 2, 3, 4, 5]);

/* Set 객체를 배열로 변환 */
const myArray = Array.from(mySet);

/* 배열 메소드를 사용하여 작업 */
myArray.forEach(item => console.log(item));
const squaredArray = myArray.map(item => item * item);
const evenNumbers = myArray.filter(item => item % 2 === 0);
const sum = myArray.reduce((acc, curr) => acc + curr, 0);

console.log(squaredArray); /* [1, 4, 9, 16, 25] */
console.log(evenNumbers); /* [2, 4] */
console.log(sum); /* 15 */
```
