# 세션 스토리지(활용)

<br /><br />

* 한 번만 작동하는 메시지 만들기
---

```
가끔 한 번만 작동하는 로직이 필요할 때가 있다.
이럴 때 필요한 게 세션 스토리지이다.

세션 스토리지(session storage)는 웹 브라우저의 저장소 메커니즘 중 하나로,
세션(사용자가 브라우저를 열고 해당 세션 동안 활성화되어 있는 동안) 동안 데이터를 저장하는 데 사용된다.

이는 브라우저가 열려 있는 동안만 유효하며,
페이지 세션이 끝날 때 제거된다.
(탭/창을 닫으면 세션이 끝나고 sessionStorage 안의 객체를 초기화.)

간단한 예제와 함께 세션 스토리지 활용법을 알아보자.
```

<br /><br /><br />

1. CSS
```css
#toast {
  opacity: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  position: fixed;
  bottom: -100px;
  left: 50%;
  transform: translate(-50%,0);
  width: 1200px; padding: 48px;
  background-color: var(--color-btn-txt);
  border: 1px solid var(--color-btn);
  border-radius: 16px;
  box-shadow: 0px 4px 10px 0px rgba(0, 0, 0, 0.25);
  transition: all 0.4s;
  color: var(--color-main);
  font-size: 40px; font-weight: 700;
}

#toast.active {
  opacity: 1;
  bottom: 32px;
}
```

<br /><br />

2. HTML
```html
<div id="toast">
  <p>로그인되었습니다.</p>
</div>
```

<br /><br />

3. Javascript
```javascript
document.addEventListener("DOMContentLoaded", function () {

  const toastMessage = document.querySelector('#toast');
  const hasShownToast = sessionStorage.getItem('hasShownToast');

  if (!hasShownToast) {

    function showToast() {
      toastMessage.classList.add('active');

      setTimeout(() => {
        toastMessage.classList.remove('active');
        sessionStorage.setItem('hasShownToast', 'true');
      }, 2000);
    }
    showToast();
  }
});
```
