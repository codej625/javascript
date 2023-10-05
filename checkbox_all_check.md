# 체크박스를 올 체크/해제 해보자


```html
<input class="all" name="all-agree" type="checkbox">

<input class="btn-1" name="agree" type="checkbox">
<input class="btn-2" name="agree" type="checkbox">
```
```javascript
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
