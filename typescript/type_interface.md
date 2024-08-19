# 타입과 인터페이스에 대해

<br /><br />

```
typescript에서 type와 interface는 비슷한 역할을 한다.
어떤 경우에는 type를 사용하는 게 좋고 어떤 경우에는 interface를 사용하는 게 좋은지 알아보자.
```

<br /><br /><br />

1. 확장(상속)

```typescript
// interface
// extends 키워드를 이용해서 확장할 수 있다.

interface Person {
  name: string;
  age: number;
}

interface Student extends Person { // 확장(상속)
  school: string;
}

const codej625: Student = {
  name: 'codej625',
  age: 34,
  school: '부천동중학교(박효신 중학교)'
}
```

<br />

```typescript
// type
// & 기호를 이용해서 확장할 수 있다.

type Person = {
  name: string,
  age: number
}

type Student = Person & { // 확장(상속)
  school: string
}

const codej625: Student = {
  name: 'codej625',
  age: 34,
  school: '부천동중학교(박효신 중학교)'
}
```

<br /><br />

2. 선언적 확장

```typescript
// interface
// 선언적 확장(Declaration Merging)이 가능하다.
// 같은 이름의 interface를 선언하면, 자동으로 확장

interface Person {
  name: string;
  age: number;
}

interface Person { // 선언적 확장
  gender: string;
}

const codej625: Person = {
  name: 'codej625',
  age: 34,
  gender: 'male'
}
```

<br />

```typescript
// type
// 선언적 확장이 불가능

type Person = {
  name: string;
  age: number;
}

type Person = { // Error
  gender: string;
}

// 따라서 타입 객체의 확장성을 위해서는 interface를 사용하는 것이 더 좋다.
```

<br /><br />

3. 자료형(type)

```typescript
// interface
// 객체(Object)의 타입을 설정할 때 사용할 수 있으며, 원시 자료형에는 사용할 수 없다.

interface Person {
  name: string;
  age: number;
  gender: string;
}

interface name extends string { // Error
  ...
}
```

<br />

```typescript
// type
// 객체 타입을 정의할 때도 사용할 수 있지만, 객체 타입을 정의할 때는 interface를 사용하는게 좋다.
// 단순한 원시값(Primitive Type)이나 튜플(Tuple), 유니언(Union) 타입을 선언할 때 type을 사용하는 것이 좋다.

type Name = string; // primitive
type Age = number;
type Person = [string, number, boolean]; // tuple
type NumberString = string | number; // union

type Person = { // 객체는 interface를 사용하도록 하자.
  name: string,
  age: number,
  gender: string
}

interface Person = { // interface
  name: string,
  age: number,
  gender: string
}
```

<br /><br />

4. computed value

```typescript
// interface
// computed value 사용이 불가능

type Subjects = 'math' | 'science' | 'sociology';

interface Grades {
  [key in Subjects]: string; // Error
}
```

<br />

```typescript
// type

type Subjects = 'Math' | 'Science' | 'Sociology';

type Grades = {
  [key in Subjects]: string;
}
```
