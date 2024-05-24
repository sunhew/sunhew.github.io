---
layout: post
title: var, let, const 차이
date: 2024-05-23 09:53 +0900
description: JAVASCRIPT
image: ../assets/img/html_css.png
category: JAVASCRIPT
tags: JAVASCRIPT html var let const 차이
published: true
sitemap: true
---

# JAVASCRIPT
해당 포스팅에서는 block, inline-block, inline 차이에 대해 다룹니다. 꽤 많이 길기에 오른쪽에 있는 목차를 활용해 주세요.<br />


## __JAVASCRIPT__
* 자바스크립트 장단점 <br/>
* 데이터 타입 <br/>
* 데이터 형 변환<br/>
* 불변성을 유지하려면 어떻게..<br/>
* 프로토타입 <br/>
* var, let, const 차이 ✔️<br/>
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

## __변수 선언 방식__<br/>

### __변수 선언 방식의 기본 개념__

* __var__

    `var` 는 ES6 이전에 자바스크립트에서 변수를 선언하는 유일한 방법이었습니다. 함수 스코프(function scope)를 가지며, 함수 내부에서 선언된 변수는 함수 전체에서 접근할 수 있습니다. 또한, 호이스팅(hoisting)이라는 특징이 있어, 선언 부분이 코드의 최상단으로 끌어올려진 것처럼 동작합니다.

* __let__

    `let` 은 ES6에서 도입된 변수 선언 방식으로, 블록 스코프(block scope)를 가집니다. 이는 변수가 선언된 블록 내에서만 유효하며, 호이스팅은 되지만 초기화는 선언된 위치에서 이루어집니다.

* __const__

    `const` 또한 ES6에서 도입된 변수 선언 방식으로, `let` 과 동일하게 블록 스코프를 가집니다. `const` 로 선언된 변수는 상수로 취급되며, 선언과 동시에 초기화되어야 하며 이후에 값을 변경할 수 없습니다. 하지만 객체나 배열과 같은 참조 타입의 경우, 참조 자체는 불변이지만 내부 값은 변경할 수 있습니다.


### __변수 선언 방식의 사용 예시__

* __var의 사용 예시__

    `var` 로 변수를 선언하면 함수 스코프를 가지며, 호이스팅이 발생합니다. 이는 아래 예제에서 `var` 로 선언된 `i` 가 for문 바깥에서도 접근 가능하며, 선언 전에 호출해도 `undefined` 로 평가되는 것을 확인할 수 있습니다.

```javascript
console.log(x); // undefined
var x = 5;

function example() {
    var y = 10;
    if (true) {
        var z = 20;
    }
    console.log(z); // 20 (함수 스코프)
}
example();
console.log(y); // ReferenceError: y is not defined
```

* __let의 사용 예시__

    `let` 로 변수를 선언하면 블록 스코프를 가지며, 호이스팅은 되지만 초기화는 선언된 위치에서 이루어집니다. 이는 아래 예제에서 `let` 로 선언된 `i` 가 for문 바깥에서는 접근할 수 없고, 선언 전에 호출하면 ReferenceError가 발생하는 것을 확인할 수 있습니다.

```javascript
console.log(a); // ReferenceError: a is not defined
let a = 5;

function example() {
    let b = 10;
    if (true) {
        let c = 20;
    }
    console.log(c); // ReferenceError: c is not defined
}
example();
console.log(b); // ReferenceError: b is not defined
```

* __const의 사용 예시__

    `const` 로 변수를 선언하면 블록 스코프를 가지며, 선언과 동시에 초기화되어야 하고 이후에 값을 변경할 수 없습니다. 이는 아래 예제에서 `const` 로 선언된 `d` 가 재할당 시 오류를 발생시키는 것을 확인할 수 있습니다.

```javascript
const d = 5;
d = 10; // TypeError: Assignment to constant variable.

const obj = { name: 'John' };
obj.name = 'Doe'; // 가능 (객체 내부 값은 변경 가능)
console.log(obj.name); // Doe

const arr = [1, 2, 3];
arr.push(4); // 가능 (배열 내부 값은 변경 가능)
console.log(arr); // [1, 2, 3, 4]
```

### __변수 선언 방식의 특징 및 차이점__

* 스코프

    `var` 는 함수 스코프를 가지며, `let` 과 `const` 는 블록 스코프를 가집니다. 이는 변수가 어디서 접근 가능한지를 결정짓는 중요한 특징입니다.

* 호이스팅

    `var` 는 호이스팅되어 변수 선언이 코드의 최상단으로 끌어올려진 것처럼 동작합니다. `let` 과 `const` 도 호이스팅되지만, 초기화는 변수 선언 위치에서 이루어집니다. 따라서 선언 전에 변수를 사용하려고 하면 ReferenceError가 발생합니다.

* 재할당 가능 여부

    `var` 와 `let` 은 재할당이 가능하지만, `const` 는 재할당이 불가능합니다. `const` 로 선언된 변수는 상수로 취급되며, 선언과 동시에 초기화되어야 합니다. 하지만 객체나 배열과 같은 참조 타입의 경우, 내부 값은 변경할 수 있습니다.


자바스크립트의 변수 선언 방식에 대한 이해는 코드의 가독성과 유지보수성을 높이는 데 매우 중요합니다.