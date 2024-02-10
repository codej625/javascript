# import와 export에 대해 알아보자!

<br />

1) Export
```
Named export
특정 함수, 변수 또는 객체를 다른 파일에서 사용할 수 있도록 내보내는 방법
```
```javascript
/* ex) */
export const myFunction = () => {
  console.log('This is a named function export');
};

export const myVariable = 10;

export const myObject = {
  key: 'value'
};
```

<br />

```
Default export
하나의 파일에서 하나의 항목만 내보낼 수 있다.
다른 파일에서 import할 때 이름을 바꿀 필요가 없다.
```
```javascript
/* ex) */
const myFunction = () => {
  console.log('This is a default function export');
};

/* export { myFunction as renamedFunction }; 이름을 바꿔 내보내기 */
export default myFunction;
```

<br />
<br />

2) Import
```
Named import
이름을 사용하여 모듈에서 특정 함수, 변수 또는 객체를 가져온다.
```
```javascript
import { myFunction, myVariable, myObject } from './myModule.js';
/* import { myFunction as renamedFunction } from './myModule.js'; 이름을 바꿔 가져오기 */

myFunction(); /* 내보낸 함수 실행 */
console.log(myVariable); /* 내보낸 변수 사용 */
console.log(myObject); /* 내보낸 객체 사용 */
```
```javascript
/* 모든 것을 한 번에 가져오기 */
import * as myModule from './myModule.js';

myModule.myFunction(); /* 내보낸 함수 실행 */
console.log(myModule.myVariable); /* 내보낸 변수 사용 */
console.log(myModule.myObject); /* 내보낸 객체 사용 */
```

<br />

```
Default import
default로 내보낸 항목을 가져옵니다. 이름을 바꾸려면 as 키워드를 사용한다.
```
```javascript
/* ex) */
import myFunction from './myModule.js'; /* 이름을 바꾸지 않고 가져오기 */
import myRenamedFunction from './myModule.js'; /* 이름을 바꿔 가져오기 */
```
