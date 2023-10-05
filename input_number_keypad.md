# 모바일화면에서 키패드 입력시 숫자키패드 전환이 자동으로 일어나게 해보자!

```html
<input name="" type="number" pattern="\d*" maxlength="11" oninput="maxLengthCheck(this);" placeholder=""> // 아이폰 호환을 위해 패턴과 함수 사용
```

```javascript
function maxLengthCheck(object){
  if (object.value.length > object.maxLength){
    object.value = object.value.slice(0, object.maxLength);
  }
}
```
