# forEach를 사용해서 여러 Element 접근하기

<br /><br />

```
간혹, 여러 Element의 값을 가져오기 위해
querySelector()를 과도하게 하드 코딩 할 때가 있다.

이럴때 forEach()를 사용해서 하드 코딩을 줄여보자.
```

<br /><br /><br />

```javascript
// Before

  const empId = document.querySelector('#userInfoId').value;
  const locId = document.querySelector('#userInfoLoc').value;
  const deptId = document.querySelector('#userInfoDeptId').value;
  const posId = document.querySelector('#userInfoPosId').value;
  const authId = document.querySelector('#userInfoAuth').value;
  const empEmail = document.querySelector('#userInfoEmail').value;
  const empPhone = document.querySelector('#userInfoPhone').value;
  

  const userInfo = {
    empId,
    empLoc,
    empDeptId,
    empPosId,
    empAuthId,
    empEmail,
    empPhone
  };
```

<br />

```javascript
// After

const fields = ['Id', 'Loc', 'DeptId', 'PosId', 'Auth', 'Email', 'Phone'];
const userInfo = {};

fields.forEach(field => {
  userInfo[`emp${field}`] = document.querySelector(`#userInfo${field}`).value;
});
```
