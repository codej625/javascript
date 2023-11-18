# axios가 아닌 fetch를 사용하여 비동기 처리를 해보자!

<br/>

```javascript
ex) post

async function postData(url, data) {
  try {
    const requestOptions = {
      method: 'POST', // 요청 방식 설정
      headers: {
        'Content-Type': 'application/json' // 내용 유형을 JSON으로 설정
      },
      body: JSON.stringify(data) // 데이터를 JSON 문자열로 변환
    };

    const response = await fetch(url, requestOptions);
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }

    return response.json(); // JSON 형태로 응답을 파싱 한다.
  } catch (error) {
    console.error('Error:', error);
  }
}

postData('https://example.com/test', { test: 'test' })
  .then(data => {
    console.log(data);
  })
  .catch(error => {
    console.error('Error in postData:', error);
  });
```

```javascript
ex) get

async function fetchData(url) {
  try {
    const response = await fetch(url);
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }

    const data = await response.json();

    return data;
  } catch (error) {
    console.error('Fetch error:', error);
  }
}

fetchData('https://example.com/test')
  .then(data => {
    console.log(data);
  })
  .catch(error => {
    console.error('Error in fetchData:', error);
  });
```
아니면 즉시 실행 함수에 넣어서 함수를 실행시키는 것도 가능하다.
