# Pagination

<br /><br />

1. HTML

```html
<ul class="pagination">
  <li><button id="first-btn">First</button></li>
  <li><button id="prev-btn">Previous</button></li>
  <li id="page-buttons"></li>
  <li><button id="next-btn">Next</button></li>
  <li><button id="last-btn">Last</button></li>
</ul>
```

<br /><br /><br />

2. CSS

```css
.pagination {
  display: flex;
  list-style-type: none;
  padding: 0;
}
.pagination li {
  margin: 0 5px;
}
.pagination button {
  padding: 5px 10px;
  cursor: pointer;
}
.pagination button:disabled {
  cursor: not-allowed;
  opacity: 0.5;
}
```

<br /><br /><br />

3. Javascript

```javascript
let currentPage = 1; // 현재 페이지
let currentGroupStart = 1; // 현재 페이지 그룹의 시작 페이지
const rowsPerPage = 15; // 페이지당 데이터 개수
const buttonsPerGroup = 5; // 페이지 그룹당 버튼 개수

// 데이터와 총 데이터 개수를 서버에서 가져오는 함수
const fetchData = async (start, end) => {
  try {
    // 총 데이터 개수 가져오기
    const countResponse = await fetch('/api/total-count');
    const totalCount = await countResponse.json();
    const totalPages = Math.ceil(totalCount / rowsPerPage);

    // 페이지 데이터 가져오기
    const dataResponse = await fetch(`/api/data?start=${start}&end=${end}`); // start, end 파라미터 필수
    const data = await dataResponse.json();

    return { data, totalPages };
  }
  catch { return { data: [], totalPages: 0 }; }
};

// 페이지 업데이트 함수
const updatePage = async (page) => {
  if (page < 1 || page > Math.ceil(totalCount / rowsPerPage)) return;
  currentPage = page;

  // 데이터 범위 계산
  const start = (page - 1) * rowsPerPage + 1;
  const end = Math.min(start + rowsPerPage - 1, totalCount);

  // 서버에서 데이터 가져오기
  const { data, totalPages } = await fetchData(start, end);

  // 데이터 업데이트
  const dataContainer = document.getElementById('data-container');
  dataContainer.innerHTML = data.map(ele => ele.key).join("<br>"); // 예시

  // 페이지 버튼 업데이트
  const pageButtonsContainer = document.getElementById('page-buttons');
  pageButtonsContainer.innerHTML = '';

  // 현재 페이지 그룹의 시작과 끝 페이지 계산
  const startPage = currentGroupStart;
  const endPage = Math.min(startPage + buttonsPerGroup - 1, totalPages);

  for (let i = startPage; i <= endPage; i++) {
    const button = document.createElement('button');
    button.textContent = i;
    button.disabled = i === currentPage;
    button.onclick = () => updatePage(i);
    pageButtonsContainer.appendChild(button);
  }

  // 네비게이션 버튼 업데이트
  document.getElementById('prev-btn').disabled = currentGroupStart === 1;
  document.getElementById('next-btn').disabled = endPage === totalPages;
  document.getElementById('first-btn').disabled = currentGroupStart === 1;
  document.getElementById('last-btn').disabled = endPage === totalPages;
};

// 버튼 클릭 이벤트 설정
document.getElementById('first-btn').onclick = () => {
  currentGroupStart = 1;
  updatePage(1);
};

document.getElementById('prev-btn').onclick = () => {
  currentGroupStart = Math.max(1, currentGroupStart - buttonsPerGroup);
  updatePage(currentGroupStart);
};

document.getElementById('next-btn').onclick = () => {
  const totalPages = Math.ceil(totalCount / rowsPerPage);
  currentGroupStart = Math.min(totalPages - buttonsPerGroup + 1, currentGroupStart + buttonsPerGroup);
  updatePage(currentGroupStart);
};

document.getElementById('last-btn').onclick = () => {
  const totalPages = Math.ceil(totalCount / rowsPerPage);
  currentGroupStart = Math.max(1, totalPages - buttonsPerGroup + 1);
  updatePage(currentGroupStart);
};

// 초기화
let totalCount = 0;
const initialize = async () => {
  try {
    const response = await fetch('/api/total-count'); // 예시
    totalCount = await response.json();
    updatePage(currentPage);
  }
  catch { console.error('Failed to initialize pagination error'); }
};

initialize();

// fetchData 함수
// start와 end 파라미터를 사용하여 서버에서 데이터를 가져온다.
// 총 데이터 개수를 가져와 totalPages를 계산한다.


// updatePage 함수
// start와 end를 계산하여 해당 범위의 데이터를 서버에서 가져온다.
// 페이지 버튼을 현재 페이지 그룹에 맞게 업데이트한다.


// 초기화
// initialize 함수에서 총 데이터 개수를 가져와 페이지를 로드한다.


// 버튼 클릭 이벤트
// 페이지 그룹 변경 시 currentGroupStart를 조정하고 페이지를 업데이트한다.
```

<br /><br /><br />

4. Java

```java
// Controller

@ResponseBody
@GetMapping(value = "/api/total-count") // 예시
public ResponseEntity<Integer> getTotalCount() {
    Integer totalCount = accountMapper.getTotalCount();

    return ResponseEntity.ok(totalCount);
}

@ResponseBody
@GetMapping(value = "/api/data") // 예시
public ResponseEntity<List<{model_name}>> getData(@RequestParam String start, @RequestParam String end) {

    List<{model_name}> data = accountMapper.getData(new HashMap<String, Object>() {{
        put("start", start);
        put("end", end);
    }});

    return ResponseEntity.ok(data);
}

// 테스트이기 때문에 Service layer 제외.

// Mapper Interface

@Mapper
public interface Mapper {
    public Integer getTotalCount();
    public List<{model_name}> getData(Map<String,Object> params);
}
```

<br /><br /><br />

5. Mybatis

```XML
<!-- Oracle -->

<select id="getData" parameterType="hashmap" resultType="hashmap" or resultMap="">
    SELECT X.*
           , TO_CHAR(X.LAST_LOGGED, 'YYYY-MM-dd') // LocalDateTime이 지원하지 않을 시 문자열로 변환
    FROM   (
            SELECT *
                   , ROW_NUMBER() OVER (ORDER BY {기준_컬럼}) AS ROWNUM
            FROM {table_name}
           ) X
    WHERE  X.rnum BETWEEN #{start} AND #{end}
</select>

<select id="getTotalCount" resultType="integer">
  SELECT count(*)
  FROM   {table_name}
</select>
```

<br />

```XML
<!-- MySQL 8 이하 버전 -->
<!-- MySQL 사용시 8버전 이하라면 lownum 함수를 사용 못하므로, LIMIT을 사용한다. -->

<select id="getData" parameterType="hashmap" resultType="hashmap" or resultMap="">
  SELECT * 
  FROM {table_name}
  ORDER BY {기준_컬럼} // 정렬 기준
  LIMIT ${start}, 10
</select>

<select id="getTotalCount" resultType="integer">
  SELECT count(*)
  FROM {table_name}
</select>
```
