# 정말 시간이 없을때 급하게 비밀번호 인증이 필요하다면..!

<br/>

```javascript
/*
  Marketing Division(마케팅본부) -> m,
  Production Studio(제작실) p,
  Development Division(연구전담부서) -> d,
  Strategic Management Division(경영전략본부) -> s,
  New Business Division(신사업본부) -> n,
  International Business Division(해외사업부) -> i,
  Affiliate Business Division(제휴사업본부) -> a
*/

/* Global Variable */
let passwd = '';
const passwordArray = [ /* password list */
  'm-1', 'm-2', 'm-3',
  'm-4', 'm-5', 'p-6',
  'd-7', 's-8', 'n-9',
  'i-10', 'a-11'
];
const isLogined = getCookie("login");

if (isLogined === "") {
  passwd = prompt('전달받으신 비밀번호를 입력하세요', '');

  if (!passwordArray.includes(passwd)) {
    alert("비밀번호를 확인해주세요.");
    location.reload();
    document.getElementById('wrap').style.display = 'none';
  } else {
    setCookie('login', passwd.split('-')[1], 30);
  }
}

/* Function */
function setCookie(cname, cvalue, exdays) {
  const d = new Date();
  d.setTime(d.getTime() + (exdays * 24 * 60 * 60 * 1000));
  const expires = "expires=" + d.toUTCString();
  document.cookie = cname + "=" + cvalue + ";" + expires + ";path=/";
}

function getCookie(cname) {
  const name = cname + "=";
  const decodedCookie = decodeURIComponent(document.cookie);
  const ca = decodedCookie.split(';');
  for (let i = 0; i < ca.length; i++) {
    let c = ca[i];
    while (c.charAt(0) === ' ') {
      c = c.substring(1);
    }
    if (c.indexOf(name) === 0) {
      return c.substring(name.length, c.length);
    }
  }
  return "";
}
```
