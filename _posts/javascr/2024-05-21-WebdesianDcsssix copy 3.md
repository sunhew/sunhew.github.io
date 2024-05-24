---
layout: post
title: 데이터 타입
date: 2024-05-20 19:24 +0900
description: JAVASCRIPT
image: ../assets/img/html_css.png
category: JAVASCRIPT
tags: JAVASCRIPT 데이터타입 데이터
published: true
sitemap: true
---

# JAVASCRIPT
해당 포스팅에서는 데이터 타입에 대해 다룹니다. 꽤 많이 길기에 오른쪽에 있는 목차를 활용해 주세요.<br />


## __JAVASCRIPT__
* 자바스크립트 장단점 <br/>
* 데이터 타입 ✔️<br/>
* 데이터 형 변환<br/>
* 불변성을 유지하려면 어떻게..<br/>
* 프로토타입 <br/>
* var, let, const 차이<br/>
* 호이스팅(Hoisting)<br/>
* es6 문법 특징과 차이<br/>
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

## __데이터 타입__<br/>

### __데이터 타입의 설명__
자바스크립트는 동적이고 약한 타입의 언어로, 변수의 타입을 명시하지 않고도 사용할 수 있습니다. 자바스크립트의 데이터 타입은 크게 기본 타입(원시 타입)과 객체 타입으로 나뉩니다. 아래는 각 데이터 타입에 대한 자세한 설명입니다.

### __기본 타입 (Primitive Types)__
기본 타입은 단일 값만을 가지며, 변경 불가능(immutable)합니다.

#### __숫자 (Number)__
숫자 타입은 정수와 실수를 포함합니다. 자바스크립트에서는 모든 숫자가 64비트 부동소수점 형식 (IEEE 754)으로 저장됩니다.

```javascript
let integer = 42;         // 정수
let float = 3.14;         // 실수
let negative = -7;        // 음수
let exponential = 1.23e4; // 지수 표기법
let notANumber = NaN;     // 숫자가 아님(Not-a-Number)
let infinity = Infinity;  // 무한대
let negativeInfinity = -Infinity; // 음의 무한대
```

#### __문자열 (String)__
문자열 타입은 텍스트 데이터를 표현합니다. 문자열은 작은따옴표(''), 큰따옴표(""), 또는 백틱(``)으로 감쌀 수 있습니다.

```javascript
let singleQuote = 'Hello, world!';
let doubleQuote = "Hello, world!";
let templateLiteral = `Hello, ${name}!`; // 템플릿 리터럴
```

#### __불리언 (Boolean)__
불리언 타입은 논리 값을 나타내며, true와 false 두 가지 값만 가질 수 있습니다.

```javascript
let isTrue = true;
let isFalse = false;
```

#### __null__
`null` 은 의도적으로 값이 없음을 나타내는 타입입니다.

```javascript
let emptyValue = null;
```

#### __undefined__
`undefined` 는 값이 할당되지 않은 변수를 나타냅니다. 변수를 선언하고 초기화하지 않으면 기본적으로 `undefined` 값을 가집니다.

```javascript
let notAssigned;
console.log(notAssigned); // undefined
```

#### __심볼 (Symbol)__
ES6에서 도입된 심볼 타입은 유일무이한 식별자를 생성하는 데 사용됩니다. 주로 객체의 프로퍼티 키로 사용됩니다.

```javascript
let symbol1 = Symbol();
let symbol2 = Symbol('description');
```

### __객체 타입 (Object Types)__
객체 타입은 여러 값을 포함할 수 있는 복합 자료형입니다. 객체는 키-값 쌍의 집합입니다.

#### __객체 (Object)__
객체는 키-값 쌍을 포함하는 컨테이너입니다. 키는 문자열이나 심볼이고, 값은 어떤 타입도 가능합니다

```javascript
let person = {
    name: 'John',
    age: 30,
    greet: function() {
        console.log('Hello!');
    }
};

console.log(person.name); // 'John'
person.greet();           // 'Hello!'
```

#### __배열 (Array)__
배열은 순서가 있는 값의 리스트입니다. 배열의 요소는 어떤 타입도 될 수 있습니다.

```javascript
let numbers = [1, 2, 3, 4, 5];
let mixedArray = [1, 'two', true, null, undefined, {key: 'value'}, [1, 2, 3]];

console.log(numbers[0]); // 1
console.log(mixedArray[5]); // {key: 'value'}
```

#### __함수 (Function)__
함수는 특정 작업을 수행하는 코드 블록입니다. 함수도 객체의 일종입니다.

```javascript
function greet(name) {
    return `Hello, ${name}!`;
}

let add = function(a, b) {
    return a + b;
};

console.log(greet('Alice')); // 'Hello, Alice!'
console.log(add(2, 3));      // 5
```

#### __날짜 (Date)__
`Date` 객체는 날짜와 시간을 나타냅니다.

```javascript
let now = new Date();
console.log(now); // 현재 날짜와 시간
```

#### __정규 표현식 (RegExp)__
`RegExp` 객체는 정규 표현식을 나타내며, 문자열 패턴 매칭에 사용됩니다.

```javascript
let pattern = /hello/;
let text = 'Hello, world!';

console.log(pattern.test(text)); // false (대소문자 구분)
console.log(/hello/i.test(text)); // true (대소문자 무시)
```

#### __맵 (Map)과 셋 (Set)__
`Map` 은 키-값 쌍의 집합을 나타내며, `Set` 은 중복되지 않는 값의 집합을 나타냅니다. 이들은 ES6에서 도입되었습니다.

```javascript
let map = new Map();
map.set('key1', 'value1');
map.set('key2', 'value2');

console.log(map.get('key1')); // 'value1'

let set = new Set();
set.add(1);
set.add(2);
set.add(1); // 중복된 값은 추가되지 않음

console.log(set.has(1)); // true
console.log(set.size);   // 2
```

#### __약한 맵 (WeakMap)과 약한 셋 (WeakSet)__
`WeakMap` 과 `WeakSet` 은 가비지 컬렉션을 지원하는 자료 구조로, 키로 사용된 객체가 더 이상 참조되지 않을 때 자동으로 제거됩니다.

```javascript
let weakMap = new WeakMap();
let obj = {};
weakMap.set(obj, 'value');

console.log(weakMap.get(obj)); // 'value'

let weakSet = new WeakSet();
let obj2 = {};
weakSet.add(obj2);

console.log(weakSet.has(obj2)); // true
```

### __타입 확인__
자바스크립트에서 데이터 타입을 확인하는 방법에는 여러 가지가 있습니다.

#### __typeof 연산자__
원시 타입과 객체 타입을 구분하는 데 사용됩니다.

```javascript
console.log(typeof 123);         // 'number'
console.log(typeof 'hello');     // 'string'
console.log(typeof true);        // 'boolean'
console.log(typeof undefined);   // 'undefined'
console.log(typeof null);        // 'object' (자바스크립트의 오래된 버그)
console.log(typeof Symbol());    // 'symbol'
console.log(typeof {});          // 'object'
console.log(typeof []);          // 'object'
console.log(typeof function(){}); // 'function'
```

#### __instanceof 연산자__
객체가 특정 생성자 함수의 인스턴스인지 확인하는 데 사용됩니다.

```javascript
console.log([] instanceof Array);    // true
console.log({} instanceof Object);   // true
console.log(function(){} instanceof Function); // true
```

#### __Array.isArray() 메서드__
값이 배열인지 확인하는 데 사용됩니다.

```javascript
console.log(Array.isArray([])); // true
console.log(Array.isArray({})); // false
```