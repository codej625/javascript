# 엑셀 파일 다운로드 처리를 프론트에서 해보자!

<br/>

```
Excel JS 라이브러리를 사용해서 구현
```
1. import

ex) cdn import
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.14.3/xlsx.full.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/FileSaver.js/1.3.8/FileSaver.min.js"></script>
```

<br/>

ex2) script import
```html
<script src="/script/FileSaver.min.js" type="text/javascript"></script>
<script src="/script/xlsx.full.min.js" type="text/javascript"></script>
```

2. script 작성
```javascript
function tableToExcel() { /* table to excel */
  const fileName = 'file_name.xlsx';
  const tableName = document.getElementById('table_name');
  const workBook = XLSX.utils.table_to_book(tableName, { sheet: 'sheet_name', raw: true }); 
  
  return XLSX.writeFile(workBook, fileName, { bookType:'xlsx',  type: 'binary' }); /* excel extension, binary or string */
}
// Function ============================================================================
document.getElementById('click_element_name').addEventListener('click', () => {
  return tableToExcel();
});
```
