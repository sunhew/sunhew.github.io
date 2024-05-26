---
layout: post
title: Hoisting의 함수 호이스팅
date: 2024-05-26 22:02 +0900
description: JAVASCRIPT
image: ../assets/img/javascript.png
category: JAVASCRIPT
tags: JAVASCRIPT Hoisting 호이스팅 변수 var let const 함수 함수호이스팅 클래스호이스팅
published: true
sitemap: true
---

# JAVASCRIPT
해당 포스팅에서는 호이스팅(Hoisting)의 함수 호이스팅에 대해 다룹니다.<br />


## __JAVASCRIPT__
* 자바스크립트 장단점 <br/>
* 데이터 타입 <br/>
* 데이터 형 변환<br/>
* 불변성을 유지하려면 어떻게..<br/>
* 프로토타입 <br/>
* var, let, const 차이 <br/>
* 호이스팅(Hoisting) ✔️<br/>
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

## __호이스팅(Hoisting)__<br/>
해당 포스팅에서는 호이스팅(Hoisting)의 변수중 __함수 호이스팅__ 에 대해 다룹니다.

### __함수 호이스팅의 개념__
호이스팅(Hoisting)은 __JAVASCRIPT 에서 함수 선언이 해당 범위의 최상단으로 끌어올려지는 동작__ 을 의미합니다. 함수 호이스팅 덕분에 함수 선언문은 코드 작성 순서와 상관없이 호출될 수 있습니다. 그러나 함수 표현식에서는 호이스팅이 다르게 작동합니다.

### __함수 선언문과 함수 표현식의 차이__

#### __함수 선언문(Function Declaration)__
함수 선언문은 __함수 전체가 호이스팅되며,__ 이로 인해 함수 선언 위치보다 앞서 함수 호출이 가능합니다.

##### __예시 코드__

```javascript
console.log(square(5));  // 25

function square(n) {
    return n * n;
}
```

위 코드에서 함수 `square`는 선언되기 전에 호출되었지만, 정상적으로 동작하는 이유는 함수 선언문이 호이스팅되어 아래의 코드처럼 처리되기 떄문입니다.

```javascript
function square(n) {
    return n * n;
}

console.log(square(5));  // 25
```

#### __함수 표현식(Function Experssion)__
함수 표현식은 __변수 선언만 호이스팅되며, 변수에 할당된 함수는 호이스팅되지 않습니다.__ 따라서 함수 표현식으로 선언된 함수는 선언 전에 호출 할 수 없습니다.

##### __예시 코드__

```javascript
// console.log(add(5, 10));  // TypeError: add is not a function
var add = function(a, b) {
    return a + b;
};
console.log(add(5, 10));  // 15
```

위 코드에서 `ver add`선언만 호이스팅 되므로, 초기화 전에는 `add`가 `undefined`로 처리됩니다. 아래의 코드는 호이스팅에 의해 처리된 코드입니다.

```javascript
var add;
// console.log(add(5, 10));  // TypeError: add is not a function
add = function(a, b) {
    return a + b;
};
console.log(add(5, 10));  // 15
```

#### __호이스팅과 함수 선언의 예시__

##### __1. 함수 선언문__

```javascript
console.log(greet('World'));  // Hello, World!

function greet(name) {
    return `Hello, ${name}!`;
}
```

아래의 코드는 호이스팅에 의해 처리된 코드입니다.

```javascript
function greet(name) {
    return `Hello, ${name}!`;
}

console.log(greet('World'));  // Hello, World!
```

##### __2. 함수 표현식__

```javascript
// console.log(multiply(2, 3));  // TypeError: multiply is not a function
var multiply = function(a, b) {
    return a * b;
};
console.log(multiply(2, 3));  // 6
```

아래의 코드는 호이스팅에 의해 처리된 코드입니다.

```javascript
var multiply;
// console.log(multiply(2, 3));  // TypeError: multiply is not a function
multiply = function(a, b) {
    return a * b;
};
console.log(multiply(2, 3));  // 6
```

### __호이스팅과 변수 선언과의 관계__
함수 표현식에서 `let`과 `const`를 사용하는 경우에도, 변수 호이스팅과 TDZ 규칙이 적용됩니다.

##### __let과 const와 함께 사용하는 함수 표현식__

```javascript
// console.log(divide(10, 2));  // ReferenceError: Cannot access 'divide' before initialization
let divide = function(a, b) {
    return a / b;
};
console.log(divide(10, 2));  // 5
```

아래의 코드는 호이스팅에 의해 처리된 코드입니다.

```javascript
let divide;
// console.log(divide(10, 2));  // ReferenceError: Cannot access 'divide' before initialization
divide = function(a, b) {
    return a / b;
};
console.log(divide(10, 2));  // 5
```

### __IIFE (Immediately Invoked Function Expression)와 호이스팅__
즉시 실행 함수 표현식(IIFE)은 함수가 정의되자마자 즉시 실행됩니다. IIFE는 호이스팅과는 무관하게, 함수의 독립적인 실행 환경을 만들기 위해 사용됩니다.

##### __let과 const와 함께 사용하는 함수 표현식__

```javascript
(function() {
    console.log('This is an IIFE!');
})();
```

위 코드에서는 IIFE가 즉시 실행되어 `This is an IIFE!`가 출력됩니다.

### __마무리__
함수 호이스팅은 JAVASCRIPT에서 중요한 개념으로, __함수 선언문이 코드의 최상단으로 끌어올려져 선언 위치와 상관없이 호출될 수 있게 합니다.__ 그러나 __함수 표현식은 변수 선언만 호이스팅되며, 함수 할당은 호이스팅되지 않으므로__ 선언 전에 호출할 수 없습니다. 이를 이해하고 활용한다면 __더 예측 가능하고 안정적인 코드를 작성할 수 있습니다.__