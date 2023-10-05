# data-속성을 사용하여 url path에 따른 nav bar에 색을 바꿔보자!

```css
.add-color { color: aqua; }
```
```html
<div class="gnb-list">
  <ul>
    <li><a class="gnb-button" data-nav="cancer">암보험</a></li>
    <li><a class="gnb-button" data-nav="health">종합건강보험</a></li>
    <li><a class="gnb-button" data-nav="simple">간편보험</a></li>
    <li><a class="gnb-button" data-nav="actual">실비보험</a></li>
    <li><a class="gnb-button" data-nav="driver">운전자보험</a></li>
    <li><a class="gnb-button" data-nav="check">보험리모델링</a></li>
  </ul>
</div>
```
```javascript
(() => {
  const currentPath = window.location.pathname.split('/')[1];
  const gnbButton = document.querySelectorAll('.gnb-button');

  gnbButton.forEach(value => {
    if (value.getAttribute('data-nav') === currentPath) {
      value.classList.add("add-color");
    }
  });
})();
```
