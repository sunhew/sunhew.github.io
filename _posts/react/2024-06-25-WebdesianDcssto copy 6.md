---
layout: post
title: 리액트의 훅
date: 2024-06-25 00:37 +0900
description: REACT
image: ../assets/img/react07.jpg
category: react
tags: react훅 훅 react react개념
published: true
sitemap: true
---

# REACT
해당 포스팅에서는 REACT의 훅을 다룹니다.  <br />


## __이번 포스팅 목차__
* REACT의 훅 <br/>

## __리액트 훅의 주요 특징__<br/>
리액트의 훅(Hooks)은 함수형 컴포넌트에서 상태와 생명주기 기능을 사용할 수 있게 해주는 __새로운 기능__ 입니다. 훅을 사용하면 클래스형 컴포넌트 없이도 리액트의 주요 기능을 활용할 수 있습니다. 

### __리액트 훅의 주요 종류와 사용법__

#### __1. useState__

* __상태 관리__: `useState` 훅은 함수형 컴포넌트에서 상태를 관리할 수 있게 해줍니다. 상태는 컴포넌트 내에서 값이 변경될 수 있는 데이터를 의미합니다.
* __사용법__: `const [state, setState] = useState(initialState)` 형식으로 사용하며, `state`는 현재 상태 값, `setState`는 상태를 갱신하는 함수입니다.
  
```javascript
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

#### __2. useEffect__

* __사이드 이펙트 처리__: `useEffect` 훅은 함수형 컴포넌트에서 사이드 이펙트 를 수행할 수 있게 해줍니다. 예를 들어, 데이터 fetching, 구독(subscription) 설정, DOM 업데이트 등이 있습니다.
* __사용법__: `useEffect(() => { /* 효과 함수 */ }, [dependencies])` 형식으로 사용하며, 첫 번째 매개변수는 효과 함수, 두 번째 매개변수는 의존성 배열입니다. 의존성 배열이 비어 있으면 컴포넌트가 처음 렌더링될 때만 효과 함수가 실행됩니다.

```javascript
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;
  }, [count]); // count가 변경될 때마다 실행

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

#### __3. useContext__

* __컨텍스트 사용__: `useContext` 훅은 컴포넌트 트리에서 __컨텍스트(Context)__ 를 쉽게 사용할 수 있게 해줍니다. 컨텍스트는 전역적으로 데이터를 공유할 때 사용됩니다.
* __사용법__: __`const value = useContext(MyContext)`__ 형식으로 사용하며, __`MyContext`__ 는 __`React.createContext`__ 로 생성한 컨텍스트 객체입니다

```javascript
import React, { useContext } from 'react';

const MyContext = React.createContext();

function MyComponent() {
  const value = useContext(MyContext);
  return <div>{value}</div>;
}

function App() {
  return (
    <MyContext.Provider value="Hello, World!">
      <MyComponent />
    </MyContext.Provider>
  );
}
```

#### __4. useReducer__

* __복잡한 상태 관리__: `useReducer` 훅은 __복잡한 상태 로직__ 을 관리할 때 유용합니다. 주로 Redux와 같은 패턴을 사용할 때 비슷한 방식으로 상태를 관리할 수 있습니다.
* __사용법__: `onst [state, dispatch] = useReducer(reducer, initialState)` 형식으로 사용하며, `reducer`는 상태와 액션을 받아 새로운 상태를 반환하는 함수입니다.

```javascript
import React, { useReducer } from 'react';

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
    </div>
  );
}
```

#### __5. useRef__

* __복잡한 상태 관리__: `useReducer` 훅은 __복잡한 상태 로직__ 을 관리할 때 유용합니다. 주로 Redux와 같은 패턴을 사용할 때 비슷한 방식으로 상태를 관리할 수 있습니다.
* __사용법__: `onst [state, dispatch] = useReducer(reducer, initialState)` 형식으로 사용하며, `reducer`는 상태와 액션을 받아 새로운 상태를 반환하는 함수입니다.

```javascript
import React, { useReducer } from 'react';

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
    </div>
  );
}
```

### __훅의 장점과 단점__

#### __장점__

* __함수형 컴포넌트__: 훅을 사용하면 함수형 컴포넌트에서 클래스형 컴포넌트의 기능을 동일하게 사용할 수 있어 코드가 간결하고 이해하기 쉬워집니다.

* __재사용 가능한 로직__: 커스텀 훅을 만들어 상태 로직을 여러 컴포넌트에서 재사용할 수 있습니다.

* __테스트 용이__: 함수형 컴포넌트는 테스트하기가 더 용이하며, 훅을 사용하면 테스트 코드 작성이 더욱 쉬워집니다.

#### __단점__

* __학습 곡선__: 클래스형 컴포넌트에 익숙한 개발자에게는 훅의 개념과 사용법을 익히는 데 시간이 걸릴 수 있습니다.

* __규칙 준수__: 훅을 사용할 때는 특정 규칙(예: 훅은 컴포넌트의 최상위에서만 호출되어야 함)을 준수해야 하며, 이를 어길 경우 예기치 않은 동작이 발생할 수 있습니다.

* __복잡한 상태 관리__: 복잡한 상태 로직을 훅으로 관리할 때는 가독성이 떨어질 수 있으며, 이를 해결하기 위해 리듀서나 상태 관리 라이브러리를 추가로 사용할 수 있습니다.

### __사용 예시__
아래 예시는 `useState`와 `useEffect` 훅을 사용하여 데이터를 가져오고, 컴포넌트가 처음 마운트될 때만 데이터를 가져오는 간단한 컴포넌트를 보여줍니다.

```javascript
import React, { useState, useEffect } from 'react';

function ExampleComponent() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => setData(data));
  }, []); // 빈 배열이므로 컴포넌트가 처음 마운트될 때만 실행

  return (
    <div>
      {data ? (
        <pre>{JSON.stringify(data, null, 2)}</pre>
      ) : (
        <p>Loading...</p>
      )}
    </div>
  );
}
```

### __훅의 활용 예시__

* __데이터 페칭__: `useEffect` 훅을 사용하여 컴포넌트가 마운트될 때 API 요청을 보내고 데이터를 가져올 수 있습니다.

* __폼 관리__: `useState` 훅을 사용하여 폼의 입력 값을 관리하고, 입력 값이 변경될 때 상태를 업데이트할 수 있습니다.

* __애니메이션__: `useRef` 훅을 사용하여 DOM 요소에 직접 접근하고, 애니메이션을 제어할 수 있습니다.

### 마무리

리액트의 훅(Hooks)은 __함수형 컴포넌트에서 상태와 생명주기 기능을 사용할 수 있게 해주는 강력한 기능__ 입니다. 주요 훅으로는 `useState`, `useEffect`, `useContext`, `useReducer`, `useRef` 등이 있으며, 이를 통해 함수형 컴포넌트에서 다양한 기능을 구현할 수 있습니다. 훅을 잘 이해하고 활용하면, __코드의 간결성과 재사용성 을 높일 수 있으며, 개발 생산성 을 크게 향상__ 시킬 수 있습니다. 그러나 훅을 사용할 때는 특정 규칙을 준수해야 하며, 복잡한 상태 관리를 위해 추가적인 도구가 필요할 수 있습니다.