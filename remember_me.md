# 로그인 정보 저장 기능 구현

<br /><br />

```
로그인 시 로그인의 정보를 저장하는 핵심 기능만
빠르게 구현해보자.
```

<br /><br /><br />

1. HTML

```html
<form id="login" action="/login" method="post">
  <div class="input-group">
    <label class="form-label" for="username"></label>
    <input id="username" class="form-control" name="username" type="text" placeholder="아이디" required>
  </div>
  <div class="input-group">
    <label class="form-label" for="password"></label>
    <input id="password" class="form-control" name="password" type="password" placeholder="패스워드" required>
  </div>
  <div class="input-group">
    <label class="form-label" for="remember-me">로그인 정보 저장</label>
    <input id="remember-me" class="remember-me" type="checkbox">
  </div>
  <div class="text-center">
    <button class="login-btn" type="submit">로그인</button>
  </div>
</form>
```

<br /><br /><br />

2. Javascript

```javascript
  (() => { // 즉시 실행 함수
    let result = true;
    const loginData = localStorage.getItem('login');
    const loginCheckbox = document.querySelector('#remember-me');
    const usernameInput = document.querySelector('#username');
    const passwordInput = document.querySelector('#password');

    // 1) 로그인 저장 데이터가 있는지 확인
    if (loginData && loginData !== 'false') {
      const loginObj = JSON.parse(loginData);
      // 1-1) 저장 데이터가 있으면 로그인 폼에 값을 대입
      usernameInput.value = loginObj.username;
      passwordInput.value = loginObj.password;
    }
    else { result = false; }

    // 2) 로그인 정보 저장 버튼 상태 변경
    return loginCheckbox.checked = result;
  })();

  // 로그인 폼에서 submit 이벤트 작동 시
  document.querySelector('#login').addEventListener('submit', function(e) {
    e.preventDefault(); // 1) Form submit 중지

    const username = document.querySelector('#username').value;
    const password = document.querySelector('#password').value;
    const loginCheckbox = document.querySelector('#remember-me').checked;

    // 2) 로그인 값이 비어 있을 시(유효성)
    if (!username || !password) return false;

    // 3) 로그인 정보 저장 버튼 상태 확인
    if (loginCheckbox)
      localStorage.setItem('login', JSON.stringify({ username, password }));
    else
      localStorage.setItem('login', 'false');

    // 4) Form submit
    this.submit();
  });
```
