# 현재 시각 구하기

<br /><br />

```
Date 객체를 대신하는 Temporal 개체를 사용하고 싶지만,
아직 모든 브라우저에서 지원하지 않으므로(240701 기준)
Date 객체를 기준으로 설명한다.
```

<br /><br />

1. Date 객체 생성
```javascript

now = new Date();

```

<br />

2. Options 만들기
```javascript
const options = {
  timeZone: 'Asia/Seoul',  // 'Asia/Seoul', 'America/New_York' 등을 사용할 수 있습니다.
  year: 'numeric',         // 연도를 숫자로 표시
  month: 'short',          // 월을 짧은 형식으로 표시 (예: Jan, Feb, ...)
  day: 'numeric',          // 일을 숫자로 표시
  weekday: 'long',         // 요일을 긴 형식으로 표시 (예: Sunday, Monday, ...)
  hour: '2-digit',         // 시간을 2자리 숫자로 표시 (예: 01, 02, ..., 12, 13, ...)
  minute: '2-digit',       // 분을 2자리 숫자로 표시 (예: 00, 01, ..., 59)
  second: '2-digit',       // 초를 2자리 숫자로 표시 (예: 00, 01, ..., 59)
  hour12: false            // 24시간 형식으로 표시
};
```

<br />

3. 현재 시각 출력
```javascript
let currentTime = now.toLocaleString('ko-KR', options); // 로케일(언어와 국가)를 선택하고 Options을 추가
currentTime = currentTime.replace('시', ''); // '시' 제거
```
