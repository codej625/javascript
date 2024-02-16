# 체크박스 전체를 체크해보자!

<br />

```html
<input id="select-all" type="checkbox" />

<input class="check" type="checkbox" />
<input class="check" type="checkbox" />
```

```javascript
const selectAllCheckbox = document.getElementById('select-all');

selectAllCheckbox.addEventListener('change', () => {
  const checkboxes = document.querySelectorAll('.check');
  
  checkboxes.forEach((checkbox) => {
    checkbox.checked = selectAllCheckbox.checked;
  });
});
```
