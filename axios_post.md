# axios를 사용해보자!

<br/>

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
  } catch (err) {
    ...
  }
}
```

```javascript
ex) 함수 실행이 아닌 로직 중에 axios를 사용할 때는 익명 함수를 활용하자.

const send = async () => {
  try {
    ...
  } catch (err) {
    ...
  }
}
send();
```

```javascript
ex) 즉시 실행 함수를 활용할 수 있다.

(async () => {
  try {
    ...
  } catch (err) {
    ...
  }
})();
```


