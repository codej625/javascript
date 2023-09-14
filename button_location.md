# 버튼을 눌러서 로케이션을 이동시켜보자!

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
/* IIFE */
(() => {
  const urlPath = document.querySelectorAll('.gnb-button');

  urlPath.forEach(path => {
    path.addEventListener('click', () => {
      const params = window.location.search;
      const pathName = path.getAttribute('data-nav');
      
      window.location.href = `${pathName}${params}`;
    });
  });
})();
```