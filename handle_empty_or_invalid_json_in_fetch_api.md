# Fetch API에서 빈 JSON 또는 잘못된 JSON 처리하기

<br /><br />

```
Fetch를 사용해 요청 데이터를 응답받아 처리할 때,
.json() 를 사용하여 JSON으로 변환하려고 하면 빈 문자열(＂＂)이나 잘못된 JSON 형식에서 오류가 발생한다.

이런 문제를 방지해보자.
```

<br /><br /><br />

* 예시
---

```javascript
(async () => {
  try {
    const response = await fetch('/user', {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ userId })
    });

    if (!response.ok) {
      return alert('사용자 검색에 실패하였습니다.');
    }

    const text = await response.text();
    if (!text) {
      return alert('응답이 비어 있습니다.');
    }

    try {
      const user = JSON.parse(text);
      console.log(user);
    }
    catch (jsonError) {
      return alert('JSON 파싱 중 오류가 발생했습니다.');
    }
  }
  catch (error) {
    alert('네트워크 연결이 원활하지 않습니다.');
    console.error(error);
  }
})();
```
