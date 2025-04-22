# 자바스크립트의 split method

<br />
<br />

* split?
---

```
자바스크립트에는 여러가지 메서드가 있다.

split() 메서드는 JavaScript의 String 객체가 제공하는 유용한 메서드 중 하나로,
원본 문자열을 지정된 구분자(separator)를 기준으로 여러 개의 부분 문자열로 분리하여 배열로 반환한다.
```

<br />
<br />
<br />
<br />

1. 정의

```
// String.prototype.split(separator, limit)

separator (필수): 문자열을 분리할 기준이 되는 문자열 또는 정규 표현식이다.
                 이 구분자는 결과 배열에 포함되지 않는다.
                 만약 separator를 생략하거나 undefined로 전달하면,
                 split 메서드는 원본 문자열 전체를 포함하는 하나의 요소를 가진 배열을 반환한다.

limit (선택): 분리를 제한하는 숫자로,
             최대 몇 개의 요소로 이루어진 배열을 반환할지를 지정한다.
             분리된 요소의 개수가 limit에 도달하면 더 이상 분리를 멈춘다.
             만약 원본 문자열이 limit으로 지정된 개수보다 적은 수의 부분 문자열로 분리된다면,
             실제 분리된 모든 부분 문자열이 배열에 포함된다.

split() 메서드는 원본 문자열을 변경하지 않고,
항상 새로운 배열을 반환한다.
```

<br />
<br />
<br />

2. 사용

```js
// 특정 문자로 분리하기

const str = "apple,banana,orange";
const fruits = str.split(','); // 쉼표(,)를 기준으로 분리

console.log(fruits); // 출력: ["apple", "banana", "orange"]
```

<br />

```js
//공백 문자로 분리하기

const sentence = "Hello world this is a test";
const words = sentence.split(' '); // 공백을 기준으로 분리

console.log(words); // 출력: ["Hello", "world", "this", "is", "a", "test"]
```

<br />

```js
// 빈 문자열("")로 분리하기 (각 문자를 분리)

const greeting = "안녕하세요";
const characters = greeting.split(''); // 빈 문자열을 기준으로 분리

console.log(characters); // 출력: ["안", "녕", "하", "세", "요"]
```

<br />

```js
// 구분자 없이 사용하기 (원본 문자열 전체를 배열에 담음)

const text = "Single string";
const arr = text.split(); // 구분자 생략

console.log(arr); // 출력: ["Single string"]
```

<br />

```js
// limit 매개변수 사용하기

const data = "A-B-C-D-E";
const limitedData = data.split('-', 3); // 하이픈(-)을 기준으로 분리하되, 최대 3개의 요소만 반환

console.log(limitedData); // 출력: ["A", "B", "C"]
```

<br />
<br />
<br />

2. 주의 사항

```js
const convertedMitreAttackTechniques = mitreAttackTechniques.data.map((t: any) => {
  return {
    ...t,
    tactics: t.tactics.split(",").map((t: string) => t.trim()), // 여기서 split 사용
    platforms: t.platforms.split(",").map((p: string) => p.trim()), // 여기서 split 사용
    isSubTechnique: t.isSubTechnique === "FALSE" ? false : true,
    subTechniqueOf: t.subTechniqueOf ? t.subTechniqueOf : "",
  };
});
```

```
예를 들어 위와 같은 코드가 있다고 가정하고,
어떤 문제가 생길지 알아보자.

오류가 발생할 수 있는 경우는 다음과 같습니다.

1) t.tactics 또는 t.platforms가 null 또는 undefined인 경우,
   null 또는 undefined에는 split 메서드가 존재하지 않으므로 TypeError가 발생한다.

2) t.tactics 또는 t.platforms가 문자열이 아닌 다른 타입 (예: 숫자, 객체, 배열)인 경우,
   마찬가지로 해당 타입에는 split 메서드가 없거나 예상치 못한 동작을 할 수 있다.
```

<br />

```js
const convertedMitreAttackTechniques = mitreAttackTechniques.data.map((t: MitreAttackTechniqueResponse) => {
  return {
    ...t,
    tactics: t.tactics ? t.tactics.split(",").map((t: string) => t.trim()) : [],
    platforms: t.platforms ? t.platforms.split(",").map((p: string) => p.trim()) : [],

    ...

  };
});
```

```
위와 같이 데이터 변환 전에 입력값을 검증한다면,
데이터가 falsy값일때 에러를 방지할 수 있다.
```
