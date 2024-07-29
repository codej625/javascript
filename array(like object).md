# 유사 배열에 Array method를 사용해보자!

<br /><br />

ex)
```javascript
/* 모든 checkbox를 가져온다. */
const checkboxes = document.querySelectorAll('.checkbox');

/* querySelectorAll() 메서드가 반환하는 것이 실제 배열이 아닌 NodeList이기 때문에 from()을 사용한다. */
const isAnyChecked = Array.from(checkboxes).some(checkbox => checkbox.checked);
```
