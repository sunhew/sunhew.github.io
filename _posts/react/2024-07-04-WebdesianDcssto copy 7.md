---
layout: post
title: 왜 state를 직접 바꾸지 않고 useState를 사용해야 하나?
date: 2024-07-04 19:22 +0900
description: REACT
image: ../assets/img/react19.jpg
category: react
tags: react
published: true
sitemap: true
---

# REACT
해당 포스팅에서는 왜 state를 직접 바꾸지 않고 useState를 사용해야 하는지에 대해 다룹니다.  <br />


## __이번 포스팅 목차__
* REACT의 state vs props <br/>

## __리액트의 왜 state를 직접 바꾸지 않고 useState를 사용해야 하지?__<br/>
리액트에서 __state__ 를 직접 바꾸지 않고 `useState` 훅을 사용해야 하는 이유는 리액트의 __상태 관리와 렌더링 메커니즘__ 에 깊이 관련되어 있습니다. 리액트는 상태 관리와 렌더링을 통해 UI를 업데이트하며, 이러한 프로세스를 효율적으로 관리하기 위해 상태 변경을 추적할 수 있는 방법이 필요합니다. `useState` 훅을 사용해야 하는 이유와 이를 직접 변경하는 것이 왜 문제가 되는지 자세히 설명하겠습니다.

### 1. __리액트의 상태 관리 메커니즘__
리액트에서 __상태__ 는 컴포넌트가 렌더링하는 데 필요한 데이터를 저장하는 방법입니다. `useState` 훅은 상태 변수를 선언하고, 해당 상태 변수를 업데이트하는 함수(`setState`)를 반환합니다. 이 함수는 __상태 변경을 리액트에게 알리고__, 변경된 상태를 기반으로 컴포넌트를 다시 렌더링합니다.

```javascript
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}

export default Counter;
```

### 2. __직접 상태를 변경하지 말아야 하는 이유__

#### __리액트의 상태 추적__
리액트는 __상태 변경__ 을 통해 컴포넌트가 어떻게 업데이트되어야 하는지 추적합니다. __`useState`__ 의 상태 업데이트 함수(`setState`)를 사용하면 리액트는 상태가 변경되었음을 인지하고, 변경된 상태에 따라 컴포넌트를 다시 렌더링합니다.

##### __직접 상태 변경했을때의 잘못된 방법 예시__
아래 예시에서 `count`를 직접 변경해도 리액트는 상태가 변경되었음을 인지하지 못하므로, 컴포넌트를 다시 렌더링하지 않습니다.

```javascript
function Counter() {
  const [count, setCount] = useState(0);

  function increment() {
    count = count + 1; // 직접 상태 변경 (잘못된 방법)
  }

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={increment}>Click me</button>
    </div>
  );
}
```

#### __리렌더링 트리거__
__useState__ 의 상태 업데이트 함수(`setState`)를 사용하면 리액트는 자동으로 __컴포넌트를 다시 렌더링__ 합니다. 직접 상태를 변경하면 리렌더링이 발생하지 않아 UI가 상태 변경을 반영하지 못합니다.

##### __올바른 상태 업데이트 예시 코드__

```javascript
function Counter() {
  const [count, setCount] = useState(0);

  function increment() {
    setCount(count + 1); // 상태 업데이트 함수 사용 (올바른 방법)
  }

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={increment}>Click me</button>
    </div>
  );
}
```

### 3. __상태 일관성 유지__
리액트는 __상태 일관성__ 을 보장하기 위해 특정 규칙을 따릅니다. __useState__ 를 사용하면 상태 변경이 예측 가능하고 일관되게 처리됩니다. 직접 상태를 변경하면 예기치 않은 동작이 발생할 수 있습니다.

### 4. __배치 업데이트__
리액트는 성능 최적화를 위해 여러 상태 업데이트를 __배치 처리__ 할 수 있습니다. __`useState`__ 를 사용하면 리액트는 여러 상태 업데이트를 한 번의 렌더링으로 처리할 수 있지만, 직접 상태를 변경하면 이러한 최적화를 활용할 수 없습니다.

##### __배치 업데이트 예시 코드__
아래 예시에서 `count`를 직접 변경해도 리액트는 상태가 변경되었음을 인지하지 못하므로, 컴포넌트를 다시 렌더링하지 않습니다.

```javascript
function Counter() {
  const [count, setCount] = useState(0);

  function increment() {
    setCount(prevCount => prevCount + 1);
    setCount(prevCount => prevCount + 1); // 배치 업데이트
  }

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={increment}>Click me</button>
    </div>
  );
}
```

### __마무리__
리액트에서 __state__ 를 직접 변경하지 않고 `useState` 훅을 사용하는 것은 리액트의 __상태 관리와 렌더링 메커니즘__ 을 준수하는 중요한 원칙입니다. __`useState`__ 를 사용하면 리액트가 상태 변경을 추적하고, 필요한 경우 컴포넌트를 다시 렌더링하여 __UI의 일관성을 유지__ 할 수 있습니다. 상태를 직접 변경하는 것은 리액트의 상태 관리 메커니즘을 우회하는 것이며, 이는 __예기치 않은 동작__ 과 __성능 문제__ 를 초래할 수 있습니다. 따라서 항상 __`useState`__ 와 같은 상태 관리 함수를 사용하여 상태를 업데이트하는 것이 권장됩니다.