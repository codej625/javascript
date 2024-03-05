# 텍스트가 바뀌며 돌아가는(위 아래로) 기능을 만들어보자!

<br />

1. CSS
```css
.slider-body-top {
  border: 4px solid;
  border-image: linear-gradient(to right, #f0c364, #e8a34e);
  border-image-slice: 1;
}
```

2. HTML
```html
<div class="wrap">
  <div class="slider-body-top">
    <div class="standby-1"></div>
  </div>
  <div class="standby-2"></div>
  <div class="standby-3"></div>
</div>
```

3. Javascript
```javascript
let index = 0;
const textElement1 = document.querySelector('.standby-1');
const textElement2 = document.querySelector('.standby-2');
const textElement3 = document.querySelector('.standby-3');
const phrases = [
  '1번 문구', 
  '2번 문구', 
  '3번 문구'
];

function changeText() {
  textElement1.innerHTML = phrases[index];
  textElement2.innerHTML = phrases[(index + 1) % phrases.length];
  textElement3.innerHTML = phrases[(index + 2) % phrases.length];
  
  index = (index + 1) % phrases.length;
}
changeText(); /* default set */
setInterval(changeText, 2000);
```
