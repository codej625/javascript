# 체크박스가 체크 되어있지 않으면 알려주는 스크립트를 만들어보자!

```css
.hidden { display: none; }

.fade-out { display: block; font-weight: bold; color: #ec008b; opacity: 0; animation: fadeOut 2s ease-in-out; } // 2s === 2초
@keyframes fadeOut { 0% { opacity: 1; } 100% { opacity: 0; } }
```

```html
<div class="box-1">
  <div><input type="checkbox" name="agree"></div>
  <div class="hidden">체크해주세요!</div>
</div>
<div class="box-2">
  <div><input type="checkbox" name="agree"></div>
  <div class="hidden">체크해주세요!</div>
</div>

<div>
  <button class="agree-check-all">확인</button>
</div>
```
```javascript
const agree = document.querySelectorAll('input[name="agree"]');
const checkBtn = document.querySelector('.agree-check-all');

checkBtn.addEventListener('click', () => {
  agree.forEach((chk, idx) => {
    if (!chk.checked) {
      let fade = '';

      if (idx === 0) {
        fade = `.box-1 > div`;
      } else {
        fade = `.box-2 > div`;
      }

      fade = document.querySelectorAll(fade)[1];
      fade.classList.add('fade-out');
      checkBtn.disabled = true; // 사용자가 버튼을 여러 번 연속으로 빠르게 클릭하여 중복 이벤트가 발생하는 것을 방지
      
      setTimeout(() => {
        checkBtn.disabled = false;
        fade.className = 'hidden';
      }, 2000); // 2000 밀리초 = 2초
    }
  });
});
```
