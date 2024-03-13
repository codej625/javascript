# fetch를 사용해서 delete 기능을 만들어보자.

<br />

```
예를 들어 전화번호 차단 기능 구현 중 특정 seq(식별 값)를 가진
데이터를 DB에서 삭제해야 한다고 가정.
```
```javascript
async function deletePhone(seq) {
  const deleteCheck = confirm('삭제하시겠습니까?');
  
  if (deleteCheck) {
    try {
      /* csrf 처리 */
      const csrfToken = document.querySelector('meta[name="_csrf"]').getAttribute('content');
      const csrfHeader = document.querySelector('meta[name="_csrf_header"]').getAttribute('content');
      const errorMessage = 'Network error';
      
      const response = await fetch(`/blocked-numbers/${seq}`, {
        method: 'DELETE',
        headers: {
          'Content-Type': 'application/json',
          [csrfHeader]: csrfToken,
        },
      });

      if (!response.ok) {
        throw new Error(errorMessage);
      }

      alert('삭제되었습니다.');
      fetchData(); // fetchData 함수 호출

    } catch (error) {
      console.error(error);
      alert('Network error');
      /*
        ... 
        Additional logic needs to be added later. 
      */
    }
  } else {
    alert('취소하였습니다.');
  }
}
```

<br />

```
스프링으로 백엔드를 구현 시
```
```java
@DeleteMapping(value = "/blocked-numbers/{seq}", consumes = MediaType.ALL_VALUE)
public ResponseEntity<Void> deleteBlockedNumber(@PathVariable int seq) {
  log.info(">>> start >>>");
  
  try {
    admin_recordSecondMapper.deleteBlockedNumbers(seq);
    return new ResponseEntity<>(HttpStatus.CREATED);
  } catch (Exception e) {
    e.printStackTrace();
    return ResponseEntity.status(HttpStatus.INTERNAL_SERVER_ERROR).build();
  }
}
```
