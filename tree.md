# 크리스마스 트리를 만들어보자!

<br/>

```javascript
let tree = "";

for (let i = 0; i < 15; i++) {
  for (let j = 15; j > i; j--) {
    tree += " ";
  }
  for (let k = 0; k < i * 2 + 1; k++) {
    tree += "*";
  }
  tree += "\n";
}
console.log(tree);
```
