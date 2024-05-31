---
layout: post
title: Hoisting의 클래스 호이스팅
date: 2024-05-27 09:29 +0900
description: JAVASCRIPT
image: ../assets/img/javascript.png
category: JAVASCRIPT
tags: JAVASCRIPT Hoisting 호이스팅 변수 var let const 함수 함수호이스팅 클래스호이스팅
published: true
sitemap: true
---

# JAVASCRIPT
해당 포스팅에서는 호이스팅(Hoisting)의 클래스 호이스팅에 대해 다룹니다.<br />


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
해당 포스팅에서는 호이스팅(Hoisting)의 __클래스 호이스팅__ 에 대해 다룹니다.

### __클래스 호이스팅의 개념__
호이스팅(Hoisting)은 __JAVASCRIPT 에서 함수 선언이 해당 범위의 최상단으로 끌어올려지는 동작__ 을 의미합니다. 하지만 클래스 호이스팅은 변수 호이스팅과 유사하면서도 약간 다른 동작 방식을 가집니다. 클래스는 선언되기 전에 접근할 수 없으면 이는 TDZ(Temporal Dead Zone)라는 개념과 연관이 있습니다.

### __클래스 호이스팅의 동작__

#### __TDZ(Temporal Dead Zone)__
TDZ는 __블록 스코프 내에서 클래스 선언이 이루어지기 전까지의 영역__ 을 의미합니다. 이 기간 동안 클래스에 접근하려 하면 `ReferenceError`가 발생합니다. 즉, 클래스 선언이 호이스팅되지만, TDZ로 인해 선언 전에 접근 할 수 없습니다.

##### __클래스 선언문(Class Declaration)__
클래스 선언문은 호이스팅되지만, TDZ로 인해 선언 전에 접근할 수 없습니다. 클래스 선언이 실제 코드에 도달하기 전까지는 클래스에 접근할 수 없습니다. 아래 코드에서 `class MyClass` 선언은 호이스팅되지만, 선언 전에 접근하려 하면 `ReferenceError`가 발생합니다.

```javascript
// console.log(MyClass);  // ReferenceError: Cannot access 'MyClass' before initialization
class MyClass {
    constructor(name) {
        this.name = name;
    }
}

let instance = new MyClass('example');
console.log(instance.name);  // 'example'
```

##### __클래스 표현식(Class Expression)__
클래스 표현식은 변수 호이스팅 규칙을 따릅니다. 즉, 변수 선언만 호이스팅되며, __변수에 할당된 클래스는 호이스팅되지 않습니다.__ 따라서 클래스 표현식으로 선언된 클래스는 선언 전에 접근할 수 없습니다. 아래 코드에서 `let MyClass`선언만 호이스팅되므로, 초기화 전에는 `MyClass`에 접근할 수 없습니다.

```javascript
// console.log(MyClass);  // ReferenceError: Cannot access 'MyClass' before initialization
let MyClass = class {
    constructor(name) {
        this.name = name;
    }
};

let instance = new MyClass('example');
console.log(instance.name);  // 'example'
```

#### __클래스 호이스팅과 함수 호이스팅 비교__
클래스 호이스팅과 함수 호이스팅의 주요 차이점은 __클래스의 경우 TDZ로 인해 선언 전에 접근할 수 없다__ 는 점입니다. 반면 __함수 선언문은 전체가 호이스팅되어 선언 전에 호출이 가능__ 합니다.

##### __함수 선언문(Function Declaration)__
아래 코드에서 함수 `square`는 선언되기 전에 호출되었지만, 정상적으로 동작합니다. 이는 함수 선언문이 호이스팅되어 최상단으로 끌어올려졌기때문입니다.

```javascript
console.log(square(5));  // 25

function square(n) {
    return n * n;
}
```

##### __클래스 선언문(Class Declaration)__
아래 코드에서 클래스 `MyClass`는 선언되기 전에 접근하려 하면 `ReferenceError`가 발생합니다. 이유는 __클래스 선언문이 호이스팅되지만, TDZ로 인해 선언전에 접근할 수 없기 떄문__ 입니다.

```javascript
// console.log(MyClass);  // ReferenceError: Cannot access 'MyClass' before initialization
class MyClass {
    constructor(name) {
        this.name = name;
    }
}

let instance = new MyClass('example');
console.log(instance.name);  // 'example'
```

### __클래스 선언과 표현식의 예시__

#### __클래스 선언문__
아래 코드에서는 `class Car`선언이 정상적으로 이루어지며, `car`클래스의 인스턴스를 생성하고 메서드를 호출할 수 있습니다.

```javascript
class Car {
    constructor(model) {
        this.model = model;
    }

    displayModel() {
        console.log(this.model);
    }
}

let myCar = new Car('Tesla Model 3');
myCar.displayModel();  // Tesla Model 3
```

#### __클래스 표현식__
아래 코드에서는 `let Car`에 클래스 표현식을 할당하여 `Car` 클래스의 인스턴스를 생성하고 메서드를 호출할 수 있습니다.

```javascript
let Car = class {
    constructor(model) {
        this.model = model;
    }

    displayModel() {
        console.log(this.model);
    }
};

let myCar = new Car('Tesla Model 3');
myCar.displayModel();  // Tesla Model 3
```

### __마무리__
클래스 호이스팅은 JAVASCRIPT에서 중요한 개념으로, __클래스 선언이 코드의 최상단으로 끌어올려지지만, TDZ로 인해 선언 전에 접근할 수 없습니다.__ 이는 클래스 선언문과 함수 선언문 사이의 주요 __차이점__ 입니다. 이러한 동작을 이해한다면 __클래스와 함수의 선언과 사용을 더 명확하게 이해하고, 예기치 않은 오류를 방지할 수 있습니다.__