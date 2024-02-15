# 디바이스를(해상도 기준으로) 체크해보자!

<br/>

```javascript
const isMobile = window.matchMedia("only screen and (max-width: 760px)").matches;

if (isMobile) {
  console.log('Mobile');
} else {
  console.log('PC');
}
```
