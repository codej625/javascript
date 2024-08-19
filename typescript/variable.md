# 타입스크립트의 변수 선언

<br /><br />

```
타입스크립트는 자바스크립트의 상위 집합으로,
정적 타입을 추가하여 코드의 안정성과 가독성을 높여준다.
```

<br /><br /><br />

1. 변수 선언(타입 명시)

```typescript
let name: string = "Alice";
const age: number = 30;

name = 10; // 에러
```

<br /><br />

2. 타입 추론

```typescript
let inferredNumber = 10; // inferredNumber는 자동으로 number 타입으로 추론된다.
```

<br /><br />

3. 타입별칭(Type Aliases)

```typescript
// 변수의 타입을 재사용하거나 복잡한 타입을 정의하기 위해 타입별칭을 사용할 수 있다.

type User = {
  name: string;
  age: number;
};

let user: User = {
  name: "Charlie",
  age: 25,
};
```

<br /><br />

4. 인터페이스(Interfaces)

```typescript
// 타입과 유사하지만, 확장 가능한 형태로 객체의 구조를 정의할 때 사용.

interface Person {
  name: string;
  age: number;
}

let person: Person = {
  name: "David",
  age: 40,
};
```

<br /><br />

5. 튜플(Tuple)

```typescript
// 고정된 크기의 배열을 정의할 때 사용하며, 각 요소의 타입을 명시할 수 있다.

let tuple: [string, number] = ["hello", 42];
```

<br /><br />

6. Optional 및 Default Parameters

```typescript
// 함수 매개변수에 타입을 지정할 수 있으며, 선택적(optional) 또는 기본값(default)을 설정할 수 있다.

function greet(name: string, age?: number): void {
  console.log(`Hello, ${name}.`);
  if (age !== undefined) {
    console.log(`You are ${age} years old.`);
  }
}
```
