---
layout: post
title: Hoisting의 변수 var
date: 2024-05-24 18:21 +0900
description: JAVASCRIPT
image: ../assets/img/javascript.png
category: JAVASCRIPT
tags: JAVASCRIPT Hoisting 호이스팅 변수 var let const 함수 함수호이스팅 클래스호이스팅
published: true
sitemap: true
---

# JAVASCRIPT
해당 포스팅에서는 호이스팅(Hoisting) 변수중 하나인 var에 대해 다룹니다.<br />


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
해당 포스팅에서는 호이스팅(Hoisting)의 변수중 `var` 에 대해 다룹니다. 꽤 많이 길기에 오른쪽에 있는 목차를 활용해 주세요.

### __호이스팅(Hoisting)의 개념__
호이스팅(Hoisting)은 __JAVASCRIPT 에서 변수 선언과 함수 선언이 코드의 최상위로 끌어올려지는 동작__ 을 의미합니다. 즉 __실제 코드 작성 위치와 상관없이 변수 및 함수 선언이 코드의 실행 전에 처리__ 되는 것을 말합니다. 이로인해, 변수와 함수는 선언되기 전에 참조될 수 있습니다.

### __변수 호이스팅__

#### __var의 호이스팅__

##### __선언과 초기화__

`var` 로 선언된 변수는 다음과 같은 과정을 거치게 됩니다.
1. __선언 단계__ : 변수의 선언이 호이스팅되어 코드의 최상단으로 이동합니다.
2. __초기화 단계__ : 변수의 초기화는 실제 코드가 실행될 때 발생합니다.

이로 인해, __선언 전에 변수를 참조하면 `undefined`__ 가 반환됩니다. 이는 변수가 선언되었지만 초기화되지 않았기 떄문입니다.

##### __예시 코드와 설명 첫번째__

```javascript
console.log(x);  // undefined
var x = 5;
console.log(x);  // 5
```

위 코드의 실행 순서를 호이스팅을 고려하여 설명해보겠습니다.

###### __1. 호이스팅 후 코드__

```javascript
var x;
console.log(x);  // undefined
x = 5;
console.log(x);  // 5
```

2. 변수 `x` 의 선언이 최상단으로 이동합니다. 
3. 첫번쨰 `console.log(x);` 는 `x`가 아직 초기화되지 않았으므로 `undefined`를 출력합니다.
4. `x`에 `5`를 할당합니다.
5. 두번쨰 `console.log(x)`는 `x`가 초기화되었으므로 `5`를 출력합니다.

##### __함수 내에서의 var 호이스팅 코드와 설명__

```javascript
function example() {
    console.log(y);  // undefined
    var y = 10;
    console.log(y);  // 10
}

example();
```

`var`의 호스팅은 함수 내에서도 동일하게 발생합니다. __함수 스코프에서 선언된 변수는 함수의 최상단으로 호이스팅__ 됩니다. 위 코드의 실행 순서를 호이스팅을 고려하여 설명해보겠습니다.

###### __1. 호이스팅 후 코드__

```javascript
function example() {
    var y;
    console.log(y);  // undefined
    y = 10;
    console.log(y);  // 10
}
example();
```

2. 함수 `example` 내에서 변수 `y`의 선언이 __함수 최상단으로 이동__ 합니다.
3. 첫번째 `console.log(y)`는 `y`가 아직 초기화되지 않았으므로 `undefined`를 출력합니다.
4. `y`에 `10`를 할당합니다.
5. 두번쨰 `console.log(y)`는 `y`가 초기화되었으므로 `10`를 출력합니다.

##### __반복문 내에서의 var 호이스팅 코드와 설명__

```javascript
for (var i = 0; i < 3; i++) {
    setTimeout(function() {
        console.log(i);
    }, 1000);
}
```

위의 코드에서는 `setTimeout` 함수가 비동기로 실행되므로, 모든 `setTimeout`콜백이 실행될 때 `i`의 값은 이미 __3__ 입니다. 따라서 __3__ 이 세번 출력됩니다.<br/>
이 문제를 해결하려면,  `let`을 사용하여 블록 스코프를 적용하거나 __즉시 실행 함수(IIFE)__ 를 사용할 수 있습니다.

###### __1. `let`을 사용하여 블록 스코프 적용__

```javascript
for (let i = 0; i < 3; i++) {
    setTimeout(function() {
        console.log(i);
    }, 1000);
}
```

###### __2. `IIFE`를 사용__

```javascript
for (var i = 0; i < 3; i++) {
    (function(i) {
        setTimeout(function() {
            console.log(i);
        }, 1000);
    })(i);
}
```

##### __호이스팅과 함수 선언__

```javascript
console.log(square(5));  // 25

function square(n) {
    return n * n;
}
```

`var`와 __함께 함수 선언도 호이스팅__ 됩니다. 함수 선언은 전체 함수가 호이스팅되어 코드의 최상단에서 사용할 수 있게 됩니다. 위의 코드의 실행 순서를 호이스팅을 고려하여 설명하겠습니다.

###### __1. 호이스팅 후 코드__

```javascript
function square(n) {
    return n * n;
}

console.log(square(5));  // 25
```

2. 함수 `square`의 선언과 정의가 최상단으로 이동합니다.
3. `square(5)`호출이 정상적으로 동작하여 `25`를 출력합니다.

### __결론__
호이스팅은 JAVASCRIPT의 중요한 개념으로, __변수와 함수 선언이 코드의 최상단으로 끌어올려지는 동작__ 입니다. `var`로 선언된 변수는 __선언이 호이스팅 되지만 초기화는 그렇지 않기 때문에 초기화 전에 접근하면__ `undefined`를 반환합니다. 이 동작을 이해하면 __코드의 실행 흐름을 더 명확히 파악하고, 예기치 않은 오류를 피할 수 있습니다.__  <br />
하지만 `var`의 이러한 특성 떄문에 종종 의도치 않은 동작이 발생할 수 있으므로, __변수 선언시 `let`이나 `const`를 사용하는 것이 더 권장__ 됩니다.
`let`과 `const`는 블록 스코프를 가지며, TDZ를 통해 선언 전에 접근을 방지하므로 __코드의 안전성과 가독성을 높이는 데 도움이 됩니다.