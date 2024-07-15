# 자바스크립트에서 중복제거를 해보자.

<br /><br />

1. trim()
```

문자열 앞뒤의 모든 공백(스페이스, 탭, 줄바꿈 등)을 제거한다.

```

<br />

```javascript
const str = "   Hello, World!   ";
const trimmedStr = str.trim();
console.log(trimmedStr); // "Hello, World!"
```

<br /><br /><br />

2. RegExp
```
정규 표현식을 사용하는 방법도 있다.
예를 들어, 앞뒤 공백만 제거하려면 아래와 같이 할 수 있다.
```

<br />

```javascript
const str = "   Hello, World!   ";
const trimmedStr = str.replace(/^\s+|\s+$/g, '');
console.log(trimmedStr); // "Hello, World!"
```

<br /><br />

```
정규식으로  문자열 안에 공백도 제거하고 싶다면,
밑에 방법을 사용하면 된다.
```

<br />

```javascript
const str = "   Hello, World!   ";
const trimmedStr = str.replace(/\s/g, '');
console.log(trimmedStr); // "Hello,World!"
```
