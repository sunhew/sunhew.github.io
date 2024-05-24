---
layout: post
title: 프로토타입
date: 2024-05-22 19:24 +0900
description: JAVASCRIPT
image: ../assets/img/javascript.png
category: JAVASCRIPT
tags: JAVASCRIPT 프로토타입
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
* 프로토타입 ✔️<br/>
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

## __프로토타입__<br/>

### __프로토타입의 기본 개념__
* __객체의 생성과 프로토타입__

    모든 자바스크립트 객체는 `prototype` 속성을 가지고 있으며, 이는 객체의 부모 역할을 하는 또 다른 객체를 참조합니다. 이 참조를 통해 객체는 자신의 프로토타입으로부터 메서드와 속성을 상속받을 수 있습니다.

* __프로토타입 체인__

    객체의 메서드나 속성에 접근할 때, 자바스크립트 엔진은 먼저 해당 객체 자체에서 메서드나 속성을 찾습니다. 만약 찾지 못하면, 프로토타입 체인을 따라 상위 프로토타입에서 해당 메서드나 속성을 찾습니다. 최종적으로 null에 도달할 때까지 찾지 못하면 undefined를 반환합니다.


### __프로토타입의 사용 예시__
* __함수와 프로토타입__

    함수가 생성될 때, 함수 객체는 자동으로 `prototype` 속성을 가집니다. 이 속성은 빈 객체로 초기화되며, 이 객체는 생성된 모든 인스턴스의 프로토타입이 됩니다.
    아래 예제에서 `Person` 생성자 함수의 프로토타입 객체에 `greet` 메서드를 추가하였습니다. `person1` 객체는 `Person` 의 인스턴스로, `greet` 메서드를 호출할 수 있습니다. 이는 `person1` 객체가 `Person.prototype` 을 프로토타입으로 가지고 있기 때문입니다.

```javascript
function Person(name) {
    this.name = name;
}

Person.prototype.greet = function() {
    console.log('Hello, ' + this.name);
};

const person1 = new Person('Alice');
person1.greet(); // Hello, Alice
```

* __객체 리터럴과 프로토타입__

    객체 리터럴로 생성된 객체는 기본적으로 `Object.prototype` 을 프로토타입으로 가집니다. `obj` 객체는 `toString` 메서드를 가지고 있지 않지만, 프로토타입 체인을 통해 `Object.prototype` 에서 상속받아 사용할 수 있습니다.

```javascript
const obj = {a: 1};

console.log(obj.toString()); // [object Object]
```

### __프로토타입의 상속__
프로토타입 상속을 통해 객체 간에 메서드와 속성을 공유할 수 있습니다. 이는 자바스크립트에서 객체 지향 프로그래밍을 구현하는 중요한 기법입니다.

* 기본 상속 예제

    아래 예제에서 `Dog` 생성자는 `Animal` 생성자로부터 상속받습니다. `Dog.prototype` 을 `Animal.prototype` 을 이용해 생성하고, `Dog.prototype.constructor` 를 `Dog` 로 설정하여 상속 구조를 형성합니다. `dog` 객체는 `Dog` 의 인스턴스로, `speak` 메서드를 호출할 수 있으며, 이는 `Dog.prototype` 의 `speak` 메서드를 사용합니다

* `class` 문법과 프로토타입

    ES6에서는 `class` 문법을 도입하여 프로토타입 기반 상속을 더 쉽게 구현할 수 있습니다. `class` 문법을 사용하면 생성자 함수와 프로토타입 메서드를 정의하는 것이 더 직관적이고 간결해집니다. `super` 키워드를 사용하여 부모 클래스의 생성자를 호출할 수 있습니다.


```javascript
class Animal {
    constructor(name) {
        this.name = name;
    }

    speak() {
        console.log(this.name + ' makes a noise.');
    }
}

class Dog extends Animal {
    constructor(name) {
        super(name);
    }

    speak() {
        console.log(this.name + ' barks.');
    }
}

const dog = new Dog('Rex');
dog.speak(); // Rex barks.
```

### __프로토타입 체인 탐색__

프로토타입 체인 탐색은 객체의 메서드나 속성을 찾을 때, 자바스크립트 엔진이 객체의 프로토타입 체인을 따라 탐색하는 과정입니다. 이를 통해 객체는 자신의 프로토타입 및 상위 프로토타입에서 정의된 메서드와 속성을 사용할 수 있습니다. 아래 예제에서 `car` 객체는 `model` 속성을 직접 가지고 있지만, `drive` 메서드는 프로토타입 체인을 통해 `Car.prototype` 에서 상속받습니다.

```javascript
function Car(model) {
    this.model = model;
}

Car.prototype.drive = function() {
    console.log(this.model + ' is driving.');
};

const car = new Car('Tesla');
console.log(car.hasOwnProperty('model')); // true
console.log(car.hasOwnProperty('drive')); // false
console.log('drive' in car); // true
car.drive(); // Tesla is driving
```

자바스크립트의 프로토타입 시스템은 객체 지향 프로그래밍을 가능하게 하는 강력한 기능입니다. 프로토타입을 이해하면 자바스크립트의 상속과 메서드 공유 메커니즘을 효과적으로 활용할 수 있습니다.