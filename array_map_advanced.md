# map을 활용해보자!

ex) 두 개의 배열 값을 비교하며 조건을 체크하는 경우

```javascript
const resultDate = [
  { 'result_time': 2017 },
  { 'result_time': 2018 },
  { 'result_time': 2019 },
  { 'result_time': 2020 },
  { 'result_time': 2021 },
  { 'result_time': 2022 },
  { 'result_time': 2023 },
];
const visitDate = [
  { 'visit_date': '' },
  { 'visit_date': 2020 },
  { 'visit_date': '' },
  { 'visit_date': 2022 },
];
```
```javascript
const newResult = resultDate.map(result => {
  // find 함수가 조건을 만족 시 true를 아닐 시 undefined를 반환한다.
  const visit = visitDate.find(visit => visit.visit_date === result.result_time);
  if (visit) {
    return {
      'result_time': result.result_time,
      'visit_date': 1
    };
  } else {
    return {
      'result_time': result.result_time,
      'visit_date': 0
    };
  }
});
console.log('newResult => ', newResult);
```
