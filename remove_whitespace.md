# Javascript 공백 제거

<br />
<br />

* trim() 메서드를 사용해보자.
---

```
가끔 input 값에 공백을 입력하거나,
로직이 처리되는 과정에서 공백이 생기는 경우가 있다.

이럴때 간단하게 trim()이라는 메서드를 사용하여 해결할 수 있다.
```

<br />
<br />
<br />
<br />

1. 객체에서 공백을 제거

```
payload 값으로 사용하는 객체의 공백이 생겼을 때,
string 타입을 확인하고 일괄적으로 공백을 제거하는 방법이다.
```

```tsx
const handleSubmit = (data: any) => {
  const formData = Object.fromEntries(
    Object.entries(data).map(([key, value]) => [
      key,
      typeof value === "string" ? value.trim() : value,
    ])
  );

  ...

```
