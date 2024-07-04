---
layout: post
title: 리액트의 Context API
date: 2024-07-04 18:30 +0900
description: REACT
image: ../assets/img/react16.jpg
category: react
tags: reactContextAPI ContextAPI Context API react
published: true
sitemap: true
---

# REACT
해당 포스팅에서는 REACT의 Context API에 대해 다룹니다.  <br />


## __이번 포스팅 목차__
* REACT의 Context API <br/>

## __리액트의 Context API__<br/>
__Context API__ 컴포넌트 트리 전체에 __데이터를 효율적__ 으로 전달하고 사용할 수 있도록 하는 강력한 기능입니다. 이를 통해 상위 컴포넌트에서 하위 컴포넌트로 __props__ 를 일일이 전달하지 않고도 __전역적으로 데이터를 공유__ 할 수 있습니다.

### 1. __Context API의 개념__
__Context__ 는 리액트 애플리케이션에서 __전역적__ 인 데이터를 관리하고, 트리의 여러 수준에 걸쳐 이 데이터를 전달할 때 사용됩니다. 이는 주로 __테마, 사용자 정보, 인증 상태__ 등의 데이터를 다룰 때 유용합니다.

### 2. __Context API의 주요 구성 요소__
__템플릿 리터럴__ 을 사용하면 문자열 내에서 변수와 표현식을 더 간편하게 삽입할 수 있습니다. 백틱을 사용하여 문자열을 감싸며, ${} 구문을 사용하여 변수를 포함할 수 있습니다.

#### __React.createContext__
새로운 __Context__ 객체를 생성합니다. 이 객체는 `Provider`와 `Consumer` 두 가지 주요 컴포넌트를 포함합니다.

```javascript
const MyContext = React.createContext(defaultValue);
```

#### __Provider__
`Provider` 컴포넌트는 Context를 구독하는 컴포넌트들에게 값을 전달합니다. `Provider`는 `value` prop을 받아 하위 트리에 있는 모든 컴포넌트에 값을 제공합니다.

```javascript
<MyContext.Provider value={/* some value */}>
  {/* components that can access the context */}
</MyContext.Provider>
```

#### __Consumer__
`Consumer` 컴포넌트는 Context의 __값에 접근__ 할 수 있습니다. 함수 컴포넌트의 경우, `useContext` 훅을 사용하여 더 간편하게 접근할 수 있습니다.

```javascript
<MyContext.Consumer>
  {value => /* render something based on the context value */}
</MyContext.Consumer>
```

### 3. __Context API 사용 예시__

#### __Context 생성 및 Provider 사용__

```javascript
import React, { createContext, useState } from 'react';

// 1. Context 생성
const ThemeContext = createContext();

function App() {
  const [theme, setTheme] = useState('light');

  return (
    // 2. Provider 사용, 트리 전체에 값 전달
    <ThemeContext.Provider value={{ theme, setTheme }}>
      <Toolbar />
    </ThemeContext.Provider>
  );
}

function Toolbar() {
  return (
    <div>
      <ThemedButton />
    </div>
  );
}
```

#### __Consumer 사용__
`ThemedButton` 컴포넌트에서 `Consumer`를 사용하여 Context에 접근합니다.

```javascript
function ThemedButton() {
  return (
    <ThemeContext.Consumer>
      {({ theme, setTheme }) => (
        <button
          onClick={() => setTheme(theme === 'light' ? 'dark' : 'light')}
          style={{ background: theme === 'light' ? '#fff' : '#333', color: theme === 'light' ? '#000' : '#fff' }}
        >
          Toggle Theme
        </button>
      )}
    </ThemeContext.Consumer>
  );
}
```

### 4. __useContext 훅 사용__
함수형 컴포넌트에서는 `useContext` 훅을 사용하여 더 간편하게 Context에 접근할 수 있습니다.

```javascript
import React, { useContext } from 'react';

function ThemedButton() {
  const { theme, setTheme } = useContext(ThemeContext);

  return (
    <button
      onClick={() => setTheme(theme === 'light' ? 'dark' : 'light')}
      style={{ background: theme === 'light' ? '#fff' : '#333', color: theme === 'light' ? '#000' : '#fff' }}
    >
      Toggle Theme
    </button>
  );
}
```

### 5. __Context API의 장점과 단점__

#### __장점__
* __전역 상태 관리__: __props drilling__ 없이 전역적으로 상태를 관리하고 전달할 수 있습니다.

* __코드 가독성 향상__: 상위 컴포넌트에서 하위 컴포넌트로 __props를 반복적으로 전달__ 하지 않아도 되므로 코드 가독성이 향상됩니다.

* __유연성__: 여러 Context를 사용하여 다양한 전역 상태를 독립적으로 관리할 수 있습니다.

#### __단점__
* __성능 이슈__: Context 값이 변경되면 이를 구독하는 모든 컴포넌트가 리렌더링됩니다. 따라서 __성능 최적화__ 를 위해 필요에 따라 `React.memo`와 같은 최적화 기법을 사용해야 합니다.

* __구조 복잡성__: 많은 Context를 사용하면 트리 구조가 복잡해질 수 있으며, 관리가 어려울 수 있습니다.

### 6. __고급 사용 사례__

#### __Context의 동적 값 업데이트__
Provider의 value는 동적으로 변경될 수 있으며, 이를 통해 보다 유연한 상태 관리를 할 수 있습니다.

```javascript
const ThemeContext = createContext();

function App() {
  const [theme, setTheme] = useState('light');

  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      <Toolbar />
    </ThemeContext.Provider>
  );
}

function Toolbar() {
  return (
    <div>
      <ThemedButton />
    </div>
  );
}

function ThemedButton() {
  const { theme, setTheme } = useContext(ThemeContext);

  return (
    <button
      onClick={() => setTheme(theme === 'light' ? 'dark' : 'light')}
      style={{ background: theme === 'light' ? '#fff' : '#333', color: theme === 'light' ? '#000' : '#fff' }}
    >
      Toggle Theme
    </button>
  );
}
```

### __마무리__
리액트의 __Context API__ 는 __전역적 상태 관리와 데이터 전달__ 을 효율적으로 할 수 있는 강력한 도구입니다. 이를 통해 __props drilling__ 문제를 해결하고, 전역적으로 데이터를 공유할 수 있습니다. 하지만 성능 이슈와 구조 복잡성을 고려하여 적절히 사용하는 것이 중요합니다. `useContext` 훅을 통해 함수형 컴포넌트에서도 쉽게 Context에 접근할 수 있으며, Context API를 올바르게 사용하면 리액트 애플리케이션의 코드 가독성과 유지보수성을 크게 향상시킬 수 있습니다.