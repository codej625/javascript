## a 태그를 주소 이동이 아닌 자바스크립트 작동방식으로 활용해보자!

```html
<ul>
  <li>
    <a href="javascript:void(0);" onclick="click()">list 1</a>
  </li>
  <li>
    <a href="javascript:void(0);" onclick="click()">list 2</a>
  </li>
  <li>
    <a href="javascript:void(0);" onclick="click()">list 3</a>
  </li>
</ul>
```
```
* 설명
javascript:void(0);"는 자바스크립트 이벤트 핸들러에서 주로 사용되는 특별한 JavaScript 표현식이다.
이 표현식은 주로 "href" 속성에 할당되어 클릭 이벤트를 처리하고 페이지가 다시 로드되지 않도록 방지하는 데 사용된다.
```
```
* 자세한 설명
1. javascript:는 링크의 URL을 자바스크립트로 처리하겠다는 것을 나타낸다.
2. void(0);는 JavaScript에서 "undefined" 값을 반환하는 표현식이다.
   "void" 연산자는 뒤에 오는 표현식을 실행하고 그 결과를 "undefined"로 만든다.
```
```
* 결론
javascript:void(0);은 클릭할 때 아무것도 하지 않고 현재 페이지에서 이동하지 않도록 만드는 표현식이다.
이것은 일반적으로 JavaScript 이벤트 핸들러에서 링크의 기본 동작을 막을 때 사용된다.
예를 들어, 페이지의 내용을 동적으로 변경하거나 모달 창을 열 때 사용된다.
```
