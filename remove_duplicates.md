# 중복제거를 해보자!

<br/>

```javascript
function removeDuplicatesByKeys(arr, keys) {
  /* 중복 제거를 위한 Set 객체 생성 */
  const uniqueSet = new Set();
  /* 중복 제거된 객체들을 담을 배열 */
  const uniqueArray = [];
  
  arr.forEach(obj => {
    /* keys 배열에 정의된 프로퍼티들을 조합한 문자열을 생성하여 중복 여부를 확인 */
    let keyString = keys.map(key => obj[key]).join('-');
    /* Set에 keyString이 없는 경우, 중복이 아니므로 해당 객체를 추가하고 uniqueSet에 keyString 추가 */
    if (!uniqueSet.has(keyString)) {
      uniqueSet.add(keyString);
      uniqueArray.push(obj);
    }
  });
  return uniqueArray;
}
```

```javascript
try {
  const keys = [ /* 중복 제거 옵션 */
    'ip',
    'name',
    'gender',
    'mobile',
    'birthday'
  ];
  const result = removeDuplicatesByKeys(obj, keys);
} catch {
  ...
}
```
