# axios를 사용해보자!

```javascript
const url = '/';
const dbData = {
  id: 'admin',
  pw: '1234',
  auth
};

async function axiosRecord() {
  try {
    const response = await axios.post(`${url}`, dbData, {
      timeout: 5000, // override the default timeout for this request
      headers: {
        'Content-Type': 'application/x-www-form-urlencoded',
      },
    });
    
    if (response.status === 200) {

    } 
  } catch (err) {
    alert('서버와 통신하는 동안 오류가 발생했습니다.');

    const params = window.location.search;
    const currentPath = window.location.pathname.split('/')[1];
    
    return location.href = `/${currentPath}${params}`;
  }
}
```

```javascript
ex) 함수 실행이 아닌 로직 중에 axios를 사용할 때는 익명 함수를 활용하자.

const send = async () => {
  try {
    const response = await axios.post(`${url}`, dbData, {
      timeout: 5000, // override the default timeout for this request
      headers: {
        'Content-Type': 'application/x-www-form-urlencoded',
      },
    });
    if (response.status === 200) {
      console.log('status 200');
    }
  } catch (err) {
    alert('서버와 통신하는 동안 오류가 발생했습니다.');

    return window.location.reload();
  }
}
send();
```
