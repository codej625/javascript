# Date 포맷 변경 및 차이 계산

<br /><br />

1. javascript 버전

```javascript
var time = {
  // date(날짜)를 받아 요일 반환
  getKorOne: function (date) {
    // date -> 입력 예시 '2024-07-01'
    var days = ["일", "월", "화", "수", "목", "금", "토"];
    var day = new Date(date);
    if (isNaN(day.getTime())) throw new Error("Invalid date format.");
    return days[day.getDay()];
  },
  // 두 날짜의 차이 계산
  calculateTimeDifference: function (start, end) {
    // start, end -> 입력 예시 '2024-07-01 10:10'
    // 날짜 객체로 변환
    var startDate = new Date(start);
    var endDate = new Date(end);
    if (isNaN(startDate.getTime()) || isNaN(endDate.getTime())) {
      throw new Error("Invalid date format.");
    }
    // 두 날짜 사이의 차이 계산 (밀리초 단위)
    var difference = endDate.getTime() - startDate.getTime();
    // 차이를 시간과 분으로 변환
    var hours = Math.floor(difference / (1000 * 60 * 60)); // 시간 계산
    var minutes = Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60)); // 분 계산
    return { hours: hours, minutes: minutes };
  },
  // yyyyMMdd -> 포맷 변환 
  dateFormat: function (date, option) {
    var today = date;
    return today.replace(/(\d{4})(\d{2})(\d{2})/g, "$1".concat(option, "$2").concat(option, "$3"));
  },
  // HHmm -> 포맷 변환
  hourFormat: function (time, option) {
    var hour = time;
    return hour.replace(/(\d{2})(\d{2})/g, "$1".concat(option, "$2"));
  },
};
// 사용 예시
console.log(time.getKorOne('2024-07-01')); // 월
console.log(time.calculateTimeDifference('2024-07-01 10:10', '2024-07-01 12:30')); // { hours: 2, minutes: 20 }
console.log(time.dateFormat('20240701', '-')); // 2024-07-01
console.log(time.hourFormat('1030', ':')); // 10:30
```

<br /><br /><br />

2. typescript 버전

```typescript
const time = {
  // date(날짜)를 받아 요일 반환
  getKorOne: (date: string): string => {
    // date -> 입력 예시 '2024-07-01'
    const days: string[] = ["일", "월", "화", "수", "목", "금", "토"];
    const day = new Date(date);
    
    if (isNaN(day.getTime())) throw new Error("Invalid date format.");

    return days[day.getDay()];
  },

  // 두 날짜의 차이 계산
  calculateTimeDifference: (start: any, end: any): object => {
    // start, end -> 입력 예시 '2024-07-01 10:10'
    // 날짜 객체로 변환
    const startDate = new Date(start);
    const endDate = new Date(end);

    if (isNaN(startDate.getTime()) || isNaN(endDate.getTime())) {
      throw new Error("Invalid date format.");
    }

    // 두 날짜 사이의 차이 계산 (밀리초 단위)
    const difference = endDate.getTime() - startDate.getTime();

    // 차이를 시간과 분으로 변환
    const hours = Math.floor(difference / (1000 * 60 * 60)); // 시간 계산
    const minutes = Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60)); // 분 계산

    return { hours, minutes };
  },

  // yyyyMMdd -> 포맷 변환 
  dateFormat: (date: string, option: string): string => { // 입력 예시 option 값 :, . 등
    const today = date;
    return today.replace(/(\d{4})(\d{2})(\d{2})/g, `$1${option}$2${option}$3`);
  },

  // HHmm -> 포맷 변환
  hourFormat: (time: string, option: string): string => { // 입력 예시 option 값 :, . 등
    const hour = time;
    return hour.replace(/(\d{2})(\d{2})/g, `$1${option}$2`);
  },
};

// 사용 예시
console.log(time.getKorOne('2024-07-01')); // 월
console.log(time.calculateTimeDifference('2024-07-01 10:10', '2024-07-01 12:30')); // { hours: 2, minutes: 20 }
console.log(time.dateFormat('20240701', '-')); // 2024-07-01
console.log(time.hourFormat('1030', ':')); // 10:30
```
