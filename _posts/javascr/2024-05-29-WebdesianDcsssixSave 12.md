---
layout: post
title: this
date: 2024-05-29 20:04 +0900
description: JAVASCRIPT
image: ../assets/img/javascript.png
category: JAVASCRIPT
tags: JAVASCRIPT this
published: true
sitemap: true
---

# JAVASCRIPT
해당 포스팅에서는 __this__ 에 대해 다룹니다.<br />


## __JAVASCRIPT__
* 자바스크립트 장단점 <br/>
* 데이터 타입 <br/>
* 데이터 형 변환<br/>
* 불변성을 유지하려면 어떻게..<br/>
* 프로토타입 <br/>
* var, let, const 차이 <br/>
* 호이스팅(Hoisting) <br/>
* es6 문법 특징과 차이<br/>
* this ✔️<br/>
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

## __this__<br/>
해당 포스팅에서는 자바스크립트의 __this__ 에 대해 다룹니다.

### __this의 개념__
`this`는 자바스크립트에서 함수가 호출될 때 결정되는 특별한 키워드입니다. 또한 `this`가 가리키는 값은 __함수가 어떻게 호출되었는지에 따라 달라집니다.__ `this`는 런타임에 바인딩되며, 함수 호출 패턴에 따라 다르게 설정됩니다. 자바스크립트에서는 __함수 호출 방식에 따라 `this`의 값이 달라지기 떄문에 이해하는 것이 중요__ 합니다.

### __this의 동작__

#### __일반 함수 호출__
함수가 전역 컨텍스트에서 호출될 때, `this`는 __전역 객체__ 를 가리킵니다. __브라우저 환경에서는 전역 객체가 `window`가 되며, Node.js에서는 `global`객체가 됩니다.__

```javascript
function showThis() {
    console.log(this);
}
showThis(); // 브라우저에서는 window, Node.js에서는 global
```

#### __메서드 호출__
객체의 메서드로 호출될 때, `this`는 해당 메서드를 호출한 객체를 가리킵니다.

```javascript
const obj = {
    value: 42,
    showThis: function() {
        console.log(this);
    }
};
obj.showThis(); // obj 객체
```

#### __생성자 함수 호출__
__`new`__ 키워드를 사용하여 생성자 함수를 호출하면, __`this`는 새로 생성된 객체__ 를 가리킵니다.

```javascript
function Person(name) {
    this.name = name;
}
const person1 = new Person('Alice');
console.log(person1.name); // Alice
```

#### __ `call`, `apply`, `bind` 메서드를 이용한 호출__
__`call`과 `apply`메서드__ 를 사용하면, __`this`를 명시적으로 설정__ 할 수 있습니다. `bind`메서드는 `this`값을 영구적으로 바인딩한 새로운 함수를 반환합니다.

```javascript
function showThis() {
    console.log(this);
}
const obj = { value: 42 };

showThis.call(obj); // obj
showThis.apply(obj); // obj

const boundShowThis = showThis.bind(obj);
boundShowThis(); // obj
```

#### __화살표 함수__
화살표 함수는 __`this`바인딩이 정적으로 결정__ 됩니다. 화살표 함수의 `this`는 __함수가 선언된 위치의 상위 스코프__ 의 `this`를 가리킵니다.

```javascript
const obj = {
    value: 42,
    showThis: function() {
        const inner = () => {
            console.log(this);
        };
        inner();
    }
};
obj.showThis(); // obj
```

### __this의 사용예시__

#### __객체 메서드에서의 this__
__객체의 메서드__ 에서 `this`는 __해당 메서드를 호출한 객체를 가리킵니다.__ 이를 통해 객체의 속성에 접근하거나 메서드를 호출할 수 있습니다.

```javascript
const car = {
    model: 'Tesla',
    drive: function() {
        console.log(`${this.model} is driving.`);
    }
};
car.drive(); // Tesla is driving.
```


#### __생성자 함수에서의 this__
__생성자 함수에서 `this`는 새로 생성된 객체__ 를 가리키며, 생성자 __함수 내부에서 해당 객체의 속성을 정의__ 할 수 있습니다.

```javascript
function Car(model) {
    this.model = model;
}
const myCar = new Car('Toyota');
console.log(myCar.model); // Toyota
```


#### __이벤트 핸들러에서의 this__
__DOM 이벤트 핸들러__ 에서 `this`는 __이벤트가 발생한 요소__ 를 가리킵니다.

```javascript
document.querySelector('button').addEventListener('click', function() {
    console.log(this); // 클릭된 버튼 요소
});
```

#### __ 콜백 함수에서의 this__
__콜백 함수__ 에서의 `this`는 __함수가 호출된 컨텍스트에 따라 달라집니다.__ 주로 `this`가 기대한 값과 다를 수 있으므로, __`bind`나 화살표 함수를 사용하여 해결__ 할 수 있습니다.

```javascript
function Timer() {
    this.seconds = 0;
    setInterval(function() {
        this.seconds++;
        console.log(this.seconds);
    }.bind(this), 1000);
}
const timer = new Timer();
```

### __this와 관련된 주의사항__

<!--  -->
#### __엄격 모드 (Strict Mode)__
__엄격 모드에서는 `this`가 전역 객체로 설정되지 않습니다__. 일반 함수 호출에서 `this`는 __`undefind`__ 가 됩니다.


```javascript
'use strict';
function showThis() {
    console.log(this);
}
showThis(); // undefined
```


#### __메서드와 화살표 함수의 혼용__
화살표 함수는 `this`를 __상위 스코프에 바인딩__ 하므로, 객체 메서드로 사용될 때 주의가 필요합니다.

```javascript
const obj = {
    value: 42,
    showThis: () => {
        console.log(this);
    }
};
obj.showThis(); // undefined (전역 객체를 가리킴)
```


### __마무리 정리__
`this`는 __자바스크립트의 동적 바인딩 특성을 이해하는데 중요한 역할__ 을 합니다. __함수 호출 방식에 따라 `this`가 가리키는 대상이 달라지므로__, 이를 정확히 이해하고 사용하는 것이 중요합니다. 자바스크립트에서 `this`의 동작 방식을 잘 이해하면, 코드를 보다 효과적으로 작성하고 디버깅할 수 있습니다!