---
layout: post
title: 불변성을 유지하려면 어떻게..
date: 2024-05-21 18:24 +0900
description: JAVASCRIPT
image: ../assets/img/html_css.png
category: JAVASCRIPT
tags: JAVASCRIPT html 불변성을유지 불변성 불변성유지방법
published: true
sitemap: true
---

# JAVASCRIPT
해당 포스팅에서는 불변성을 유지하려면 어떻게해야 하는지에 대해 다룹니다.<br />


## __JAVASCRIPT__
* 자바스크립트 장단점 <br/>
* 데이터 타입 <br/>
* 데이터 형 변환<br/>
* 불변성을 유지하려면 어떻게.. ✔️<br/>
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

## __불변성__<br/>

### __불변성의 설명__
자바스크립트에서 불변성(immutability)을 유지하는 것은 데이터 구조나 객체의 상태를 변경하지 않고, 변경이 필요할 때는 새로운 데이터 구조나 객체를 생성하는 것을 의미합니다. 불변성을 유지하는 것은 코드의 예측 가능성과 디버깅 용이성을 높이는 데 유리합니다. 아래는 자바스크립트에서 불변성을 유지하는 방법을 자세하게 설명한 내용입니다.

### __불변성의 종류__

#### __기본 타입의 불변성__
기본 타입(원시 타입)인 숫자, 문자열, 불리언, null, undefined, symbol은 본래 불변성(immutable)을 가집니다. 이러한 값들은 변경될 수 없고, 값이 변경되면 새로운 값을 할당하게 됩니다.

```javascript
let a = 10;
let b = a; // b는 a의 복사본을 가짐
a = 20;    // a를 변경해도 b는 영향을 받지 않음
console.log(a); // 20
console.log(b); // 10
```

#### __객체와 배열의 불변성 유지__
객체와 배열은 기본적으로 가변성(mutable)을 가집니다. 객체와 배열의 불변성을 유지하려면 여러 가지 방법을 사용할 수 있습니다.

##### __객체의 불변성 유지__

###### __`Object.assign()`__
새로운 객체를 생성하여 기존 객체의 프로퍼티를 복사합니다.

```javascript
const obj = {a: 1, b: 2};
const newObj = Object.assign({}, obj, {b: 3});
console.log(obj);    // {a: 1, b: 2}
console.log(newObj); // {a: 1, b: 3}
```

###### __스프레드 연산자__
ES6의 스프레드 연산자를 사용하여 객체를 복사하고, 변경된 프로퍼티를 추가합니다.

```javascript
const obj = {a: 1, b: 2};
const newObj = {...obj, b: 3};
console.log(obj);    // {a: 1, b: 2}
console.log(newObj); // {a: 1, b: 3}
```

#### __깊은 복사 (Deep Copy)__

##### __JSON을 사용한 깊은 복사__
간단한 중첩 객체의 경우 `JSON.parse` 와 `JSON.stringify` 를 사용하여 깊은 복사를 할 수 있습니다.

```javascript
const obj = {a: 1, b: {c: 2}};
const newObj = JSON.parse(JSON.stringify(obj));
newObj.b.c = 3;
console.log(obj.b.c);    // 2
console.log(newObj.b.c); // 3
```

###### __라이브러리 사용__
복잡한 객체의 깊은 복사를 위해 lodash 같은 라이브러리를 사용할 수 있습니다.

```javascript
const _ = require('lodash');

const obj = {a: 1, b: {c: 2}};
const newObj = _.cloneDeep(obj);
newObj.b.c = 3;
console.log(obj.b.c);    // 2
console.log(newObj.b.c); // 3
```


#### __불변 데이터 구조 라이브러리__
불변성을 유지하는 데이터 구조를 제공하는 라이브러리를 사용하는 것도 좋은 방법입니다. 대표적으로 Immutable.js와 immer가 있습니다.

##### __Immutable.js__
Immutable.js는 불변성을 유지하는 데이터 구조를 제공합니다.

```javascript
const { Map } = require('immutable');

let map1 = Map({a: 1, b: 2});
let map2 = map1.set('b', 3);

console.log(map1.get('b')); // 2
console.log(map2.get('b')); // 3
```

##### __immer__
immer는 불변성 관리를 쉽게 해주는 라이브러리입니다. `produce` 함수를 사용하여 불변성을 유지하면서 객체를 업데이트할 수 있습니다.

```javascript
const produce = require('immer').produce;

const state = {a: 1, b: {c: 2}};
const newState = produce(state, draft => {
    draft.b.c = 3;
});

console.log(state.b.c);    // 2
console.log(newState.b.c); // 3
```

#### __함수형 프로그래밍__
불변성을 유지하기 위해 함수형 프로그래밍 패러다임을 채택할 수 있습니다. 함수형 프로그래밍에서는 상태를 변경하지 않고 새로운 상태를 생성하는 것을 지향합니다.

```javascript
const increment = (num) => num + 1;

const state = {count: 0};
const newState = {...state, count: increment(state.count)};

console.log(state.count);    // 0
console.log(newState.count); // 1
```

자바스크립트에서 불변성을 유지하는 것은 데이터의 예측 가능성과 코드의 가독성을 높이는 데 매우 유용합니다. 기본 타입은 원래 불변성을 가지지만, 객체와 배열은 그렇지 않기 때문에 다양한 방법을 통해 불변성을 유지해야 합니다. 스프레드 연산자, `Object.assign()`, 배열 메서드, 깊은 복사, 불변 데이터 구조 라이브러리 등을 적절히 활용하여 불변성을 유지할 수 있습니다.