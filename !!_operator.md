# 논리 NOT 연산자 활용

<br />
<br />

* 예시

---

```
자바스크립트에서는 0 이상의 Number 타입을 true 즉,
Boolean 값으로 평가한다.

하지만 === 엄격 비교를 사용 시 타입이 달라 비교할 수 없으므로,
논리 !(NOT) 연산자를 사용해서 쉽게 변환해보자.
```

<br />
<br />
<br />
<br />


1. 예시

```javascript
const val = 1; // val -> Number 타입
const booleanValue = !!val; // booleanValue -> Boolean 타입
```

<br />

```
위 코드에서 !!val은 두 번의 논리 NOT 연산자를 사용하여 Number 타입을 Boolean 타입으로 변환하는데,
!!는 두 번의 논리 NOT 연산자를 사용한 것이다.

첫 번째 !는 값을 Boolean으로 변환하고,
두 번째 !는 그 결과를 다시 Boolean으로 변환하여 원래의 Boolean 값으로 만든다.
```
