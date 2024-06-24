---
layout: post
title: 리액트의 useState, useEffect와 useEffect / useLayoutEffect의 차이점
date: 2024-06-24 02:20 +0900
description: REACT
image: ../assets/img/react10.jpg
category: react
tags: reactuseState,useEffect와useEffect/useLayoutEffect의차이점 useState useEffect useEffect useLayoutEffect useEffect,useLayoutEffect의차이점 react
published: true
sitemap: true
---

# REACT
해당 포스팅에서는 REACT의 useState, useEffect와 useEffect / useLayoutEffect의 차이점에 대해 다룹니다.  <br />


## __이번 포스팅 목차__
* REACT의 useState, useEffect와 useEffect / useLayoutEffect의 차이점 <br/>

## __리액트의 함수형 컴포넌트 훅__<br/>
리액트에서 __useState, useEffect, useLayoutEffect__ 는 함수형 컴포넌트에서 중요한 역할을 하는 훅(Hooks)입니다. 각 훅은 특정한 목적과 사용 방법을 가지고 있습니다. 여기서는 이들 훅의 역할과 차이점에 대해 자세히 설명하겠습니다.

### __useState__
__`useState`__ 훅은 함수형 컴포넌트에서 __상태(state)를 관리__ 하기 위해 사용됩니다. `useState`를 호출하면 현재 상태 값과 이 상태를 업데이트하는 함수를 반환합니다.

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

#### __특징__

* __상태 초기값 설정__: `useState`는 초기 상태 값을 인수로 받습니다.

* __상태 업데이트__: 상태를 업데이트할 때는 반환된 함수를 사용하여 새로운 상태 값을 전달합니다.

* __리렌더링__: 상태가 변경되면 __컴포넌트가 다시 렌더링__ 됩니다.

### __useEffect__
__useEffect__ 훅은 함수형 컴포넌트에서 __사이드 이펙트(Side-Effect)를 수행__ 하기 위해 사용됩니다. 이는 컴포넌트가 렌더링된 후에 실행되는 코드 블록을 정의할 수 있게 합니다.

```javascript
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    // 사이드 이펙트 수행: 컴포넌트가 렌더링된 후 실행
    document.title = `You clicked ${count} times`;

    // 정리 함수 반환 (옵션)
    return () => {
      console.log('Clean up');
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

#### __특징__

* __초기 렌더링 및 업데이트 후 실행__: 컴포넌트가 처음 렌더링될 때와 의존성 배열의 값이 변경될 때 실행됩니다.

* __의존성 배열__: 두 번째 인수로 의존성 배열을 전달하여 특정 값이 변경될 때만 이펙트를 재실행하도록 제어할 수 있습니다.

* __정리 함수__: 이펙트 내에서 반환되는 함수는 __컴포넌트가 언마운트되거나__, 의존성 배열의 값이 변경될 때 실행됩니다.

### __useLayoutEffect__
__useLayoutEffect__ 훅은 `useEffect`와 유사하지만, __DOM 업데이트 후__ 그리고 __브라우저가 화면을 그리기 전에__ 동기적으로 실행됩니다. 이는 레이아웃을 읽거나 변경해야 할 때 유용합니다.

```javascript
import React, { useLayoutEffect, useRef } from 'react';

function LayoutEffectExample() {
  const divRef = useRef();

  useLayoutEffect(() => {
    // DOM 변형 작업: 브라우저가 페인트하기 전에 실행됨
    const { height } = divRef.current.getBoundingClientRect();
    console.log('Height:', height);
  });

  return <div ref={divRef}>Hello, world!</div>;
}
```

#### __특징__

* __DOM 업데이트 후, 페인트 전에 실행__: `useLayoutEffect`는 __DOM이 업데이트된 후 브라우저가 화면을 그리기 전에 실행__ 됩니다.

* __동기적 실행__: 이는 브라우저가 레이아웃을 읽거나 수정할 때 블로킹됩니다.

* __정리 함수__: `useLayoutEffect` 내에서 반환되는 정리 함수는 다음 레이아웃 이펙트가 실행되기 전에 실행됩니다.

### __useEffect와 useLayoutEffect의 차이점__

#### __실행 시점__

* __useEffect__: __DOM 업데이트 후 비동기적으로__ 실행되며, 브라우저가 화면을 그리고 나서 실행됩니다. 이로 인해 화면에 보이는 변화가 발생하기 전에 처리되지 않습니다.

* __useLayoutEffect__: __DOM 업데이트 후 동기적__ 으로 실행되며, 브라우저가 화면을 그리기 전에 실행됩니다. 이로 인해 화면에 보이는 변화가 발생하기 전에 처리됩니다.

#### __사용 사례__

* __useEffect__: 네트워크 요청, 구독 설정, 로깅 등 비동기 작업을 수행할 때 주로 사용됩니다.

* __useLayoutEffect__: 레이아웃을 읽거나 변경해야 할 때, 예를 들어, DOM 측정을 하거나 스타일을 동적으로 변경할 때 사용됩니다.

### __마무리__

* __useState__: 함수형 컴포넌트에서 __상태 관리__ 를 위해 사용됩니다.

* __useEffect__: 함수형 컴포넌트에서 __사이드 이펙트를 처리하기 위해 사용__ 되며, 비동기적으로 실행됩니다.

* __useLayoutEffect__: `useEffect`와 유사하지만, __DOM이 업데이트된 후 브라우저가 화면을 그리기 전에 동기적으로 실행__ 됩니다.

각 훅은 특정한 상황에서 유용하며, 올바르게 사용함으로써 리액트 애플리케이션의 기능성과 성능을 최적화할 수 있습니다.