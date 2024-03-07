# OR 연산자에 대해 알아보자!

<br />

```
논리 OR 연산자(||)는 두 가지 주요 쓰임새가 있다.

1) 두 개의 조건 중 하나라도 참이면 true 반환
2) 기본값 설정

이렇게 크게 두 가지 경우에 사용된다.
밑에서 자세하게 알아보자!
```

<br />

```
이것이 가장 일반적인 사용 방법이다.
두 개의 조건 중 하나라도 참이면 전체 표현식은 true로 평가된다.
```

```javascript

1)
const a = true;
const b = false;
const result = a || b; /* true */

2)
const a = null;
const b = ' ';
if (a === null || b === null) {
  console.log('a는 false이지만, b는 true이기 때문에 if문이 작동된다.');
}
```

<br />

```
논리 OR 연산자는 변수에 기본값을 설정할 때 유용하다.
만약 왼쪽의 값이 falsy한 경우 (즉, 존재하지 않거나 false, 0, null, undefined, 빈 문자열 등),
오른쪽의 값을 사용한다.
```

```javascript

/* 만약 process.env.PORT가 설정되지 않았다면 기본값으로 8080을 사용 */
const port = process.env.PORT || 8080;
```
