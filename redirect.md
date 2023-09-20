# 간단하게 리다이렉트 시켜보자!

```
파라미터로 path 이름을 받아와서 리다이렉트 시키는 함수
```
```javascript
function mainPage(path) {
  const params = window.location.search;
  const currentPath = path;
  
  return location.href = `/${currentPath}${params}`;
}
```
