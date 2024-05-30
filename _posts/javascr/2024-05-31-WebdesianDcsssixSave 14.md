---
layout: post
title: 화살표 함수와 일반 함수 차이
date: 2024-05-31 19:27 +0900
description: JAVASCRIPT
image: ../assets/img/javascript.png
category: JAVASCRIPT
tags: JAVASCRIPT 화살표함수 일반함수 차이 화살표_함수와_일반_함수_차이
published: true
sitemap: true
---

# JAVASCRIPT
해당 포스팅에서는 자바스크립트의 __화살표 함수와 일반 함수 차이__ 에 대해 다룹니다.<br />


## __JAVASCRIPT__
* 자바스크립트 장단점 <br/>
* 데이터 타입 <br/>
* 데이터 형 변환<br/>
* 불변성을 유지하려면 어떻게..<br/>
* 프로토타입 <br/>
* var, let, const 차이 <br/>
* 호이스팅(Hoisting) <br/>
* es6 문법 특징과 차이<br/>
* this<br/>
* 제이쿼리 메서드 중 attr(), prop() 차이<br/>
* 화살표 함수와 일반 함수 차이 ✔️<br/>
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

## __화살표 함수와 일반 함수 차이__<br/>
해당 포스팅에서는 __화살표 함수와 일반 함수 차이__ 에 대해 다룹니다.

### __함수의 기본 개념__

#### __화살표 함수 (Arrow Function)__
화살표 함수는 __ES6에서 도입된 새로운 함수 선언 방식__ 입니다. 함수 표현식의 간결한 문법으로, 특히 __익명 함수 및 콜백 함수로 자주 사용__ 됩니다. 화살표 함수는 __`function` 키워드를 사용하지 않고, 화살표(`=>`)를 사용하여 정의__ 합니다.

#### __일반 함수 (Regular Function)__
일반 함수는 __기존의 함수 선언 방식__ 으로, __`function` 키워드를 사용하여 정의__ 됩니다. 전통적으로 사용되며, __다양한 함수 선언 방식이 존재__ 합니다.

### __함수의 문법 차이__

#### __화살표 함수 (Arrow Function)__

```javascript
const add = (a, b) => {
    return a + b;
};

// 더 간결하게
const add = (a, b) => a + b;
```

#### __일반 함수__

```javascript
function add(a, b) {
    return a + b;
}

// 함수 표현식으로 선언할 때
const add = function(a, b) {
    return a + b;
};
```

### __this 바인딩 차이__

#### __화살표 함수__
화살표 함수는 자신만의 `this` 바인딩을 가지지 않습니다. 대신, 화살표 함수 내부의 `this`는 __자신이 정의된 환경(상위 스코프)의 `this`를 상속__ 받습니다.
아래 예제에서,  __`regularFunction`은 호출된 객체 `obj를` `this`로 참조__ 합니다. 반면, __`arrowFunction`은 자신이 정의된 환경인 전역 스코프의 `this`를 참조하여 undefined를 출력__ 합니다.

```javascript
const obj = {
    value: 42,
    regularFunction: function() {
        console.log(this.value); // 42
    },
    arrowFunction: () => {
        console.log(this.value); // undefined
    }
};

obj.regularFunction(); // 42
obj.arrowFunction();   // undefined
```

#### __일반 함수__
일반 함수는 __호출 방식에 따라 `this` 바인딩이 동적으로 결정__ 됩니다. 즉, 함수가 어떻게 호출되었느냐에 따라 `this`가 달라집니다.아래 예제에서, __`obj.regularFunction`은 `obj`의 컨텍스트에서 호출되므로 `this`는 `obj`를 참조__ 합니다. 하지만 __`func`로 할당된 후에는 전역 컨텍스트에서 호출되므로 `this`는 전역 객체(`window` 또는 `global`)를 참조__ 하게 됩니다.

```javascript
const obj = {
    value: 42,
    regularFunction: function() {
        console.log(this.value);
    }
};

obj.regularFunction(); // 42

const func = obj.regularFunction;
func(); // undefined
```

### __arguments 객체__

#### __화살표 함수__
화살표 함수는 __`arguments` 객체를 자체적으로 가질 수 없습니다.__ 대신, __상위 스코프의 `arguments` 객체를 참조__ 합니다.

```javascript
const arrowFunction = () => {
    console.log(arguments); // ReferenceError
};

function regularFunction() {
    const arrowFunctionInside = () => {
        console.log(arguments); // regularFunction의 arguments
    };
    arrowFunctionInside(1, 2, 3);
}

regularFunction(1, 2, 3);
```

#### __일반 함수__
일반 함수는 __호출된 함수의 인자를 담고 있는 `arguments` 객체를 가집니다.__

```javascript
function regularFunction() {
    console.log(arguments); // [Arguments] { '0': 1, '1': 2, '2': 3 }
}

regularFunction(1, 2, 3);
```

### __생성자 함수로 사용 가능 여부__

#### __화살표 함수__
화살표 함수는 __`new` 키워드를 사용한 생성자 함수로 사용할 수 없습니다.__ 생성자 함수는 __`this`를 인스턴스 객체에 바인딩 하지만, 화살표 함수는 자신만의 `this` 바인딩을 가지지 않기 때문입니다.__ 

```javascript
const Person = (name) => {
    this.name = name;
};

const person = new Person('Alice'); // TypeError: Person is not a constructor
```

#### __일반 함수__
일반 함수는 __`new` 키워드를 사용하여 생성자 함수로 사용할 수 있습니다.__ 생성자 __함수로 호출될 때, `this`는 새로 생성된 인스턴스를 참조__ 합니다.

```javascript
function Person(name) {
    this.name = name;
}

const person = new Person('Alice');
console.log(person.name); // Alice
```

### __마무리__
화살표 함수와 일반 함수는 __`this`바인딩, `arguments`객체, 생성자 함수로의 사용 여부 등에서 중요한 차이점__ 이 있습니다. __화살표 함수는 더 간결한 문법을 제공하고 상위 스코프의 `this`를 사용하기 때문에 콜백 함수나 메서드 내부 함수로 자주 사용__ 됩니다. 반면, __일반 함수는 더 유연한 `this` 바인딩과 `arguments`객체를 가지고 있어 다양한 상황에서 사용__ 될 수 있습니다. 화살표 함수와 일반 함수의 차이점을 이해하고 적절히 사용하는 것은 자바스크립트 코드를 더 효과적이고 오류 없이 작성하는 데 매우 중요합니다.