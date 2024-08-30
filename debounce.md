# Debounce

<br /><br />

```
디바운스란 서버의 무리를 주지 않기 위해 사용되는 일종의 최적화 방법이다.

자바스크립트로 구현방법을 알아보자.
```

<br /><br /><br />

1. 예시

```javascript
// 1) 함수 선언
function debounce(func, delay) {
  let timer;

  // 3) 클로저 함수 반환 (debounce 함수가 반환한 내부 함수가 이벤트 리스너에 등록된다.)
  return function () {      /**
    const args = arguments;  * 호출 된 함수의 인자를 가져온다.
                             * 반환된 함수가 호출될 때,
                             * 이 객체는 그 호출에 전달된 인자들을 포함한다.
                             * 예를 들어, 이벤트 리스너로 등록된 함수가 input 이벤트를 처리하면
                             * arguments 객체에는 input 이벤트 객체가 포함된다.
                             */
    clearTimeout(timer);

    timer = setTimeout(() => {
      func.apply(this, args); /**
                               * input 요소의 input 이벤트 리스너로 등록된
                               * debounce 함수는 input 요소에서 호출됩니다.
                               * 따라서, input 요소의 이벤트가 발생할 때 호출된
                               * debounce 반환 함수의 this는 이벤트 리스너로 등록된 요소를 참조한다.
                               * 즉, this는 input 요소이다.
                               */
    }, delay);
  }
}

const input = document.querySelector('#test');
// input의 이벤트 리스너 등록
input.addEventListener('input', debounce(function(e) {
  console.log(e.target.value);
}, 300));
```

<br />

```html
<label for="test">인풋의 라벨</label>
<input id="test" type="text">
```
