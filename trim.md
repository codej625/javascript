# 중복 제거를 해보자!

<br/>

1. 문자열의 앞뒤 공백 제거하기
```javascript
let str1 = " 문자열의 앞 뒤 공백 제거하기    ";
document.write(str1.trim());
```

<br/>

2. 문자열의 앞뒤 공백 제거하기(2)
```javascript
let str1 = " 문자열의 앞 뒤 공백 제거하기    ";
document.write(str1.replace(/^\s+|\s+$/gm,''));
```

<br/>

3. 문자열의 모든 공백 제거하기
```javascript
let str1 = "  문자열의 모든 공백 제거하기    ";
document.write(str1.replace(/(\s*)/g, ""));
```

<br/>

4. 문자열의 앞 공백 제거하기
```javascript
let str1 = "  문자열의 앞 공백 제거하기    ";
document.write(str1.replace(/^\s*/, ""));
```

<br/>

5. 문자열의 뒤 공백 제거하기
```javascript
let str1 = "  문자열의 뒷 공백 제거하기    ";
document.write(str1.replace(/\s*$/, ""));
```
