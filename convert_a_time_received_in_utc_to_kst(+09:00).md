# UTC로 받은 시간을 KST(+09:00)으로 바꿔보자

<br/>

```javascript
function timestamp(current) { /* 677721600000 */
  const timestamp = current;
  const date = new Date(timestamp);
  const timeString = date.toLocaleString("ko-KR", {timeZone: "Asia/Seoul"});
  const result = timeString.substring(0, 14);
  const timeSplit = result.split('. ');

  return `${timeSplit[0]}-${timeSplit[1]}-${timeSplit[2]}`;
}
```
