# 나이 제한 로직을 만들어 보자!

<br/>

```javascript
function ageCheck(age) {
  if (age.value.length === 8) { /* 숫자 8자리이면 ex) 19910625 */
    const ageStr = age.value;
    const startDigit = ageStr.substring(0, 4); /* 앞 4자리 ex) 1991 */
		
    if (!(startDigit >= 2007 && startDigit <= 2020)) { /* 최소,  나이를 정한다. */
      alert('2020~2007년생으로 나이 제한');
      return false;
    }
  }
}
```
