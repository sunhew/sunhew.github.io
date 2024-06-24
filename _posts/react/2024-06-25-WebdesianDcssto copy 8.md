---
layout: post
title: 리액트의 Side-Effect
date: 2024-06-23 01:53 +0900
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

## __리액트의 사이드 이펙트(Side-Effect)__<br/>
리액트에서 __사이드 이펙트(Side-Effect)__ 는 컴포넌트의 렌더링과는 별도로 일어나는 연산이나 동작을 말합니다. 이에는 __데이터 가져오기, DOM 조작, 구독 설정 및 해제, 타이머 설정__ 등이 포함됩니다. 리액트 컴포넌트는 주로 순수 함수로 상태를 업데이트하고, UI를 업데이트하기 위해 렌더링을 실행합니다. 그러나 많은 경우 이러한 순수 함수 이외의 부가 작업을 처리해야 할 때 사이드 이펙트가 필요합니다.

### __사이드 이펙트의 종류__

#### __데이터 가져오기 (Fetching Data)__
* API 호출을 통해 서버로부터 데이터를 가져와 상태를 업데이트합니다.

#### __구독 설정 및 해제 (Subscriptions)__
* 웹 소켓 연결, 이벤트 리스너 설정 및 해제 등의 작업을 수행합니다.

#### __타이머 설정 (Timers)__
* `setTimeout`이나 `setInterval`을 사용하여 타이머를 설정하고, 필요시 이를 정리합니다.

#### __DOM 조작 (Direct DOM Manipulation)__
* 리액트가 직접 처리하지 않는 DOM 조작을 수행합니다.

### __사이드 이펙트를 관리하는 방법__

#### __useEffect 훅__
리액트의 `useEffect` 훅은 함수형 컴포넌트 내에서 사이드 이펙트를 수행하는 데 사용됩니다. 이 훅은 __컴포넌트가 렌더링된 후에 실행__ 되며, 특정 조건이 변경될 때 다시 실행됩니다.

```javascript
import React, { useState, useEffect } from 'react';

function ExampleComponent() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    // 브라우저 타이틀을 업데이트하는 사이드 이펙트
    document.title = `You clicked ${count} times`;
    
    // 데이터 가져오기 예시
    async function fetchData() {
      const response = await fetch('https://api.example.com/data');
      const data = await response.json();
      console.log(data);
    }

    fetchData();

    // 컴포넌트 언마운트 시나 count 변경 시 정리 작업 수행
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

#### __useEffect의 동작__

* __초기 렌더링 시 실행__: 컴포넌트가 처음 렌더링될 때 `useEffect`가 실행됩니다.

* __의존성 배열__: 두 번째 인자로 전달되는 배열에 포함된 값이 변경될 때마다 `useEffect`가 다시 실행됩니다.

    * 빈 배열(`[]`)을 전달하면, 이 이펙트는 컴포넌트가 언마운트 될 때만 정리 함수가 실행됩니다.

* __정리 함수__: `useEffect` 내에서 반환되는 함수는 __컴포넌트가 언마운트되거나__, 의존성 배열의 값이 변경될 때 실행됩니다.

```javascript
useEffect(() => {
  // 이펙트 코드

  return () => {
    // 정리 코드
  };
}, [dependencies]);
```

### __사이드 이펙트 사용 시 주의사항__

* __의존성 배열 설정__: 의존성 배열을 정확히 설정하여 불필요한 재실행을 피합니다.

    * 의존성 배열에 누락된 값이 있으면 최신 상태를 반영하지 못할 수 있습니다.

* __정리 작업 수행__: 구독 설정, 타이머, 직접 DOM 조작 등은 컴포넌트가 언마운트될 때 반드시 정리해야 메모리 누수를 방지할 수 있습니다.

* __비동기 작업 처리__: 비동기 작업이 포함된 경우, 컴포넌트가 언마운트된 후에도 작업이 계속될 수 있으므로, 적절히 정리합니다.

    * 이를 위해, 예를 들어, `AbortController`를 사용할 수 있습니다.

### __기타 훅__

#### __useLayoutEffect__

__`useLayoutEffect`__ 는 __`useEffect`__ 와 유사하지만, 모든 __DOM 변형이 실행되고 브라우저가 화면을 그리기 전에 동기적으로 실행__ 됩니다. 이는 레이아웃을 조작하거나 DOM에서 값을 읽어오는 작업에 유용합니다.

```javascript
import React, { useLayoutEffect, useRef } from 'react';

function LayoutEffectExample() {
  const divRef = useRef();

  useLayoutEffect(() => {
    // DOM 변형 작업
    const { height } = divRef.current.getBoundingClientRect();
    console.log('Height:', height);
  });

  return <div ref={divRef}>Hello, world!</div>;
}
```

### __마무리__
리액트 컴포넌트에서 사이드 __이펙트__ 는 렌더링과 별도로 발생하는 중요한 작업들을 처리하는 방법입니다. __`useEffect` 훅__ 은 함수형 컴포넌트에서 이러한 작업을 관리하는 기본 도구이며, 적절한 __의존성 배열__ 설정과 __정리 작업__ 을 통해 효율적이고 안정적인 컴포넌트 작성을 돕습니다. __`useLayoutEffect`__ 는 DOM 조작과 관련된 작업에 유용하며, 각각의 용도를 이해하고 적절하게 사용하는 것이 중요합니다.