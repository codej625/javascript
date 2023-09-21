# 유효성 검사를 해보자!

```javascript
function validation(data) { // data 파라미터에는 버튼 이름으로 유효성 검사 종류를 선택할 수 있게 한다.
  let result;
  if (data === 'pc-db-box') {
    result = pcValidation();
  }
  if (data === 'm-db-box') {
    result = mobileValidation();
  }
  console.log(result); // db 정보를 담아 사용한다.
}

function pcValidation() {
  let name = document.querySelector('input[name="name"]'); // ''값을 대입하기 위해 let으로 선언한다.
  let birthday = document.querySelector('input[name="birthday"]');
  let phone = document.querySelector('input[name="phone"]');
  const gender = document.querySelector('input[name="gender"]:checked');
  
  const db = {
    name: name.value,
    birthday: birthday.value,
    phone: phone.value,
    gender: gender.value
  };
  
  if (!validateName(name.value)) {
    name.value = '';
    alert('이름을 정확히 입력해주세요.');
    
    return false;
  }
  if (!validateBirthday(birthday.value)) {
    birthday.value = '';
    alert('생년월일을 정확히 입력해주세요.');
    
    return false;
  }
  if (!validatePhone(phone.value)) {
    phone.value = '';
    alert('연락처를 정확히 입력해주세요.');
    
    return false;
  }
  return db; // db에 전송할 값들을 담은 객체를 리턴
}
```
```javascript
function validateName(name) {
  const regName = /^[가-힣]+$/; // 한글만
  const result = regName.test(name) ? true : false;
  
  if(result ? true : false) {
    return nameLength = (name.length > 1) ? true : false;
  }
  return result;
}

function validateBirthday(birthday) {
  const regBirthday = /^(19[0-9][0-9]|20\d{2})(0[0-9]|1[0-2])(0[1-9]|[1-2][0-9]|3[0-1])$/;
  const chkBirthday = regBirthday.test(birthday) ? true : false;
  
  return chkBirthday;
}

function validatePhone(phone) {
  const regPhone = /(010)([1-9]{1})([0-9]{3})([0-9]{4})$/; // (010)(0을 제외한 1~9까지 1개)(0~9까지 3개)(0~9까지 4개) 총 11자리
  const chkPhone = regPhone.test(phone) ? true : false;
  
  return chkPhone;
}
```
