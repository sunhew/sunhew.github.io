---
layout: post
title: Hoisting의 변수 let과 const
date: 2024-05-25 18:13 +0900
description: JAVASCRIPT
image: ../assets/img/javascript.png
category: JAVASCRIPT
tags: JAVASCRIPT Hoisting 호이스팅 변수 var let const 함수 함수호이스팅 클래스호이스팅
published: true
sitemap: true
---

# JAVASCRIPT
해당 포스팅에서는 호이스팅(Hoisting) 변수중 하나인 let과 const에 대해 다룹니다.<br />


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
해당 포스팅에서는 호이스팅(Hoisting)의 변수중 `let` 과 `const` 에 대해 다룹니다. 꽤 많이 길기에 오른쪽에 있는 목차를 활용해 주세요.

### __호이스팅(Hoisting)의 개념 다시 짚기__
호이스팅(Hoisting)은 __JAVASCRIPT 에서 변수와 함수 선언이 해당 범위의 최상단으로 끌어올려지는 동작__ 을 의미합니다. `let`과 `const`도 호이스팅 되지만, `var`와는 다른 동작 방식을 가집니다. `let`과 `const`는 __호이스팅되지만, 선언 전에 접근하려 하면 오류가 발생하는__ TDZ(Temporal Dead Zone)라는 개념과 연관이 있습니다.

### __TDZ(Temporal Dead Zone)__
TDZ는 __블록 스코프 내에서 변수가 선언되기 전까지의 영역__ 을 의미합니다. 이 기간 동안 변수를 참조하려 하면 `ReferenceError`가 발생합니다. 이는 `let`과 `const`가 __호이스팅은 되지만, TDZ로 인해 선언 전에 접근 할 수 없도록 하기 떄문__ 입니다.

### __let의 호이스팅__

#### __특징__
1. __블록 스코프__ : `let` 변수는 블록 스코프를 가지며, 선언된 블록 내에서만 유효합니다.
2. __TDZ__ : `let` 변수는 선언되기 전까지 TDZ에 머물러, 해당 변수에 접근하려 하면 `ReferenceError`가 발생합니다.
3. __재선언 불가__ : 동일한 스코프 내에서 동일한 이름으로 변수를 재선언할 수 없습니다.

##### __예시 코드__

```javascript
console.log(a);  // ReferenceError: Cannot access 'a' before initialization
let a = 10;
console.log(a);  // 10
```

###### __위 코드의 실행 순서 해석__

1. 변수 `a`의 선언이 블록의 최상단으로 호이스팅됩니다.
2. 하지만 `a`는 TDZ에 있으므로 초기화되기 전까지 접근할 수 없습니다.
3. 첫번쨰 `console.log(a)`는 TDZ에 있는 `a`에 접근하려 하므로 `ReferenceError`가 발생합니다.
4. `a`에 `10`이 할당되어 초기화가 완료됩니다.
5. 두번쨰 `console.log(a)`는 정상적으로 `10`을 출력합니다.

### __const의 호이스팅__

#### __특징__
1. __블록 스코프__ : `const` 변수는 블록 스코프를 가지며, 선언된 블록 내에서만 유효합니다.
2. __TDZ__ : `let` 변수도 TDZ에 머물러, 해당 변수에 접근하려 하면 `ReferenceError`가 발생합니다.
3. __재선언 불가__ : 동일한 스코프 내에서 동일한 이름으로 변수를 재선언할 수 없습니다.
4. __재할당 불가__ : `const`로 선언된 변수는 초기화 후 재할당이 불가능합니다.

##### __예시 코드__

```javascript
console.log(b);  // ReferenceError: Cannot access 'b' before initialization
const b = 20;
console.log(b);  // 20
```

###### __위 코드의 실행 순서 해석__

1. 변수 `b`의 선언이 블록의 최상단으로 호이스팅됩니다.
2. 하지만 `b`는 TDZ에 있으므로 초기화되기 전까지 접근할 수 없습니다.
3. 첫번쨰 `console.log(b)`는 TDZ에 있는 `a`에 접근하려 하므로 `ReferenceError`가 발생합니다.
4. `b`에 `20`이 할당되어 초기화가 완료됩니다.
5. 두번쨰 `console.log(b)`는 정상적으로 `20`을 출력합니다.

### __TDZ의 다양한 상황에서의 예시__

##### __변수 선언 전에 접근__

```javascript
{
    // TDZ 시작
    // console.log(x);  // ReferenceError: Cannot access 'x' before initialization
    let x = 30;  // TDZ 종료
    console.log(x);  // 30
}
```

##### __함수 내에서 TDZ__

```javascript
function example() {
    // TDZ 시작
    // console.log(y);  // ReferenceError: Cannot access 'y' before initialization
    let y = 40;  // TDZ 종료
    console.log(y);  // 40
}
example();
```

##### __조건문 내에서 TDZ__

```javascript
if (true) {
    // TDZ 시작
    // console.log(z);  // ReferenceError: Cannot access 'z' before initialization
    const z = 50;  // TDZ 종료
    console.log(z);  // 50
}

```

### __let과 const의 호이스팅 동작 정리__

|특성|let|const|
|---|---|---|
|스코프|블록 스코프|블록 스코프|
|TDZ|존재 (선언 전에 접근 불가)|존재 (선언 전에 접근 불가)|
|재선언|불가능|불가능|
|재할당|가능|불가능|
|초기화 필요 여부|선언 후 초기화 가능|선언 시 초기화 필요|


### __마무리__
`let`과 `const`는 `var`와 다르게 호이스팅되지만, TDZ로 인해 선언 전에 접근할 수 없습니다. 이로 인해 코드의 안정성과 예측 가능성을 높여줍니다. `let`은 재할당이 가능한 변수를 선언할 때 사용하고, `const`는 재할당이 불가능한 상수를 선언할 때 사용합니다. 이러한 특성을 이해하고, 활용하면, __더 안전하고 유지보수하기 쉬운 코드를 작성할 수 있습니다.__ 긴 글 읽어주셔서 감사합니다.