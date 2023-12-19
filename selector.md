# 선택자를 알아보자!

<br/>

1) name 값 가져오기
```javascript
ex)
document.querySelector('input[name="name"]'); /* tag + name으로 값을 가져온다. */
```

<br/>

2) class 값 가져오기
```javascript
ex)
document.querySelector('.${class}');
document.querySelectorAll('.${class}'); /* class 값이 복수일때는 querySelector + All을 붙인다. */ 
document.getElementsByClassName('${class}'); /* class 값이 복수일때 [0]와 같이 인덱스를 사용한다. */
```

<br/>

3) id 값 가져오기
```javascript
ex)
document.querySelector('#${id}');
document.getElementById('${id}');
```
