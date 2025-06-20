# 윈도우의 사이즈를 알아보자!

<br />
<br />

* 뷰포트(viewport)

---

```
웹 브라우저에서 실제로 콘텐츠가 표시되는 영역을 의미한다.

사용자가 현재 화면에서 볼 수 있는 웹 페이지의 부분으로,
브라우저 창의 크기에서 툴바, 스크롤바, 주소 표시줄 등을 제외한 영역을 말한다.
```

<br />
<br />
<br />
<br />

1. 특징

<br />

`크기`

```
뷰포트의 크기는 window.innerWidth와 window.innerHeight를 통해
픽셀 단위로 확인할 수 있다.
```

<br />

`반응형 디자인`

```
뷰포트 크기에 따라 웹 페이지의 레이아웃이나,
스타일을 조정하는 데 자주 사용한다.
```

<br />

`모바일 고려`

```
모바일 기기에서는 메타 태그(<meta name="viewport">)를 사용해
뷰포트의 크기와 스케일을 설정하여 반응형 웹을 최적화한다.
```

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

<br />

`window.innerHeight`

```
브라우저 창의 뷰포트 높이(픽셀 단위)를 반환한다.

여기에는 툴바나 스크롤바를 제외한 실제 콘텐츠 영역의 높이가 포함된다.
```

<br />

`window.innerWidth`

```
브라우저 창의 뷰포트 너비(픽셀 단위)를 반환한다.

마찬가지로 스크롤바 등을 제외한 콘텐츠 영역의 너비이다.
```

```
window.innerHeight, window.innerWidth 이 두 속성은 읽기 전용이며,
현재 브라우저 창의 크기를 동적으로 확인할 때 유용하다.
```

<br />

`스크롤바와 툴바 제외`

```
innerWidth와 innerHeight는 스크롤바, 툴바, 주소 표시줄, 개발자 도구 같은 브라우저 UI 요소를 제외한 뷰포트의 크기를 반환한다.

전체 브라우저 창 크기(이 요소들을 포함)를 확인하려면 window.outerWidth와 window.outerHeight를 사용해야 한다.
```

<br />
<br />
<br />

2. 사용 예시

<br />

`실시간 크기 변화 감지`

```
브라우저 창 크기가 변경될 때마다 사이즈를 확인하려면,
resize 이벤트를 사용한다.
```

```js
// 이 코드는 창 크기가 변경될 때마다 새로운 높이와 너비를 출력한다.

window.addEventListener("resize", () => {
  console.log(`윈도우 높이: ${window.innerHeight}px, 너비: ${window.innerWidth}px`);
});
```

<br />

`반응형 디자인`

```js
// 뷰포트 크기에 따라 다른 스타일을 적용하는 예시

function updateLayout() {
  if (window.innerWidth < 768) {
    console.log("모바일 뷰 적용");
    // 모바일용 스타일/로직 적용
  }
  else {
    console.log("데스크톱 뷰 적용");
    // 데스크톱용 스타일/로직 적용
  }
}

window.addEventListener("resize", updateLayout);
window.addEventListener("load", updateLayout);
```
