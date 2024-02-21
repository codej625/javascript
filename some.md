# some() 메서드에 대해 알아보자!

<br />

```
배열의 모든 요소 중에서 주어진 조건을 만족하는 요소가 하나라도 있으면 true를 반환하고, 그렇지 않으면 false를 반환한다.
```
```javascript
const array = [1, 2, 3, 4, 5];
const hasEvenNumber = array.some(num => num % 2 === 0);
```
```
위 코드에서 num % 2 === 0 조건을 만족하는 요소(짝수)가 배열에 하나 이상 있으므로,
hasEvenNumber 변수에는 true가 할당된다.
```
