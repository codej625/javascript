# 나이 제한 로직

<br/><br/>

```javascript
function ageCheck(birthday, min, max) { // 19910625, 2007, 2020
  if (birthday.length === 8) { // 숫자 8자리이면 ex) 19910625
    const ageStr = birthday;
    const startDigit = ageStr.substring(0, 4); // 앞 4자리 ex) 1991

    if (!(startDigit >= min && startDigit <= max)) { // 최소, 나이를 정한다.
      alert(`${min} ~ ${max}년생으로 나이 제한`);
      return false;
    }
  }
}
```
