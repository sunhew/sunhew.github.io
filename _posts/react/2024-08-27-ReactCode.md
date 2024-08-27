---
layout: post
title: REACT와 NODE.JS의 차이점 그리고 리액트의 코드
date: 2024-08-27 13:15 +0900
description: REACT
image: ../assets/img/reactcode.gif
category: react
tags: 리액트코드 REACTCODE code react node.js react와node.js의차이점
published: true
sitemap: true
---

# REACT
해당 포스팅에서는 REACT의 컴포넌트에 대해 다룹니다.  <br />


## __이번 포스팅 목차__
* REACT의 컴포넌트 <br/>

## __리액트의 컴포넌트__<br/>
리액트에서 __컴포넌트__ 는 사용자 인터페이스(UI)를 구축하는 기본 단위입니다. 컴포넌트는 __독립적이고 재사용 가능한 코드 블록__ 으로, 각각의 컴포넌트는 고유한 상태와 속성을 가질 수 있습니다. 리액트 컴포넌트는 __함수형 컴포넌트와 클래스형 컴포넌트__ 로 나눌 수 있습니다. 여기에서는 두 가지 컴포넌트의 종류와 그 사용법, 주요 특징을 자세히 설명하겠습니다.

### 1. __함수형 컴포넌트 (Functional Components)__
__함수형 컴포넌트__ 는 단순히 자바스크립트 함수로 정의됩니다. 함수형 컴포넌트는 props를 인자로 받아 UI를 반환합니다. 리액트 16.8 이후에는 __훅(Hooks)__ 을 사용하여 상태와 생명주기 기능을 추가할 수 있습니다.

#### __주요 특징__ 

* __간결한 문법__: 함수형 컴포넌트는 간단하고 가독성이 좋습니다.

* __훅 사용__: `useState`, `useEffect` 등의 훅을 사용하여 상태 관리와 사이드 이펙트를 처리할 수 있습니다.

```javascript
import React, { useState, useEffect } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;
  }, [count]);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}

export default Counter;
```

### 2. __클래스형 컴포넌트 (Class Components)__
__클래스형 컴포넌트__ 는  ES6 클래스 문법을 사용하여 정의됩니다. 클래스형 컴포넌트는 __`React.Component`__ 를 상속하며, __상태와 생명주기 메서드__ 를 가질 수 있습니다.

#### __주요 특징__ 

* __상태 관리__: `this.state`를 사용하여 상태를 관리합니다.합니다.

* __생명주기 메서드__: `componentDidMount`, `componentDidUpdate`, `componentWillUnmount` 등의 생명주기 메서드를 사용하여 컴포넌트의 생명주기 동안 특정 작업을 수행할 수 있습니다.

#### __사용 예시__

```javascript
import React, { Component } from 'react';

class Counter extends Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  componentDidMount() {
    document.title = `You clicked ${this.state.count} times`;
  }

  componentDidUpdate() {
    document.title = `You clicked ${this.state.count} times`;
  }

  increment = () => {
    this.setState({ count: this.state.count + 1 });
  }

  render() {
    return (
      <div>
        <p>You clicked {this.state.count} times</p>
        <button onClick={this.increment}>Click me</button>
      </div>
    );
  }
}

export default Counter;
```

## __함수형 컴포넌트 vs 클래스형 컴포넌트__

* __문법의 간결함__: 함수형 컴포넌트는 클래스형 컴포넌트보다 문법이 더 간결합니다.

* __성능__: 함수형 컴포넌트는 리액트의 최적화 기법(예: 리액트의 Fiber 구조)을 더 잘 활용할 수 있습니다.

* __훅의 사용__: 함수형 컴포넌트는 `useState`, `useEffect` 등의 훅을 사용하여 상태와 생명주기를 관리할 수 있습니다. 이는 클래스형 컴포넌트보다 더 직관적이고 코드가 간결해지는 장점이 있습니다.

### __컴포넌트 간 데이터 전달__
리액트 컴포넌트는 __props__ 를 사용하여 부모 컴포넌트에서 자식 컴포넌트로 데이터를 전달할 수 있습니다. __props__ 는 읽기 전용이며, 자식 컴포넌트는 이를 변경할 수 없습니다.

#### __사용 예시__

```javascript
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

function App() {
  return <Greeting name="Alice" />;
}
```

### __상태 관리 (State Management)__
컴포넌트는 __state__ 를 사용하여 __동적인 데이터를 관리__ 할 수 있습니다. __state__ 는 컴포넌트 내부에서 관리되며, `setState` 또는 `useState` 훅을 통해 업데이트됩니다.

#### __사용 예시__

```javascript
import React, { useState } from 'react';

function Toggle() {
  const [isOn, setIsOn] = useState(false);

  return (
    <button onClick={() => setIsOn(!isOn)}>
      {isOn ? 'ON' : 'OFF'}
    </button>
  );
}
```

### __생명주기 메서드 (Lifecycle Methods)__
클래스형 컴포넌트는 컴포넌트의 생명주기 동안 특정 작업을 수행하기 위해 __생명주기 메서드__ 를 사용할 수 있습니다. 함수형 컴포넌트에서는 `useEffect` 훅을 사용하여 동일한 작업을 수행할 수 있습니다.

#### __주요 생명주기 메서드__

* __componentDidMount__: 컴포넌트가 처음 렌더링된 후 호출됩니다.

* __componentDidUpdate__: 컴포넌트가 업데이트된 후 호출됩니다.

* __componentWillUnmount__: 컴포넌트가 언마운트되기 전에 호출됩니다.

#### __사용 예시__

```javascript
import React, { useEffect } from 'react';

function Example() {
  useEffect(() => {
    console.log('Component did mount');
    return () => {
      console.log('Component will unmount');
    };
  }, []);

  return <div>Example</div>;
}
```

## __마무리__
리액트의 __컴포넌트__ 는 사용자 인터페이스를 구축하는 __기본 단위__ 입니다. __함수형 컴포넌트와 클래스형 컴포넌트__ 는 각각의 장점과 사용 사례를 가지고 있습니다. 함수형 컴포넌트는 __간결한 문법__ 과 __훅을 통한 상태 및 생명주기 관리__ 의 장점을 제공하며, 클래스형 컴포넌트는 전통적인 __상태 관리__ 와 __생명주기 메서드__ 를 제공합니다. 컴포넌트 간 __데이터 전달과 상태 관리__ 는 리액트 애플리케이션에서 중요한 역할을 하며, 이를 통해 복잡한 사용자 인터페이스를 효율적으로 관리할 수 있습니다.