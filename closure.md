# 클로저를 알아보자!

<br />

```javascript
const counter = (function () {
  let privateCounter = 0;

  function changeBy(val) {
    privateCounter += val;
  }

  return {
    increment() {
      changeBy(1);
    },

    decrement() {
      changeBy(-1);
    },

    value() {
      return privateCounter;
    },
  };
})();

console.log(counter.value()); /* 0 */
counter.increment();
console.log(counter.value()); /* 1 */
counter.decrement();
console.log(counter.value()); /* 0 */
```

<br />

```javascript
/* ex) */

function tbody() {
  let tbody = null;

  function re() {
    tbody = document.querySelectorAll('#tbody tr');
  }
  function reload() {
    re();
  }
  function result() {
    return tbody;
  }
  
  return {
    reload: reload(),
    result: result()
  }
}

tbody().reload;
console.log(tbody().result);
```
