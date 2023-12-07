# 아이프레임을 활용해보자!

<br />

```javascript
window.onload = () => {
  const queryString = window.location.search;
  const locationURL = `${iframeUrl}${queryString}`;

  const frameSet = document.querySelector('body').appendChild(document.createElement("iframe"));
  frameSet.id = "locationFrame";
  frameSet.src = locationURL;
  frameSet.width = "100%";
  frameSet.height = "100%";
}
```

<br />

```html
<body>
  <iframe id="frameSet" src="${url}"></iframe>
</body>
```
