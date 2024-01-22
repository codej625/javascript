# 구구단을 만들어보자!
(회사일이 아무리 바빠도 기록하는 습관을 포기하지 말자ㅠㅠ)

<br />

1. HTML
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Multiplication tables</title>
</head>

<body>
  <div>
    <p>구구단</p>
    <div id="구구단">

    </div>
  </div>
</body>

</html>
```

2. Javascript
```javascript
const 구구단 = document.querySelector('#구구단');
for (let i = 2; i <= 9; i++) {
  구구단.innerHTML += `========== ${i}단 ==========<br />`;
  for (let j = 1; j <= 9; j++) {
    구구단.innerHTML += `${i} * ${j} = ${i * j}<br />`;
  }
  if (i === 9) {
    구구단.innerHTML += `=========================`;
  }
}
```
