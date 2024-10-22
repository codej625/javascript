# Object.groupBy

<br /><br />

* Object.groupBy
---

```
Object.groupBy는 ECMAScript 2022(ES13)에서 제안된 기능 중 하나로
배열의 객체를 특정 속성 값에 따라 그룹화하는 메서드이다.
```

<br /><br /><br />

1. 예시

```javascript
const data = [
  { category: 'fruit', name: 'apple' },
  { category: 'fruit', name: 'banana' },
  { category: 'vegetable', name: 'carrot' },
  { category: 'vegetable', name: 'celery' },
];

// 리턴 값을 정해주면 조건에 따라 분류된다.
const grouped = Object.groupBy(data, ({ category }) => category === 'fruit' ? '과일' : '야채');

console.log(grouped); /** 
                       * {
                       *  과일: [
                       *    { category: 'fruit', name: 'apple' },
                       *    { category: 'fruit', name: 'banana' }
                       *  ],
                       *  야채: [
                       *    { category: 'vegetable', name: 'carrot' },
                       *    { category: 'vegetable', name: 'celery' }
                       *  ]
                       * }
                       */
```

<br /><br />

2. 예시2

```javascript
const data = [
  { category: 'fruit', name: 'apple' },
  { category: 'fruit', name: 'banana' },
  { category: 'vegetable', name: 'carrot' },
  { category: 'vegetable', name: 'celery' },
];

// 객체의 특정 키의 값을 기준으로 분류한다.
const grouped = Object.groupBy(data, item => item.category);

console.log(grouped); /**
                       * {
                       *  fruit: [
                       *    { category: 'fruit', name: 'apple' },
                       *    { category: 'fruit', name: 'banana' }
                       *  ],
                       *  vegetable: [
                       *    { category: 'vegetable', name: 'carrot' },
                       *    { category: 'vegetable', name: 'celery' }
                       *  ]
                       * }
                       */
```
