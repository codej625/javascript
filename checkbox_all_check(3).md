# 체크 되어 있는 row의 값들만 가져오는 방법!

<br />

```html
<div id="checkBox"></div>
```

```javascript
(() => {
  const html = document.querySelector('#checkBox');
  html.innerHTML = `
    <table>
      <thead>
        <tr>
          <th><input id="all" name="select-all" type="checkbox"></th>
          <th>이름</th>
          <th>나이</th>
          <th>성별</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td><input class="single" name="select" type="checkbox" value="1"></td>
          <td>이진우</td>
          <td>34살</td>
          <td>남자</td>
        </tr>
        <tr>
          <td><input class="single" name="select" type="checkbox" value="2"></td>
          <td>김진주</td>
          <td>31살</td>
          <td>여자</td>
        </tr>
        <tr>
          <td><input class="check" name="select" type="checkbox" value="3"></td>
          <td>김원찬</td>
          <td>34살</td>
          <td>남자</td>
        </tr>
      </tbody>
    </table>
  `;
})();
/* 전체 체크시에도 객체가 생성되게 클로저를 사용하여 기능 구현해야 함 */

const all = document.querySelector('input[name="select-all"]');
const single = document.querySelectorAll('input[name="select"]');

all.addEventListener('click', () => {
  const check = all.checked;

  single.forEach(chk => {
    chk.checked = check;
  });
});
single.forEach(chk => {
  chk.addEventListener('change', () => {
    let allChecked = true;
    const set = new Set();

    single.forEach(chk => {
      if (chk.checked) {
        const tr = chk.parentNode.parentNode;
        const td = tr.querySelectorAll('td');
        const obj = {};

        td.forEach((element, index) => {
          if (index === 1) {
            obj['name'] = element.textContent;
          }
          if (index === 2) {
            obj['age'] = element.textContent;
          }
          if (index === 3) {
            obj['sex'] = element.textContent;
          }
        });
        set.add(obj); /* 중복 제거 */
      }

      if (!chk.checked) {
        allChecked = false;
      }
    });
    all.checked = allChecked;

    set.forEach(ele => {
      console.log(ele);
    });
  });
});
```
