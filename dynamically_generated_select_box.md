# 테이블 데이터에 따라 특정 데이터를 기준으로 자동 생성되는 셀렉트박스를 만들어보자!

<br />

1. CSS
```css
.marig-right {
  margin-right: auto;
  margin-left: .5rem!important;
  display: flex;
  border: 1px solid #6c757d;
  border-radius: .3rem;
}

.marig-right select {
  margin: 0;
  width: 100% !important;
  height: 100% !important;
}

.marig-right select,
.marig-right button {
  border: 1px solid #fff;
  border-radius: .25rem;
}
```

2. HTML
```html
<div class="marig-right">
  <div class="mr-1">
    <select class="search-channel">
      <option>전체 채널</option>
    </select> 
  </div>
  <button id="search-channel" class="btn btn-outline-secondary" type="button">채널 검색</button>
</div>
```

3. Javascript
```javascript
// Function ============================================================================
function channelList(data) {
  const select = document.querySelector('.search-channel');
  const set = new Set(); /* 중복 제거를 위한 set 객체 생성 */
  
  data.forEach(option => {
    set.add(cutMediaString(option.media));
  });
  const optionValues = Array.from(set);

  /* 옵션들을 만들어 모은다. */
  const fragment = document.createDocumentFragment();
  optionValues.forEach(value => {
    const optionTag = document.createElement('option');
    optionTag.value = value;
    optionTag.textContent = value;
    fragment.appendChild(optionTag);
  });

  select.innerHTML = '<option>전체 채널</option>'; /* reset */
  select.appendChild(fragment);
}

const searchByChannel = document.querySelector('#search-channel');
searchByChannel.addEventListener('click', () => {
  const selectValue = document.querySelector('.search-channel').value;
  try {
    const getFilteredData = obj.filter(option => cutMediaString(option.media) === selectValue);
    visitTable(getFilteredData);
  } catch {
    alert('날짜 검색을 먼저 실행해주세요.');
  }
  /* select 요소의 value 변경 */
  document.querySelector('.search-channel').value = selectValue;
});
```
```
위에 스크립트에서 data는 테이블을 만드는 데이터이고, obj는 Global Variable으로 처음 가져온 data 객체를 대입해놓은 값이다.
```
