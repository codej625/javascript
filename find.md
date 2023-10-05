# find() 내장 함수를 사용해보자!

```
find() 함수는 배열에서 주어진 조건을 만족하는 첫 번째 요소를 찾는 데 사용된다. 
주로 배열에서 특정 값을 찾거나 특정 조건을 만족하는 요소를 검색할 때 사용하고,
이 함수는 조건을 검사하여 일치하는 첫 번째 요소를 반환하며, 일치하는 요소가 없으면 undefined를 반환한다.

find() 함수는 일반적으로 콜백 함수를 사용하여 배열 요소를 조사하고, 조건을 만족하는 첫 번째 요소를 찾는다. 
콜백 함수는 다음과 같은 형식을 가진다.
여기서 element는 배열의 각 요소를 나타내며, condition은 해당 요소를 평가하는 조건을 나타낸다.
```
```javascript
element => condition
```

<br/>

```
ex) 다음은 find() 함수를 사용하여 배열에서 특정 숫자를 찾는 예제이다.
```
```javascript
const numbers = [1, 2, 3, 4, 5];

const foundNumber = numbers.find(element => element === 3);

console.log(foundNumber); // 3
```
```
위의 예제에서 find() 함수는 배열 numbers에서 조건 element === 3을 만족하는 첫 번째 요소를 찾아서 foundNumber 변수에 저장하고 있다.
find() 함수는 조건을 만족하는 요소가 여러 개 있는 경우에도 첫 번째로 일치하는 요소만 반환하며, 
나머지 요소는 무시한다. 
만약 모든 일치하는 요소를 찾고 싶다면 filter() 함수를 사용하자.
```