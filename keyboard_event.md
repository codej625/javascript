# 키보드 이벤트를 알아보자.

<br /><br />

* 키보드 이벤트란?
---

```
자바스크립트에서 키보드 이벤트는 사용자가 키보드를 사용할 때 발생하는 이벤트이다.
웹 페이지나 웹 애플리케이션에서 사용자 입력을 감지하고 이에 반응하기 위해 사용된다.
```

<br /><br /><br />

* 이벤트 종류
---

1. keydown
```
사용자가 키보드의 키를 누를 때 발생.
이벤트는 키를 누르는 순간에 발생하며,
누르고 있는 동안 반복해서 발생.
```

2. keyup
```
사용자가 키보드의 키를 뗄 때 발생.
이벤트는 키를 누르고 뗀 순간에 발생.
```

3. keypress
```
사용자가 키를 누르고 뗄 때 발생한다.
이벤트는 키를 누르고 있는 동안에만 발생하며,
키를 누르고 뗀 순간에는 발생하지 않는다.
주로 문자 입력에 사용.
```

<br /><br /><br />

* 사용 예시
---

```html
<!DOCTYPE html>
<head>
  <meta charset="UTF-8">
  <title>ex</title>
</head>
<body>
  <input id="num" type="hidden"/>
  <div id="output"></div>
</body>
</html>
```

<br />

```javascript
const output = document.getElementById("output");
const num = document.getElementById("num");
num.focus();

document.addEventListener('keydown', function (event) {
  const keyPressed = event.key;

  if (keyPressed === 'Enter') {
    output.textContent = '';
    num.value = '';
  } else {
    num.value += keyPressed;
  }
  output.textContent = `input -> ${num.value}`;
});
```

<br />

```
키보드를 입력하면,
input(hidden)태그의 value에 키보드 입력값을 대입.
Enter를 누르면 input태그의 value를 리셋.
```
