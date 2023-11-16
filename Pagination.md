# 페이징을 구현해보자!

<br/>

1. HTML
```html
<div>
  <table id="table" class="">
    <colgroup>
      <col width="*">
      <col width="*">
    </colgroup>
    <thead class="thead-light">
      <tr>
        <th>columns1</th>
        <th>columns2</th>
      </tr>
    </thead>
    <tbody id="create-table-row"></tbody>
  </table>
  <div id="pagination" class="pagination"></div>
</div>
```

<br/>

3. script
```javascript
let currentPage = 1;
const pageSize = 10;
const maxPageButtons = 5;

function fetchData(page) {
  currentPage = page;
  const rowStart = (page - 1) * pageSize + 1;
  const rowEnd = rowStart + pageSize - 1;

  console.log(rowStart, rowEnd); /* ex) 1, 10 */
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
  tableBody.innerHTML = data.map(item => `<tr><td>${item.domain_name}</td><td>${item.expiration_date}</td></tr>`).join(''); /* contents */
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
```
간단 설명

1) fetchData 
이 함수는 페이지 번호를 인자로 받아, 현재 페이지(currentPage)를 설정 한다.
rowStart와 rowEnd를 계산하여 서버에 요청할 데이터의 범위를 지정 한다.
fetch API를 사용해 서버로부터 데이터를 받아오며, 성공 시 displayDataFromAPI와 updatePaginationButtons 함수를 호출 한다.

2) displayDataFromAPI
이 함수는 서버로부터 받은 데이터를 테이블에 표시 한다.
data 배열을 반복하여 HTML 테이블 행(<tr>)을 생성하고, 이를 테이블 본문에 삽입 한다.

3) updatePaginationButtons
이 함수는 전체 페이지 수와 현재 페이지를 기반으로 페이징 버튼을 업데이트 한다.
totalPage는 전체 페이지 수를 계산 한다.
startPage와 endPage는 표시할 페이지 버튼의 시작과 끝 번호를 계산 한다.
페이지 버튼은 동적으로 생성되며, 각 버튼은 fetchData 함수를 호출하도록 설정 된다.

4) 페이지 초기 로드
스크립트가 로드되면 fetchData(1)이 호출되어 첫 번째 페이지의 데이터를 로드 한다.
```

<br/>

4. 백엔드 서버(스프링으로 간단하게 구현시)
```java
RestController

@GetMapping(value = "/history/select")
public Map<String, Object> selectHistory(@RequestParam HashMap<String, Integer> params) throws Exception {
  log.info(">>> DevRestController selectHistory >>>");
  
  HashMap<String, Object> result = new HashMap<>();
  result.put("total", mainMapper.selectHistoryCount());
  result.put("row", mainMapper.selectHistory(params));

  return result;
}
```
```java
Mapper

public List<Map<String, Object>> selectHistory(Map<String, Integer> params) throws Exception;
public Integer selectHistoryCount() throws Exception;
```
```XML
Mybatis
- MySQL 사용시 8버전 이하라면 lownum 함수를 사용 못하므로, LIMIT을 사용한다.
${rowStart}만 사용하고 뒷자리는 고정, script단에서 rowStart변수에 -1을 한다. ex) rowStart-1

<select id="selectHistory" parameterType="hashmap" resultType="hashmap">
  SELECT * 
  FROM domain_records 
  ORDER BY seq
  LIMIT ${rowStart}, 10
</select>

<select id="selectHistoryCount" resultType="integer">
  SELECT count(*)
  FROM domain_records
</select>
```
