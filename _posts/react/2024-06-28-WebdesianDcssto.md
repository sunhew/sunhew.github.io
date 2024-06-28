---
layout: post
title: 리액트의 생명 주기 함수(LifeCycle)
date: 2024-06-28 09:12 +0900
description: REACT
image: ../assets/img/react13.jpg
category: react
tags: react생명주기함수(LifeCycle) 생명주기함수 함수 LifeCycle react
published: true
sitemap: true
---

# REACT
해당 포스팅에서는 REACT의 생명 주기 함수(LifeCycle)에 대해 다룹니다.  <br />


## __이번 포스팅 목차__
* REACT의 생명 주기 함수(LifeCycle) <br/>

## __리액트의 생명 주기 함수(LifeCycle)__<br/>
__생명 주기 함수(LifeCycle)__ 는 클래스형 컴포넌트에서 컴포넌트가 생성되고, 업데이트되며, 소멸되는 과정을 제어하기 위해 사용됩니다. 함수형 컴포넌트에서는 생명주기 함수 대신 __훅(Hooks)__ 을 사용하여 동일한 작업을 수행할 수 있습니다. 여기서는 클래스형 컴포넌트의 생명주기 함수에 대해 자세히 설명하고, 함수형 컴포넌트에서의 훅 사용법도 간단하게 설명해보겠습니다.

### __클래스형 컴포넌트의 생명주기__
클래스형 컴포넌트의 생명주기는 크게 세 가지 단계로 나눌 수 있습니다. 각 단계에는 여러 생명 주기 함수가 존재 합니다.

1. __마운팅(Mounting)__: 컴포넌트가 생성되어 DOM에 삽입될 때 호출됩니다.

2. __업데이트(Updating)__: 컴포넌트의 상태나 속성이 변경되어 다시 렌더링될 때 호출됩니다.

3. __언마운팅(Unmounting)__: 컴포넌트가 DOM에서 제거될 때 호출됩니다.

### __1. 마운팅(Mounting)의 생명주기 함수__

#### __constructor(props)__
컴포넌트가 처음 생성될 때 호출되며, 상태 초기화 및 클래스 필드를 바인딩하는 데 사용됩니다.

```javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }
}
```

#### __componentDidMount()__
컴포넌트가 처음 렌더링된 후에 호출됩니다. 여기서 __AJAX 요청__ 이나 __타이머 설정__ 등의 작업을 수행할 수 있습니다.

```javascript
class MyComponent extends React.Component {
  componentDidMount() {
    console.log('Component has mounted');
    // 데이터 가져오기 등의 작업
  }
}
```

### __2. 업데이트(Updating)의 생명주기 함수__

#### __shouldComponentUpdate(nextProps, nextState)__
컴포넌트가 리렌더링될지 여부를 결정합니다. __성능 최적화__ 를 위해 사용됩니다. 기본적으로는 true를 반환합니다.

```javascript
class MyComponent extends React.Component {
  shouldComponentUpdate(nextProps, nextState) {
    return nextState.count !== this.state.count;
  }
}
```

#### __componentDidUpdate(prevProps, prevState, snapshot)__
컴포넌트가 업데이트된 후에 호출됩니다. DOM을 조작하거나 __네트워크 요청__ 을 할 수 있습니다.

```javascript
class MyComponent extends React.Component {
  componentDidUpdate(prevProps, prevState) {
    if (prevState.count !== this.state.count) {
      console.log('Component did update');
    }
  }
}
```

### __3. 언마운팅(Unmounting)의 생명주기 함수__

#### __componentWillUnmount()__
컴포넌트가 DOM에서 제거되기 전에 호출됩니다. __타이머 정리, 구독 해제__ 등의 작업을 수행할 수 있습니다.

```javascript
class MyComponent extends React.Component {
  componentWillUnmount() {
    console.log('Component will unmount');
    // 정리 작업 수행
  }
}
```

### __함수형 컴포넌트의 훅(Hooks)__
함수형 컴포넌트에서는 이전에 다뤘었던 __useState, useEffect__ 등의 훅을 사용하여 생명주기와 유사한 작업을 수행할 수 있습니다.

### __useEffect 훅__
__useEffect__ 는 컴포넌트가 렌더링될 때와 업데이트될 때 실행됩니다. 두 번째 인자로 전달되는 의존성 배열을 통해 특정 값이 변경될 때만 실행되도록 할 수 있습니다. 컴포넌트가 언마운트될 때는 정리 함수가 호출됩니다.

```javascript
import React, { useState, useEffect } from 'react';

function MyComponent() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log('Component did mount or update');
    
    return () => {
      console.log('Component will unmount');
      // 정리 작업 수행
    };
  }, [count]); // count가 변경될 때마다 실행

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

### __마무리__
리액트의 __생명주기 함수__ 는 컴포넌트가 생성되고, 업데이트되며, 소멸되는 과정을 제어하기 위해 사용됩니다. 클래스형 컴포넌트에서는 다양한 생명주기 함수가 존재하며, 함수형 컴포넌트에서는 __useEffect__ 와 같은 __훅(Hooks)__ 을 사용하여 동일한 작업을 수행할 수 있습니다. 생명주기 함수를 올바르게 사용함으로써 컴포넌트의 상태와 동작을 효율적으로 관리할 수 있습니다. 마무리로 생명주기 함수를 요약해보겠습니다.

* __constructor(props)__: 상태 초기화 및 클래스 필드 바인딩

* __componentDidMount()__: 컴포넌트가 마운트된 후 실행

* __shouldComponentUpdate(nextProps, nextState)__: 컴포넌트가 리렌더링될지 여부 결정

* __componentDidUpdate(prevProps, prevState, snapshot)__: 컴포넌트가 업데이트된 후 실행

* __componentWillUnmount()__: 컴포넌트가 언마운트되기 전에 실행

__오늘도 제 블로그에 방문해주셔서 감사합니다!__