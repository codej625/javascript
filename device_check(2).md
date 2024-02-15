# 디바이스 체크를 해보자!

<br />

```javascript
const isMobile = /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent);

if (isMobile) {
  console.log('Mobile');
} else {
  console.log('PC');
}
```
