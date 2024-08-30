# Debounce

<br /><br />

```
디바운스란 서버의 무리를 주지 않기 위해 사용되는 일종의 최적화 방법이다.

자바스크립트로 구현방법을 알아보자.
```

<br /><br /><br />

1. 예시

```javascript
function debounce(func, delay) {
  let timer;

  return function () {
    const args = arguments;
    clearTimeout(timer);

    timer = setTimeout(() => {
      func.apply(this, args);
    }, delay);
  }
}

const input = document.querySelector('#test');
input.addEventListener('input', debounce(function(e) {
  console.log(e.target.value);
}, 300));
```

<br />

```html
<label for="test">인풋의 라벨</label>
<input id="test" type="text">
```
