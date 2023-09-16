# data-속성을 사용해보자.

```css
.add-color { color: aqua; }
```
```html
<div class="gnb-list">
  <ul>
    <li><a class="gnb-button" data-nav="cancer">암보험</a></li>
    <li><a class="gnb-button" data-nav="health">종합건강보험</a></li>
    <li><a class="gnb-button" data-nav="simple">간편보험</a></li>
  </ul>
</div>
```
```javascript
/* IIFE */
(() => {
  gnbColor();
})();
/* Function */
function gnbColor() {
  const gnbNameList = document.querySelectorAll('.gnb-button');

  gnbNameList.forEach(list => {
    list.addEventListener('click', () => {
      const name = list.getAttribute('data-nav'); /* 이값을 가지고 여러가지 조건을 만들 수 있다. */

      gnbColorRemove(gnbNameList); /* color class remove */

      return list.classList.add('add-color');
    });
  });
}
/* Function */
function gnbColorRemove(data) {
  data.forEach(remove => { remove.classList.remove('add-color'); });
}
```