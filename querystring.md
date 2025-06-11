# 자바스크립트 쿼리스트링

<br />
<br />

* 쿼리스트링을 안전하게 만드는 URLSearchParams 객체

---

```
URLSearchParams 객체는 웹 개발에서 URL 쿼리 문자열을 쉽게 다룰 수 있도록 도와주는 최신 Web API이다.

별도의 인코딩이 필요없고 여러가지 기능을 제공하므로,
모던 웹 개발에서 URL 쿼리 문자열을 효율적으로 관리하는 데 필수적인 객체이다.
```

<br />
<br />
<br />
<br />

1. URLSearchParams 기능

<br />

`파싱 (Parsing)`

```
현재 URL의 쿼리 문자열이나 주어진 쿼리 문자열을 파싱하여,
URLSearchParams 인스턴스를 생성한다.
```

<br />

`조작 (Manipulation) - append(name, value)`

```

새 키-값 쌍을 추가한다.

```

<br />

`조작 (Manipulation) - set(name, value)`

```
기존 키의 값을 설정하거나,
키가 없으면 새로 추가한다.
```

<br />

`조작 (Manipulation) - get(name)`

```

특정 키의 첫 번째 값을 반환합니다.

```

<br />

`조작 (Manipulation) - getAll(name)`

```
특정 키의 모든 값을 배열로 반환한다.
(같은 키가 여러 번 사용될 경우)
```

<br />

`조작 (Manipulation) - delete(name)`

```

특정 키-값 쌍을 삭제한다.

```

<br />

`조작 (Manipulation) - has(name)`

```

특정 키가 존재하는지 여부를 반환한다.

```

<br />

`생성 (Generation)`

```
toString() 메서드를 사용하여,
URLSearchParams 객체를 쿼리 문자열로 변환한다.
```

<br />

`이터러블 (Iterable)`

```
for...of 루프나 forEach 메서드를 사용하여,
모든 키-값 쌍을 순회할 수 있다.
```

<br />
<br />
<br />

2. 사용 예시

<br />

`URL의 쿼리 파라미터 다루기`

```js

// 현재 URL이 "https://example.com/search?query=react&page=10&type=frontend" 라고 가정
const urlParams = new URLSearchParams(window.location.search);

// 'query' 파라미터 값 가져오기
const query = urlParams.get('query');
console.log('Query:', query); // 출력: Query: react

// 'page' 파라미터 값 가져오기
const page = urlParams.get('page');
console.log('Page:', page);   // 출력: Page: 10

// 'type' 파라미터 값 변경하기
urlParams.set('type', 'webdev');
console.log('Updated URLSearchParams:', urlParams.toString()); // 출력: query=react&page=10&type=webdev

// 새로운 파라미터 추가
urlParams.append('sort', 'desc');
console.log('Appended URLSearchParams:', urlParams.toString()); // 출력: query=react&page=10&type=webdev&sort=desc

// 'page' 파라미터 삭제
urlParams.delete('page');
console.log('Deleted URLSearchParams:', urlParams.toString()); // 출력: query=react&type=webdev&sort=desc

// 'query' 파라미터 존재 여부 확인
console.log('Has query:', urlParams.has('query')); // 출력: true

// 모든 파라미터 순회
console.log('All parameters:');
for (const [key, value] of urlParams.entries()) {
  console.log(`${key}: ${value}`);
}
// 출력:
// query: react
// type: webdev
// sort: desc
```

<br />

`새로운 쿼리 문자열 생성 및 사용`

```js
const newParams = new URLSearchParams();

newParams.append('category', 'javascript');
newParams.append('tags', 'typescript');
newParams.append('tags', 'react'); // 같은 키로 여러 값 추가 가능
newParams.set('limit', '50');

console.log('New URLSearchParams:', newParams.toString()); // 출력: category=javascript&tags=typescript&tags=react&limit=50

// 생성된 쿼리 문자열을 사용하여 새로운 URL 생성
const baseUrl = 'https://api.example.com/products';
const fullUrl = `${baseUrl}?${newParams.toString()}`;
console.log('Full URL:', fullUrl); // 출력: https://api.example.com/products?category=javascript&tags=typescript&tags=react&limit=50
```

<br />

`실제 사용 예시`

```js
import dayjs from 'dayjs';

// 1. 쿼리 파라미터 데이터의 간결한 타입 정의
interface RequestParams {
  type: string;
  id: string;
  name: string;
  date: string; // dayjs로 포맷팅된 문자열을 받을 예정
  status: string;
}

// 2. 쿼리 파라미터 객체 구성
// 여기서 데이터의 최종 포맷팅이 이루어집니다 (예: dayjs 객체 -> 'YYYYMMDD' 문자열).
const requestParams: RequestParams = {
  type: "product_info", // 요청 타입
  id: "PROD_XYZ", // 실제 사용하는 ID
  name: "유선 이어폰",
  date: dayjs("2024-06-10").format("YYYYMMDD"), // 날짜 포맷팅
  status: "재고있음",
};

// 3. URLSearchParams를 사용하여 최종 쿼리스트링 생성
const queryString = new URLSearchParams(requestParams).toString();

// 4. 생성된 쿼리스트링 확인 및 활용
console.log(queryString);
// 예시 출력: type=product_info&id=PROD_XYZ&name=%EC%9C%A0%EC%84%A0+%EC%9D%B4%EC%96%B4%ED%8F%B0&date=20240610&status=%EC%9E%AC%EA%B3%A0%EC%9E%88%EC%9D%8C

// 이 쿼리스트링은 HTTP 요청(Fetch API, Axios 등)에 바로 사용할 수 있습니다.
// 예: fetch(`/api/data?${queryString}`)
// 예: axios.get('/api/data', { params: requestParams })
```
