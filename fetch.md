# fetch를 사용하는 비동기 처리

<br/><br/>

1. POST
```javascript
const sendClientID = async (key) => {
  try {
    const response = await fetch('/auth/login', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ key })
    });
    if (response.ok) console.log('response ', response);

  } catch (error) {
    console.error('Error ', error);
  }
};
sendClientID('codej625');
```

<br />

2. GET
```javascript
const fetchData = async () => {
  try {
    const response = await fetch('/auth/login');

    if (response.ok) console.log('response ', response);

  } catch (error) {
    console.error('Error ', error);
  }
}
fetchData();
```
