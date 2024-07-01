# 자바스크립트에서 Falsy를 알아보자.

<br /><br />

* Falsy
```
자바스크립트에서 Falsy 값은 false, 0, "", null, undefined, NaN과 같은 값들을 말한다.
변수가 비어 있거나 정의되지 않았거나,
혹은 falsy한 값을 가질 때 해당 조건이 참이 되어 실행될 수 있다.
```

<br /><br /><br />

* 예시
```javascript
function disableHour(startHour, endHour) {
  // ! <- 논리 부정 연산자
  if (!startHour || !endHour) {
    // ... 로직 구현

    // return; boolean 값을 반환하지 않고 바로 함수를 종료.
    return false; // boolean 값을 반환하고 함수를 종료.
  }
}
```
```
startHour 혹은 endHour의 값이 논리 부정 연산자를 만나
falsy한 값을 가질 때 해당 조건이 참이 되어 실행될 수 있다.
```
