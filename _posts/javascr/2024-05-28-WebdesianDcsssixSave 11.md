---
layout: post
title: es6 문법 특징과 차이
date: 2024-05-28 09:29 +0900
description: JAVASCRIPT
image: ../assets/img/javascript.png
category: JAVASCRIPT
tags: JAVASCRIPT es6 문법 특징과차이 es6문법특징과차이
published: true
sitemap: true
---

# JAVASCRIPT
해당 포스팅에서는 es6 문법 특징과 차이에 대해 다룹니다.<br />


## __JAVASCRIPT__
* 자바스크립트 장단점 <br/>
* 데이터 타입 <br/>
* 데이터 형 변환<br/>
* 불변성을 유지하려면 어떻게..<br/>
* 프로토타입 <br/>
* var, let, const 차이 <br/>
* 호이스팅(Hoisting) <br/>
* es6 문법 특징과 차이 ✔️<br/>
* this<br/>
* 제이쿼리 메서드 중 attr(), prop() 차이<br/>
* 화살표 함수와 일반 함수 차이<br/>
* 스코프(scope)<br/>
* 객체 지향<br/>
* 클로저(closure)<br/>
* 타입스크립트<br/>
* 프로세스<br/>
* 스레드, 싱글 스레드<br/>
* 콜백 함수 / 재귀 함수 차이<br/>
* 콜백 지옥, 콜백 지옥을 해결하는 방법<br/>
* promise / 콜백 지옥<br/>
* ajax<br/>
* 함수 선언식/ 표현식 차이<br/>
* 이벤트 버블링 / 이벤트 캡처 예시<br/>
* 이벤트 위임 (Event Delegation)<br/>
* 렉시컬 환경<br/>
* 프로퍼티<br/>
* stack이 코드 실행할 때 queue에 미뤄두는 것<br/>
* 얕은 복사 / 깊은 복사<br/>
* 동기 / 비동기<br/>

## __es6 문법 특징과 차이__<br/>
해당 포스팅에서는 호이스팅(Hoisting)의 __es6 문법 특징과 차이__ 에 대해 다룹니다.

### __변수 선언: let과 const__

#### __let__
`let`은 블록 스코프를 가지며, 변수 재할당이 가능합니다. 이는 `var`와 달리 변수의 범위를 블록 단위로 제한하여 변수 충돌을 방지합니다.

```javascript
let a = 10;
if (true) {
    let a = 20;
    console.log(a); // 20
}
console.log(a); // 10
```

#### __const__
`const`는 상수 선언을 위한 키워드로, 블록 스코프를 가지며, 선언과 동시에 초기화되어야 하고, 재할당이 불가능합니다. 그러나 객체나 배열의 속성 변경은 가능합니다.

```javascript
const b = 30;
// b = 40; // TypeError: Assignment to constant variable.

const obj = { name: "Alice" };
obj.name = "Bob"; // 가능
```

### __화살표 함수 (Arrow Functions)__
화살표 함수는 간결한 문법으로 함수를 정의할 수 있으며, `this`바인딩을 렉시컬(lexical)하게 처리합니다. 이는 기존의 `function` 키워드와 달리 `this`를 호출 위치가 아닌 선언 위치에서 결정합니다.

```javascript
const add = (x, y) => x + y;
console.log(add(2, 3)); // 5

const obj = {
    name: "Alice",
    sayName: function() {
        setTimeout(() => {
            console.log(this.name);
        }, 1000);
    }
};
obj.sayName(); // Alice
```

### __템플릿 리터럴 (Template Literals)__
템플릿 리터럴은 문자열을 편리하게 작성할 수 있는 문법입니다. 백틱을 사용하며, __`${}`__ 구문을 통해 변수를 삽입할 수 있습니다.

```javascript
const name = "Alice";
const greeting = `Hello, ${name}!`;
console.log(greeting); // Hello, Alice!

const multiLine = `This is
a multi-line
string.`;
console.log(multiLine);
```

### __디스트럭처링 할당 (Destructuring Assignment)__
디스트럭처링은 배열이나 객체의 값을 분해하여 개별 변수에 할당할 수 있게 합니다.

#### __배열 디스트럭처링__

```javascript
const [a, b] = [1, 2];
console.log(a); // 1
console.log(b); // 2
```

#### __객체 디스트럭처링__

```javascript
const {name, age} = {name: "Alice", age: 25};
console.log(name); // Alice
console.log(age); // 25
```

### __모듈 (Modules)__
ES6 모듈을 사용하면 파일 간에 코드를 분할하고 재사용할 수 있습니다. `export`와 `import` 키워드를 사용하여 모듈을 정의하고 불러옵니다.

#### __모듈 내보내기__

```javascript
// math.js
export const add = (x, y) => x + y;
export const multiply = (x, y) => x * y;
```

#### __모듈 가져오기__

```javascript
// main.js
import { add, multiply } from './math.js';
console.log(add(2, 3)); // 5
console.log(multiply(2, 3)); // 6
```

### __클래스 (Classes)__
ES6 클래스 문법은 자바스크립트에서 객체 지향 프로그래밍을 쉽게 구현 할 수 있게 합니다. 기존의 프로토타입 기반 상속을 간단한 문법으로 작성할 수 있습니다.

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

const alice = new Person("Alice", 25);
alice.greet(); // Hello, my name is Alice and I am 25 years old.
```

### __프로미스 (Promises)__
프로미스는 비동기 작업을 처리하기 위한 새로운 방법을 제공합니다. `then`, `catch`메서드를 사용하여 비동기 작업의 성공과 실패를 처리합니다.

```javascript
const fetchData = () => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve("Data received");
        }, 1000);
    });
};

fetchData()
    .then(data => {
        console.log(data); // Data received
    })
    .catch(error => {
        console.error(error);
    });
```

### __맵과 셋 (Map and Set)__
`Map`은 키-값 쌍을 저장하고, `Set`은 중복되지 않는 값을 저장합니다. 둘 다 iterable이며, 각기 다양한 유용한 메서드를 제공합니다

#### __Map__

```javascript
const map = new Map();
map.set('name', 'Alice');
map.set('age', 25);
console.log(map.get('name')); // Alice
console.log(map.size); // 2
```

#### __Set__

```javascript
const set = new Set([1, 2, 3, 3, 4]);
console.log(set.size); // 4
set.add(5);
console.log(set.has(5)); // true
```

### __디폴트 파라미터 (Default Parameters)__
함수의 매개변수에 기본값을 설정할 수 있습니다

```javascript
function greet(name = "Guest") {
    console.log(`Hello, ${name}!`);
}
greet(); // Hello, Guest!
greet("Alice"); // Hello, Alice!
```

### __나머지 파라미터와 스프레드 연산자 (Rest and Spread Operator)__

#### __나머지 파라미터__
나머지 파라미터를 사용하면 함수의 매개변수 목록을 배열로 받을 수 있습니다.

```javascript
function sum(...numbers) {
    return numbers.reduce((acc, cur) => acc + cur, 0);
}
console.log(sum(1, 2, 3, 4)); // 10
```

#### __스프레드 연산자__
스프레드 연산자를 사용하면 배열이나 객체를 펼칠 수 있습니다.

```javascript
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5, 6];
console.log(arr2); // [1, 2, 3, 4, 5, 6]

const obj1 = {a: 1, b: 2};
const obj2 = {...obj1, c: 3};
console.log(obj2); // {a: 1, b: 2, c: 3}
```