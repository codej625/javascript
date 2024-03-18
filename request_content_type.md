# 자바스크립트에서 서버에 요청할 때 사용되는 헤더 값 중 하나인 Content type에 대해 알아보자.

<br />

```
"Content-Type" 헤더는 전송되는 데이터의 유형을 명시한다.
인코딩과 관련된 정보도 포함될 수 있지만,
주된 목적은 데이터의 형식이나 유형을 서버나 클라이언트에 알려주는 것이다.

일반적으로 많이 쓰이는 type을 살펴보자.
```

<br />

1. GET
```
GET 메서드는 주로 서버로 데이터를 요청할 때 사용된다.
이 때 데이터를 본문에 담는 것이 아니라 일반적으로 쿼리 문자열(query string)을 사용하여 데이터를 전달한다.
따라서 보통 "Content-Type"을 지정하지 않는다.
하지만 경우에 따라 필요한 경우 "application/x-www-form-urlencoded"을 사용할 수 있다.
```

<br />

2. POST
```
POST 메서드는 주로 서버로 데이터를 제출할 때 사용된다.
가장 일반적으로는 HTML 폼을 통해 전송되는 데이터를 다룰 때 "application/x-www-form-urlencoded"가 사용된다.
또한, JSON 데이터를 전송하는 경우에는 "application/json"을 사용하는 것이 일반적이다.
```

<br />

3. PUT & DELETE
```
PUT 및 DELETE 메서드는 주로 리소스를 업데이트하거나 삭제할 때 사용된다.
이러한 경우에는 보통 "application/json"이나 해당 리소스의 MIME 유형을 사용한다.
그러나 PUT 및 DELETE 요청에서는 종종 본문이 없는 경우가 있으므로 "Content-Type"을 지정하지 않을 수도 있다.
```

<br />

4. ETC
```
다른 메서드의 경우에도 요청의 목적과 데이터의 유형에 따라 다양한 "Content-Type"을 사용할 수 있다.
주로 사용되는 유형은 "application/json", "application/xml", "multipart/form-data" 등이 있다.
메서드와 상관없이 데이터의 유형과 목적에 따라 적절한 "Content-Type"을 선택하는 것이 중요하다.
```

