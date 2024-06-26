# 자바스크립트로 HTML 요소(Element) 만들기

<br /><br />

1. createElement와 appendChild 메서드 사용하기
```javascript
// 1. 새로운 태그(element) 생성하기
const newElement = document.createElement('div');

// 2. 필요한 속성(attribute) 설정하기 (옵션)
newElement.id = 'myDiv';  // id 설정

// 3. 클래스(class) 추가하기
newElement.classList.add('myClass'); // 클래스 추가

// 4. 내용(content) 추가하기 (옵션)
newElement.textContent = 'Hello, world!'; // 텍스트 내용 추가

// 5. 생성한 요소를 기존 HTML 문서에 추가하기
document.body.appendChild(newElement); // body 요소에 추가
```

<br />

2. innerHTML 속성을 이용하기
```javascript
// 1. HTML 문자열로 새로운 요소 생성하기
const newElementHTML = '<div id="myDiv">Hello, world!</div>';

// 2. innerHTML을 사용하여 기존 HTML에 추가하기
document.body.innerHTML += newElementHTML;
```
