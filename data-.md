# data-속성을 사용해보자.

## data-속성은 어떤값도 정할수가 있다. 대신 data-로 시작해야 한다.

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
  /* Function */
  function gnbColor() {
    const gnbNameList = document.querySelectorAll('.gnb-button');
  
    gnbNameList.forEach(list => {
      list.addEventListener('click', () => {
        const name = list.getAttribute('data-nav'); /* 이값을 가지고 여러가지 조건을 만들 수 있다. */
        
        gnbNameList.forEach(button => button.classList.remove('add-color'));
        list.classList.add('add-color');
      });
    });
  }
})();
```
