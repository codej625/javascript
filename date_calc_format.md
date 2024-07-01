# Date 포맷 변경 및 차이 계산

<br /><br />

```javascript
const time = {
  // date(날짜)를 받아 요일 반환
  getKorOne: (date) => {
    // date -> 입력 예시 '2024-07-01'
    const days = ["일", "월", "화", "수", "목", "금", "토"];
    let day = new Date(date);

    return day = days[day.getDay()];
  },

  // 두 날짜의 차이 계산
  calculateTimeDifference: (start, end) => {
    // start, end -> 입력 예시 '2024-07-01 10:10'
    // 날짜 객체로 변환
    const startDate = new Date(start);
    const endDate = new Date(end);

    // 두 날짜 사이의 차이 계산 (밀리초 단위)
    const difference = endDate - startDate;

    // 차이를 시간과 분으로 변환
    const hours = Math.floor(difference / (1000 * 60 * 60)); // 시간 계산
    const minutes = Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60)); // 분 계산

    return { hours, minutes };
  },

  // yyyyMMdd -> 포맷 변환 
  dateFormat: (date, option) => { // 입력 예시 option 값 :, . 등
    const today = date;
    return today.replace(/(\d{4})(\d{2})(\d{2})/g, `$1${option}$2${option}$3`);
  },

  // HHmm -> 포맷 변환
  hourFormat: (time, option) => { // 입력 예시 option 값 :, . 등
    const hour = time;
    return hour.replace(/(\d{2})(\d{2})/g, `$1${option}$2`);
  },
};
```
