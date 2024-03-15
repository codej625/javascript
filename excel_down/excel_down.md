# 엑셀 파일 다운로드 처리를 프론트에서 해보자!

<br />

```
Excel JS 라이브러리를 사용해서 구현
```

<br />

1. CDN Import
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.14.3/xlsx.full.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/FileSaver.js/1.3.8/FileSaver.min.js"></script>
```

<br />

2. Script
```javascript
function tableToExcel() { /* table to excel */
  const tableName = document.getElementById({table_id});
  const workBook = XLSX.utils.table_to_book(tableName, { sheet: {sheet_name}, raw: true }); 
  const fileName = '{file_name}.xlsx';
  
  return XLSX.writeFile(workBook, fileName, { bookType:'xlsx',  type: 'binary' }); /* excel extension, binary or string */
}
document.getElementById('click_element').addEventListener('click', tableToExcel());
```
