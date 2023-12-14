# 모바일 디바이스를 체크해보자!

<br/>

```javascript
function getDeviceType() {
  const userAgent = navigator.userAgent || navigator.vendor || window.opera;
  if (/iPad|iPhone|iPod/.test(userAgent) && !window.MSStream) {
    return 'iOS';
  }
  if (/android/i.test(userAgent)) {
    return 'Android';
  }
  return 'unknown';
}
const device = getDeviceType();

if (device === 'iOS') {
  /* ... */
} else {
  /* ... */
}
```
