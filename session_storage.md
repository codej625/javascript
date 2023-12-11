# 세션 스토리지를 활용해보자!

<br/>

### 세션 스토리지는 창이 닫히면 리셋 되므로 이점을 잘 활용하면 굉장히 유용한 기능이다.

1. ex) 홈페이지 페이지 로드후 한번만 새로고침이 필요한 경우
```javascript
if (sessionStorage.getItem("reloaded") !== "true") {
  /* "reloaded"가 설정되지 않았다면 새로 고침 수행 */
  sessionStorage.setItem("reloaded", "true");
  window.location.reload();
}
```
