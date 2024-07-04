---
layout: post
title: 리액트의 리액트 훅
date: 2024-07-04 18:30 +0900
description: REACT
image: ../assets/img/react17.jpg
category: react
tags: react리액트훅 리액트훅 리액트 훅 react
published: true
sitemap: true
---

# REACT
해당 포스팅에서는 REACT의 리액트 훅에 대해 다룹니다.  <br />


## __이번 포스팅 목차__
* REACT의 리액트 훅 <br/>

## __리액트의 리액트 훅__<br/>
__리액트 훅__ 는 함수형 컴포넌트에서 상태 관리와 사이드 이펙트 처리를 가능하게 하는 강력한 기능입니다. 훅은 리액트 16.8 버전에서 도입되었으며, 클래스형 컴포넌트의 생명주기 메서드와 상태 관리를 함수형 컴포넌트에서도 할 수 있도록 합니다. 주요 리액트 훅과 그 사용 방법을 자세히 설명하겠습니다.

### 1. __useState__
`useState` 훅은 함수형 컴포넌트에서 __상태(state)__ 를 관리하기 위해 사용됩니다. `useState`를 호출하면 현재 상태 값과 이 상태를 업데이트하는 함수를 반환합니다.

```javascript
import React, { useState } from 'react';

function Counter() {
  // count는 상태 변수, setCount는 상태를 업데이트하는 함수
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

### 2. __useEffect__
`useEffect` 훅은 함수형 컴포넌트에서 __사이드 이펙트(Side-Effect)__ 를 처리하기 위해 사용됩니다. 이 훅은 컴포넌트가 렌더링된 후에 실행되며, 특정 조건이 변경될 때 다시 실행될 수 있습니다.

```javascript
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    // 컴포넌트가 마운트된 후와 count가 변경될 때 실행됨
    document.title = `You clicked ${count} times`;

    // 클린업 함수 반환 (옵션)
    return () => {
      console.log('Cleanup');
    };
  }, [count]); // count가 변경될 때마다 이펙트 실행

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

### 3. __useContext__
`useContext` 훅은 리액트의 __Context API__ 를 더 간편하게 사용할 수 있도록 합니다. 이 훅을 사용하면 Context의 값을 직접적으로 가져올 수 있습니다.

```javascript
import React, { useContext } from 'react';

const ThemeContext = React.createContext('light');

function ThemedButton() {
  const theme = useContext(ThemeContext);
  return <button style={{ background: theme === 'light' ? '#fff' : '#333' }}>Themed Button</button>;
}
```

### 4. __useReducer__
`useReducer` 훅은 상태 관리 로직이 복잡할 때 사용됩니다. 이는 Redux와 같은 상태 관리 라이브러리와 유사한 패턴을 제공합니다.

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

### 5. __useRef__
`useRef` 훅은 DOM 요소에 접근하거나 컴포넌트의 상태를 저장하는 데 사용됩니다. 이는 클래스형 컴포넌트에서 `createRef` 와 유사한 역할을 합니다.

```javascript
import React, { useRef, useEffect } from 'react';

function FocusInput() {
  const inputEl = useRef(null);

  useEffect(() => {
    inputEl.current.focus();
  }, []);

  return <input ref={inputEl} type="text" />;
}
```

### 6. __useMemo__
`useMemo` 훅은 __성능 최적화__ 를 위해 사용됩니다. 이는 특정 계산을 메모이제이션하여 불필요한 재계산을 방지합니다.

```javascript
import React, { useMemo, useState } from 'react';

function ExpensiveComponent({ num }) {
  const calculate = (num) => {
    console.log('Calculating...');
    return num * 2;
  };

  const memoizedValue = useMemo(() => calculate(num), [num]);

  return <div>{memoizedValue}</div>;
}
```

### 7. __useCallback__
`useCallback` 훅은 __성능 최적화__ 를 위해 콜백 함수를 메모이제이션합니다. 이는 컴포넌트가 불필요하게 재생성되는 것을 방지합니다.

```javascript
import React, { useCallback, useState } from 'react';

function Parent() {
  const [count, setCount] = useState(0);

  const increment = useCallback(() => {
    setCount(count + 1);
  }, [count]);

  return <Child onClick={increment} />;
}

function Child({ onClick }) {
  console.log('Child rendered');
  return <button onClick={onClick}>Increment</button>;
}
```

### 8. __useImperativeHandle__
`useImperativeHandle` 훅은 부모 컴포넌트가 자식 컴포넌트의 내부 메서드에 접근할 수 있도록 합니다.

```javascript
import React, { useRef, useImperativeHandle, forwardRef } from 'react';

const CustomInput = forwardRef((props, ref) => {
  useImperativeHandle(ref, () => ({
    focus: () => {
      inputRef.current.focus();
    }
  }));

  const inputRef = useRef();
  return <input ref={inputRef} />;
});

function Parent() {
  const inputRef = useRef();

  return (
    <div>
      <CustomInput ref={inputRef} />
      <button onClick={() => inputRef.current.focus()}>Focus Input</button>
    </div>
  );
}
```

### 9. __useLayoutEffect__
`useLayoutEffect` 훅은 __DOM이 업데이트된 후__ 에 동기적으로 실행됩니다. 이는 브라우저가 화면을 그리기 전에 실행되어야 할 경우에 유용합니다.

```javascript
import React, { useLayoutEffect, useRef } from 'react';

function LayoutEffectComponent() {
  const divRef = useRef();

  useLayoutEffect(() => {
    console.log(divRef.current.getBoundingClientRect());
  });

  return <div ref={divRef}>Layout Effect Example</div>;
}
```

### __마무리__
리액트의 __리액트 훅(Hooks)__ 는 함수형 컴포넌트에서 상태 관리와 사이드 이펙트 처리를 효율적으로 할 수 있도록 합니다. 주요 훅에는 `useState`, `useEffect`, `useContext`, `useReducer`, `useRef`, `useMemo`, `useCallback`, `useImperativeHandle`, `useLayoutEffect` 등이 있습니다. 이들 훅을 올바르게 사용하면 함수형 컴포넌트에서도 클래스형 컴포넌트와 동일한 수준의 기능과 성능을 구현할 수 있습니다.