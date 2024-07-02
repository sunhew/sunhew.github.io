---
layout: post
title: 리액트의 자바스크립트 확장 문법
date: 2024-06-29 09:12 +0900
description: REACT
image: ../assets/img/react15.jpg
category: react
tags: react자바스크립트확장문법 확장 문법 확장문법  react
published: true
sitemap: true
---

# REACT
해당 포스팅에서는 REACT의 자바스크립트 확장 문법에 대해 다룹니다.  <br />


## __이번 포스팅 목차__
* REACT의 자바스크립트 확장 문법 <br/>

## __리액트의 자바스크립트 확장 문법__<br/>
__자바스크립트 확장 문법__ 은 개발자가 더 간결하고 효율적인 코드를 작성할 수 있도록 돕는 문법적 개선 사항들입니다. 이러한 문법들은 ECMAScript(ES6 및 그 이후 버전)에서 도입되었으며, 다음과 같은 주요 기능들이 포함됩니다

### 1. __화살표 함수 (Arrow Functions)__
__화살표 함수__ 는 더 간결한 함수 선언을 가능하게 합니다. 또한, `this` 키워드의 바인딩이 기존 함수와 다릅니다.

#### __문법 예시__

```javascript
// 일반 함수 표현식
const add = function(a, b) {
  return a + b;
};

// 화살표 함수
const add = (a, b) => a + b;
```

### 2. __템플릿 리터럴 (Template Literals)__
__템플릿 리터럴__ 을 사용하면 문자열 내에서 변수와 표현식을 더 간편하게 삽입할 수 있습니다. 백틱을 사용하여 문자열을 감싸며, ${} 구문을 사용하여 변수를 포함할 수 있습니다.

#### __문법 예시__

```javascript
const name = 'John';
const greeting = `Hello, ${name}!`;
console.log(greeting); // "Hello, John!"
```

### 3. __디스트럭처링 할당 (Destructuring Assignment)__
__디스트럭처링 할당__ 은 배열이나 객체의 속성을 분해하여 개별 변수에 할당하는 문법입니다.

#### __문법 예시__

##### __배열 디스트럭처링__

```javascript
const [a, b] = [1, 2];
console.log(a); // 1
console.log(b); // 2
```

##### __객체 디스트럭처링__

```javascript
const person = { name: 'John', age: 30 };
const { name, age } = person;
console.log(name); // "John"
console.log(age); // 30
```

### 4. __디스트럭처링 할당 (Destructuring Assignment)__
함수 호출 시 인자가 전달되지 않았을 경우 __기본값__ 을 설정할 수 있습니다.

#### __문법 예시__

```javascript
function greet(name = 'Guest') {
  return `Hello, ${name}!`;
}
console.log(greet()); // "Hello, Guest!"
console.log(greet('Alice')); // "Hello, Alice!"
```

### 5. __나머지 매개변수와 스프레드 연산자 (Rest and Spread Operators)__
__나머지 매개변수__ 는 함수 매개변수 목록의 나머지 부분을 배열로 취급합니다. __스프레드 연산자__ 는 배열이나 객체를 개별 요소로 분해합니다.

#### __문법 예시__

##### __나머지 매개변수__

```javascript
function sum(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}
console.log(sum(1, 2, 3)); // 6
```

##### __스프레드 연산자__

```javascript
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5];
console.log(arr2); // [1, 2, 3, 4, 5]

const person = { name: 'John', age: 30 };
const updatedPerson = { ...person, age: 31 };
console.log(updatedPerson); // { name: 'John', age: 31 }
```

### 6. __클래스 (Classes)__
__클래스__ 는 객체 지향 프로그래밍의 중요한 개념으로, ES6에서 문법적 설탕(syntax sugar)으로 도입되었습니다. 기존 프로토타입 기반 상속을 더 명확하고 이해하기 쉽게 작성할 수 있습니다.

#### __문법 예시__

```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
  }
}

const john = new Person('John', 30);
john.greet(); // "Hello, my name is John and I am 30 years old."
```

### 7. __모듈 (Modules)__
__모듈__ 은 코드의 재사용성과 유지보수성을 높이기 위해 코드베이스를 분리하는 방법을 제공합니다. ES6부터는 `import`와 `export` 키워드를 사용하여 모듈을 정의하고 사용할 수 있습니다.

#### __문법 예시__

```javascript
// math.js
export function add(a, b) {
  return a + b;
}
export const pi = 3.14;

// main.js
import { add, pi } from './math.js';
console.log(add(2, 3)); // 5
console.log(pi); // 3.14
```

### 8. __비구조화 할당 (Destructuring Assignment)__
__비구조화 할당__ 은 배열이나 객체의 속성을 개별 변수로 추출하는 문법입니다. 배열과 객체에서 모두 사용될 수 있습니다.

#### __문법 예시__

```javascript
const person = { name: 'John', age: 30 };
const { name, age } = person;
console.log(name); // "John"
console.log(age); // 30

const numbers = [1, 2, 3];
const [first, second] = numbers;
console.log(first); // 1
console.log(second); // 2
```

### 9. __심볼 (Symbols)__
__심볼(Symbol)__ 은 고유하고 변경 불가능한 원시 타입 값으로, 객체의 프로퍼티 키로 사용됩니다.

#### __문법 예시__

```javascript
const sym = Symbol('description');
const obj = {
  [sym]: 'value'
};
console.log(obj[sym]); // "value"
```

### 10. __프라미스 (Promises)와 비동기 함수 (Async/Await)__
__프라미스(Promises)__ 는 비동기 작업을 처리하는 데 사용됩니다. __비동기 함수(Async/Await)__ 는 프라미스를 더욱 간단하게 사용할 수 있게 해줍니다.

#### __문법 예시__

##### __프라미스__

```javascript
const promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve('Done!'), 1000);
});
promise.then(result => console.log(result)); // "Done!" (1초 후)
```

##### __비동기 함수__

```javascript
async function fetchData() {
  const response = await fetch('https://api.example.com/data');
  const data = await response.json();
  console.log(data);
}
fetchData();
```

### __마무리__
자바스크립트의 __확장 문법__ 은 코드를 더욱 간결하고 효율적으로 작성할 수 있게 해줍니다. __화살표 함수, 템플릿 리터럴, 디스트럭처링 할당, 기본 매개변수, 나머지 매개변수와 스프레드 연산자, 클래스, 모듈, 심볼, 프라미스와 비동기 함수__ 등의 기능은 자바스크립트 개발자의 생산성을 높이고 코드의 가독성을 향상시키는 중요한 도구들입니다. 이러한 확장 문법을 숙지하고 활용함으로써, 더 나은 자바스크립트 코드를 작성할 수 있습니다.