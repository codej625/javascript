# javascript에서 this를 다시한번 제대로 알아보자!

```
this는 함수가 호출될 때 결정이 된다.(함수를 호출한 방법에 의해 결정)
```

<br/>

ex) 예시 1번
```javascript
const car = {
  name: 'kia',
  getName: function() {
    console.log('getName', this);
  },
};
car.getName(); /*
                 car객체 전체가 표시 된다.
                 내부에서 b를 호출한 형태(A에서 -> A.b를 호출)
               */
```

<br/>

ex) 예시 2번
```javascript
const car = {
  name: 'kia',
  getName: function() {
    console.log('getName', this);
  },
};

const globalCar = car.getName;
globalCar(); /*
               window 객체가 표시 된다.
               외부에서 b만 호출된 상태이기 때문에 최상위 객체인 window객체가 (외부에서 -> b를 호출)
             */
```

<br/>

ex) 예시 3번
```javascript
const car = {
  name: 'kia',
  getName: function() {
    console.log('getName', this);
  },
};

const car2 = {
  name: 'hyundai',
  getName: car.getName,
};
car2.getName(); /*
                  car2의 windows 객체가 표시 된다.
                  함수가 호출된 곳이 car2이기 때문에
                */
```

<br/>

ex) 예시 4번
```html
<button id="button">this는 누굴까?</button>
```
```javascript
const btn = document.getElementById('button');
btn.addEventListener('click', car.getName); /*
                                              <button id="button">this는 누굴까?</button>이 표시 된다.
                                              여기서 this는 => 'button' (함수를 호출한 대상이 'button'이므로)
                                            */
```

<br/>

```
위에 결과를 보면 알 수 있듯이, this의 주체는 계속해서 달라질 수 있다.
그래서 this의 주체를 고정하고 싶을 때 사용하는 키워드가 bind이다.
예제를 보면서 이해해보자.
```

ex) 예시 5번
```javascript
const car = {
  name: 'kia',
  getName: function() {
    console.log('getName', this);
  },
};

const car2 = {
  name: 'hyundai',
  getName: car.getName,
};

const bindGetName = car2.getName.bind(car);
bindGetName(); /*
                 car의 객체가 표시 된다.
                 bind()를 통해서 this를 고정할 수 있다.
               */
```

<br/>

ex) quiz 1번
```javascript
const quiz = {
  name: 'benz',
  getName: function() {
    console.log('getName', this);
    const innerFunc = function() {
      console.log('innerFunc', this);
    };
    innerFunc(); // 호출한 대상이 없기 때문에 최상위 객체인 windows객체가 표시 된다.
  },
}
quiz.getName(); // quiz객체 자체가 표시 된다.
```

ex) quiz 2번 위에서 innerFunc();의 값을 quiz.getName();값과 동일하게 표시하려면 어떻게 해야 하는가? 
```javascript
const quiz = {
  name: 'benz',
  getName: function() {
    console.log('getName', this);
    const innerFunc = () => {
      console.log('innerFunc', this);
    };
    innerFunc(); // '화살표 함수'를 사용하면 함수가 속해있는 최상위 함수의 this를 계승 받는다.
  },
}
quiz.getName(); // quiz객체 자체가 표시 된다.
```
