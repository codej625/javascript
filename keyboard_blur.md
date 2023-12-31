# 모바일 환경에서 키보드를 숨김 처리 해보자!

<br/>

```javascript
function birthdayCheck(input) {
  if (input.value.length > input.maxLength) {
    input.value = input.value.slice(0, input.maxLength); /* ex) 최대 길이 제한 */
  }
  if (input.value.length === 8) { /* ex) 숫자가 8자리이면 */
    input.blur(); /* 키보드 숨김 */
  }
}
```
