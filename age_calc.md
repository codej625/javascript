# 나이를 계산해보자!

<br/>

```javascript
function ageCalc(birthday) { /* ex) 20201202 */
  const currentYear = new Date().getFullYear();
  const birthYear = parseInt(birthday.substring(0, 4)); /* int type으로 캐스팅 */

  if (isNaN(birthYear)) { /* isNaN -> is not a number */
    return ['', ''];
  }
  const age = currentYear - birthYear + 1; /* 한국 기준으로 현재 나이 계산 */
  let brand = '';
  
  if (0 <= age && age <= 4) {
    brand = '유아';
  } else if (7 <= age && age <= 12) { /* 7살부터 예비 초등학생 */
    brand = '초등';
  } else if (13 <= age && age <= 15) { /* 13살은 예비 중학생 */
    brand = '중학';
  } else if (16 <= age && age <= 19) { /* 16살은 예비 중학생 */
    brand = '고등';
  }
  return brand ? [brand, age.toString()] : ['', '']; /* 배열값으로 리턴 */
}
```
