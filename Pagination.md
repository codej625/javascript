# 페이징을 구현해보자!

<br/>

```javascript
let currentPage = 1;
const pageSize = 10;
const maxPageButtons = 5;

function fetchData(page) {
  currentPage = page;
  const rowStart = (page - 1) * pageSize + 1;
  const rowEnd = rowStart + pageSize - 1;

  console.log(rowStart, rowEnd);
  fetch(`/history/select?rowStart=${rowStart}&rowEnd=${rowEnd}`, {
      method: 'get'
    })
    .then(response => response.json())
    .then(data => {
      displayDataFromAPI(data.row);
      updatePaginationButtons(data.total, currentPage);
    })
    .catch(error => {
      console.error('Error fetching data:', error);
    });
}

function displayDataFromAPI(data) {
  const tableBody = document.getElementById('table').getElementsByTagName('tbody')[0];
  tableBody.innerHTML = data.map(item => `<tr><td>${item.domain_name}</td><td>${item.expiration_date}</td></tr>`).join('');
}

function updatePaginationButtons(total, currentPage) {
  const totalPage = Math.ceil(total / pageSize);
  let startPage = Math.max(1, currentPage - Math.floor(maxPageButtons / 2));
  let endPage = Math.min(totalPage, startPage + maxPageButtons - 1);

  startPage = Math.max(1, endPage - maxPageButtons + 1);

  const paginationContainer = document.getElementById('pagination');
  paginationContainer.innerHTML = '';
  for (let i = startPage; i <= endPage; i++) {
    const button = document.createElement('button');
    button.innerText = i;
    button.onclick = () => fetchData(i);
    paginationContainer.appendChild(button);
  }
}

fetchData(1);
```

```javascript

```

```javascript

```
