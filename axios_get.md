# axios get방식에 대해 알아보자!

<br/>

get 방식으로 파라미터를 보내는 방법 1번
```javascript
const start = document.querySelector('input[name="date-start"]');
const end = document.querySelector('input[name="date-end"]');

(async () => {
  try {
    const res = await axios.get('/scheduler/select', {
      params: {
        start: start.value,
        end: end.value
      },
      timeout: 5000, // override the default timeout for this request
      headers: {
        'X-CSRF-TOKEN': document.querySelector('meta[name="_csrf"]').content,
      },
    });
    
    if (res.status === 200) {
     
    }
  } catch (err) {
    console.log('err => ', err);
  }
})();
```

<br/>

get 방식으로 파라미터를 보내는 방법 2번
```javascript
const start = document.querySelector('input[name="date-start"]');
const end = document.querySelector('input[name="date-end"]');

(async () => {
  try {
    const res = await axios.get(`/scheduler/select?start=${start}&end=${end}`, {
      timeout: 5000, // override the default timeout for this request
      headers: {
        'X-CSRF-TOKEN': document.querySelector('meta[name="_csrf"]').content,
      },
    });
  } catch (err) {
    console.log('err => ', err);
  }
})();
```
