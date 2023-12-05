# 카운트 다운을 만들어보자!

<br/>

```javascript
/* countdown */
function startCountdown(startDate, startTime, endTime) {
  // 날짜 형식을 변환하는 함수
  function convertDateFormat(inputDate) {
    return inputDate.replace(/-/g, '/'); // YYYY/MM/DD 형식으로 변환
  }
  
  const startDateTime = new Date(convertDateFormat(`${startDate} ${startTime}`));
  const endDateTime = new Date(convertDateFormat(`${startDate} ${endTime}`));
  const now = new Date();
  const countdownElement = document.getElementById("countdown");
  
  if (now >= startDateTime && now <= endDateTime) {
    /* 각 시간 단위를 문자열로 변환하는 함수 */
    const formatTimeUnit = unit => unit < 10 ? `0${unit}` : unit.toString();
    /* 남은 시간을 화면에 표시하는 함수 */
    const updateCountdown = () => {
      const now = new Date();
      const timeLeft = endDateTime - now;
  
      if (timeLeft <= 0) {
        clearInterval(interval);
        countdownElement.innerHTML = "00 : 00 : 00 : 00";
        return;
      }
      /* 남은 시간 계산 */
      let milliseconds = parseInt((timeLeft % 1000) / 10),
      seconds = parseInt((timeLeft / 1000) % 60),
      minutes = parseInt((timeLeft / (1000 * 60)) % 60),
      hours = parseInt((timeLeft / (1000 * 60 * 60)) % 24);
  
      hours = formatTimeUnit(hours);
      minutes = formatTimeUnit(minutes);
      seconds = formatTimeUnit(seconds);
      milliseconds = formatTimeUnit(milliseconds);
      /* 남은 시간을 화면에 표시 (예: "01:02:03:04") */
      countdownElement.innerHTML = `${hours} : ${minutes} : ${seconds} : ${milliseconds}`;
    };
    /* 10밀리초마다 업데이트 */
    const interval = setInterval(updateCountdown, 10);
  } else {
    countdownElement.innerHTML = "00 : 00 : 00 : 00";
  }
}
/* countdown start */
startCountdown("2023-12-06", "3:00:00", "20:00:00"); /* start date, start hour, end hour */
```
