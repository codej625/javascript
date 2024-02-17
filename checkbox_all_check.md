# 체크박스를 올 체크/해제 해보자


```html
<!DOCTYPE html>
<html lang="kr">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>check</title>
</head>

<body>
  <div id="checkBox"></div>
</body>

</html>
```
```javascript
(() => {
  const html = document.querySelector('#checkBox');
  html.innerHTML = `
    <p>
      <label for="all-check">전부 체크<label/>
      <input id="all-check" name="all-agree" type="checkbox">
    </p>
    <label for="check-1">체크1<label/>
    <input id="check-1" name="agree" type="checkbox"><br />
    <label for="check-2">체크2<label/>
    <input id="check-2" name="agree" type="checkbox">
  `;
})();

const allAgree = document.querySelector('input[name="all-agree"]');
const agree = document.querySelectorAll('input[name="agree"]');

allAgree.addEventListener('click', () => {
  const check = allAgree.checked;

  agree.forEach(chk => {
    chk.checked = check;
  });
});
agree.forEach(check => {
  check.addEventListener('change', () => {
    let allChecked = true;

    agree.forEach(chk => {
      if (!chk.checked) {
        allChecked = false;
      }
    });
    allAgree.checked = allChecked;
  });
});
```
