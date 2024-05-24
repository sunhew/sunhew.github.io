---
layout: post
title: 데이터 형 변환
date: 2024-05-19 19:24 +0900
description: JAVASCRIPT
image: ../assets/img/javascript.png
category: JAVASCRIPT
tags: html&css html css 데이터형변환 데이터
published: true
sitemap: true
---

# JAVASCRIPT
해당 포스팅에서는 데이터 형 변환에 대해 다룹니다.<br />


## __JAVASCRIPT__
* 자바스크립트 장단점 <br/>
* 데이터 타입 <br/>
* 데이터 형 변환 ✔️<br/>
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

## __데이터 형 변환__<br/>

### __데이터 형 변환의 개념__
자바스크립트에서 데이터 형 변환은 값의 타입을 다른 타입으로 변환하는 과정을 말합니다. 자바스크립트는 동적 타입 언어이기 때문에 데이터 형 변환이 자주 발생합니다. 형 변환은 매우 유연하지만, 예기치 않은 결과를 초래할 수 있습니다. 명시적 형 변환을 사용하면 코드의 의도를 명확히 할 수 있으며, 예기치 않은 오류를 방지하는 데 도움이 됩니다. 암시적 형 변환이 발생할 수 있는 상황을 이해하고, 필요한 경우 명시적으로 형 변환을 수행하는 것이 좋습니다. 데이터 형 변환은 크게 명시적 형 변환과 암시적 형 변환으로 나눌 수 있습니다.

### __명시적 형 변환 (Explicit Type Conversion)__
명시적 형 변환은 프로그래머가 의도적으로 데이터 타입을 변환하는 것을 의미합니다. 이는 일반적으로 표준 자바스크립트 함수나 메서드를 사용하여 이루어집니다.

#### __숫자 타입으로 변환 (To Number)__

##### __`Number()` 함수__

```javascript
Number("123");    // 123
Number("123abc"); // NaN
Number(true);     // 1
Number(false);    // 0
Number(null);     // 0
Number(undefined); // NaN
```

##### __`parseInt()` 함수__
문자열을 정수로 변환합니다. 문자열의 시작 부분이 숫자가 아닌 경우 NaN을 반환합니다.

```javascript
parseInt("123");    // 123
parseInt("123.45"); // 123
parseInt("abc123"); // NaN
```

##### __`parseFloat()` 함수__
문자열을 부동 소수점 숫자로 변환합니다. 문자열의 시작 부분이 숫자가 아닌 경우 NaN을 반환합니다.


```javascript
Number("123");    // 123
Number("123abc"); // NaN
Number(true);     // 1
Number(false);    // 0
Number(null);     // 0
Number(undefined); // NaN
```

### __암시적 형 변환 (Implicit Type Conversion)__
암시적 형 변환은 자바스크립트 엔진이 자동으로 데이터 타입을 변환하는 것을 의미합니다. 이는 연산자나 표현식에 의해 자동으로 발생합니다.

##### __문자열 결합__
숫자와 문자열을 더할 때, 숫자는 자동으로 문자열로 변환됩니다.

```javascript
let result = "The answer is " + 42; // "The answer is 42"
let result2 = 42 + " is the answer"; // "42 is the answer"
```

##### __숫자 연산__
문자열이 숫자 연산에 사용될 때, 자바스크립트는 문자열을 숫자로 변환합니다.

```javascript
let result = "42" - 0;  // 42
let result2 = "42" * 1; // 42
let result3 = "42" / 2; // 21
```

##### __불리언 컨텍스트__
자바스크립트에서 조건문은 `truthy` 와 `falsy` 값을 사용합니다


```javascript
if (123) { // 123은 truthy 값입니다.
    console.log("This is true");
}

if ("") { // 빈 문자열은 falsy 값입니다.
    console.log("This is false");
}
```

##### __객체 변환__
객체가 원시 타입으로 변환될 때는 `toString()` 이나 `valueOf()` 메서드가 호출됩니다.


```javascript
let obj = {
    toString() {
        return "object as string";
    },
    valueOf() {
        return 42;
    }
};

let result = obj + ""; // "object as string"
let result2 = obj * 2; // 84
```

##### __비교 연산__
비교 연산자는 다양한 암시적 형 변환을 수행합니다.


```javascript
123 == "123"; // true (숫자와 문자열이 동일한 값으로 변환됨)
0 == false;   // true (0은 falsy 값, false와 동일)
null == undefined; // true (두 값은 느슨한 비교에서 동일)
```