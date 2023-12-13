# 나이를 계산해보자!

<br/>

```javascript
function ageCalc(birthday) { /* ex) 20201202 */
  const currentYear = new Date().getFullYear();
  const birthYear = parseInt(birthday.substring(0, 4));
  if (isNaN(birthYear)) {
    return ['', ''];
  }
  const age = currentYear - birthYear + 1;
  let brand = '';
  
  if (0 <= age && age <= 4) {
    brand = '유아';
  } else if (5 <= age && age <= 12) {
    brand = '초등';
  } else if (13 <= age && age <= 15) {
    brand = '중학';
  } else if (16 <= age && age <= 19) {
    brand = '고등';
  }
  return brand ? [brand, age.toString()] : ['', ''];
}
```
