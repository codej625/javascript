#date 객체에 대해 알아보자!

<br/>

// 현재 날짜
var nowDate = new Date();
console.log(nowDate);
// Mon Aug 16 2021 18:28:43 GMT+0900 (한국 표준시)

// getFullYear : 년도 
console.log(nowDate.getFullYear());
// 2021

// getMonth : 월
console.log(nowDate.getMonth());
// 7

// getDate : 일
console.log(nowDate.getDate());
// 16

// getDay : 요일
console.log(nowDate.getDay());
// 1

// getHours : 시간
console.log(nowDate.getHours());
// 18

// getMinutes : 분
console.log(nowDate.getMinutes());
// 28

// getSeconds : 초
console.log(nowDate.getSeconds());
// 43

// getMilliseconds : 밀리초
console.log(nowDate.getMilliseconds());
// 648
