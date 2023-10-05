# filter() 함수를 사용해보자!

```
filter() 함수는 배열에서 주어진 조건을 만족하는 모든 요소를 찾아 새로운 배열로 반환하는 함수이다. 
find() 함수와는 달리 조건을 만족하는 모든 요소를 반환하기 때문에 배열의 모든 해당 요소를 찾을 수 있다.
```

<br/>

```
ex) filter() 함수를 사용하여 배열에서 특정 조건을 만족하는 요소를 찾는 예제
```
```javascript
const numbers = [1, 2, 3, 4, 5];

const evenNumbers = numbers.filter(element => element % 2 === 0);

console.log(evenNumbers); // [2, 4]
```
```
위의 예제에서 filter() 함수는 배열 numbers에서 조건 element % 2 === 0을 만족하는 모든 요소를 찾아서 evenNumbers 배열에 저장하고 있다. 
결과적으로 [2, 4] 배열이 출력되었다.
filter() 함수는 주어진 조건을 만족하는 모든 요소를 새로운 배열로 반환하므로, 
조건에 맞는 모든 요소를 필터링하고자 할 때 유용하게 사용 가능하다.
```