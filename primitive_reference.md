# 원시(primitive)값과 참조(reference)값을 알아보자!

<br />

1) 기본형 값
```
숫자 (Number)
문자열 (String)
불리언 (Boolean)
null
undefined
심볼 (Symbol, ES6에서 추가)
기본형 값은 변수에 직접 값을 저장하므로 해당 변수가 독립적으로 값을 가지게 됩니다.
```

2) 참조형 값
```
객체 (Object)
배열 (Array)
함수 (Function)
```

<br />

```
참조형 값은 변수에 값 대신에 메모리 주소(참조)가 저장되며, 여러 변수가 동일한 객체를 참조할 수 있다.
이로 인해 한 변수에서 객체를 수정하면 다른 변수에서도 영향을 받을 수 있다.
```

ex)
```javascript
// 기본형 값
let a = 10;
let b = a;
b = 20;
console.log(a); // 10 (a에는 영향을 주지 않음)

// 참조형 값
let arr1 = [1, 2, 3];
let arr2 = arr1;
arr2.push(4);
console.log(arr1); // [1, 2, 3, 4] (arr1에도 영향을 줌)
```
```
기본형 값은 값 자체를 복사하고, 참조형 값은 메모리 주소를 복사 한다.
```
