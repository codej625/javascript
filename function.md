# 함수에 대해 알아보자!

<br/>

```
기본적으로 자바스크립트 함수 명명규칙은 camel case를 사용한다.
ex) testTest, nameName, goodGood
```

<br/>

1. 익명 함수와 일반 함수의 사용 방법
```javascript
ex) 익명 함수(화살표 함수)

const noNameFunc = () => {
  //...logic
};
```
```javascript
ex) 일반 함수

const nameFunc() {
  //...logic
};
```

<br/>

2. 파라미터가 있는 함수
```javascript
ex) 파라미터의 기본값이 없는 함수

const nameFunc(data, data2) {
  //...logic
};
```
```javascript
ex) 파라미터의 기본값이 있는 함수

const nameFunc(data, data2 = 'default') {
  //...logic
};
```
