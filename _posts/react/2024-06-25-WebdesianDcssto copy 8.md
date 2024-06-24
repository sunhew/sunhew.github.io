---
layout: post
title: 리액트의 Side-Effect
date: 2024-06-25 01:37 +0900
description: REACT
image: ../assets/img/react09.jpg
category: react
tags: reactSide-Effect Side-Effect react
published: true
sitemap: true
---

# REACT
해당 포스팅에서는 REACT의 Side-Effect에 대해 다룹니다.  <br />


## __이번 포스팅 목차__
* REACT의 Side-Effect <br/>

## __리액트의 컴포넌트__<br/>
리액트(React) 컴포넌트는 두 가지 주요 형태로 작성될 수 있습니다. __함수형 컴포넌트__ 와 __클래스형 컴포넌트__ 이 두 가지 형태는 리액트의 주요 업데이트와 발전과 함께 기능적으로 많은 변화를 겪어왔습니다. 여기서는 함수형 컴포넌트와 클래스형 컴포넌트의 차이점, 장단점, 그리고 각 형태를 사용하는 사례에 대해 자세히 설명하겠습니다.

### __함수형 컴포넌트 (Functional Components)__
함수형 컴포넌트는 단순히 자바스크립트 함수로 작성되며, 리액트 훅(Hooks)을 통해 상태 관리와 사이드 이펙트를 처리합니다.

#### __특징__

* __간단한 구조__ : 함수형 컴포넌트는 기본적으로 함수이기 때문에 간단하고 가독성이 높습니다.

* __훅 사용__ : 리액트 16.8부터 도입된 훅(Hooks)을 사용하여 상태 관리(`useState`), 생명주기 메서드(`useEffect`), 그리고 다른 리액트 기능을 사용할 수 있습니다.
  
#### __예시__

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
```

#### __장점__

* __간결함__ : 함수형 컴포넌트는 코드가 짧고 간결합니다.

* __직관적인 상태 관리__ : 훅을 사용하여 상태와 생명주기를 직관적으로 관리할 수 있습니다.

* __테스트 용이__ : 함수형 컴포넌트는 순수 함수에 가깝기 때문에 테스트하기 쉽습니다.

#### __단점__

* __초기 학습 곡선__ : 훅의 개념과 사용법을 처음 접하는 개발자에게는 다소 어려울 수 있습니다.

### __클래스형 컴포넌트 (Class Components)__
클래스형 컴포넌트는 __ES6 클래스 문법을 사용하여 작성__ 되며, 리액트 생명주기 메서드를 통해 __상태와 사이드 이펙트를 관리__ 합니다.

#### __특징__

* __상태와 생명주기 메서드__ : 클래스형 컴포넌트는 __상태(`state`)__ 와 __생명주기 메서드(`componentDidMount`, `componentDidUpdate`, `componentWillUnmount` 등)__ 를 통해 상태와 사이드 이펙트를 관리합니다.

* __this 바인딩__ : 클래스형 컴포넌트에서는 `this` 키워드를 사용하여 클래스의 속성과 메서드에 접근해야 합니다.
  
#### __예시__

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

  incrementCount = () => {
    this.setState({ count: this.state.count + 1 });
  };

  render() {
    return (
      <div>
        <p>You clicked {this.state.count} times</p>
        <button onClick={this.incrementCount}>Click me</button>
      </div>
    );
  }
}
```

#### __장점__

* __명확한 생명주기 관리__ : 생명주기 메서드를 통해 상태와 사이드 이펙트를 명확하게 관리할 수 있습니다.

* __전통적 접근__ : 객체 지향 프로그래밍(OOP)에 익숙한 개발자에게 친숙합니다.

#### __단점__

* __복잡한 문법__ : 클래스형 컴포넌트는 함수형 컴포넌트에 비해 더 복잡한 문법을 가지고 있습니다.

* __this 바인딩 문제__ : `this` 키워드를 바인딩해야 하는 번거로움이 있습니다.

### __함수형 컴포넌트와 클래스형 컴포넌트의 선택 기준__

* __새 프로젝트__ : 함수형 컴포넌트와 훅을 사용하는 것이 권장됩니다. 리액트 커뮤니티와 공식 문서에서도 함수형 컴포넌트를 우선적으로 사용하는 것을 추천합니다.

* __기존 코드베이스__ : 이미 클래스형 컴포넌트를 많이 사용하고 있는 기존 프로젝트에서는 일관성을 위해 계속 클래스형 컴포넌트를 사용하는 것이 좋을 수 있습니다.

* __성능 및 최적화__ : 함수형 컴포넌트와 훅은 리액트의 최신 기능과 최적화 기법을 더 잘 활용할 수 있습니다.

### __마무리__
리액트 컴포넌트를 작성할 때는 __함수형 컴포넌트__ 와 __클래스형 컴포넌트__ 중 프로젝트와 팀의 요구 사항에 맞는 방식을 선택하면 됩니다. 함수형 컴포넌트는 __간결하고 직관적인 코드__ 를 작성할 수 있게 해주며, 클래스형 컴포넌트는 __명확한 구조와 생명주기 관리__ 를 제공합니다. 최신 리액트 개발에서는 함수형 컴포넌트와 훅을 사용하는 것이 점점 더 일반화되고 있습니다.