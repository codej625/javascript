# map()을 사용해서 반복되는 contents를 만들어보자!

<br/>

```javascript
function createContents(list) { /* array(object) */
  const body = document.querySelector('#contents-body'); /* 요소가 들어갈 공간*/
  
  body.innerHTML = list.map(element => { /* map()을 사용해서 가공된 새로운 배열을 return 한다. */
    return `
            <div class="card over">
              <div class="card-body">
                <p>${element.title}</p>
                <div class="history-body">${element.onset}</div>
              </div>
            </div>
           `;
  }).join('');
}
```
