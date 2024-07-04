---
layout: post
title: 리액트의 state vs props
date: 2024-07-04 18:30 +0900
description: REACT
image: ../assets/img/react18.jpg
category: react
tags: reactstatevsprops statevsprops state props react
published: true
sitemap: true
---

# REACT
해당 포스팅에서는 REACT의 state vs props에 대해 다룹니다.  <br />


## __이번 포스팅 목차__
* REACT의 state vs props <br/>

## __리액트의 state vs props__<br/>
__state와 props__ 컴포넌트 간 데이터 관리의 두 가지 주요 개념입니다. 이 두 개념은 리액트 애플리케이션의 구조와 데이터 흐름을 이해하는 데 있어 핵심적인 역할을 합니다. __state__ 와 __props__ 의 차이점, 사용 방법, 그리고 각 개념의 특성을 자세히 설명하겠습니다.

### 1. __Props (Properties)__
__Props__ 는 컴포넌트 간에 데이터를 전달하기 위한 __읽기 전용__ 속성입니다. 부모 컴포넌트가 자식 컴포넌트에 데이터를 전달할 때 사용되며, 자식 컴포넌트는 이를 받아 렌더링합니다. __Props는 변경할 수 없으며__ 컴포넌트 외부에서 전달됩니다.

#### __주요 특징__

* __읽기 전용__: 자식 컴포넌트는 props를 수정할 수 없습니다.

* __부모 컴포넌트에서 전달__: 부모 컴포넌트가 자식 컴포넌트에 데이터를 전달합니다.

* __동적 데이터 전달__: 부모 컴포넌트의 상태나 props가 변경되면 자식 컴포넌트에 전달된 props도 업데이트됩니다.

```javascript
import React from 'react';

function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

function App() {
  return <Greeting name="Alice" />;
}

export default App;
```

### 2. __State__
__State__ 는 컴포넌트 내부에서 관리되는 __동적인 데이터__ 입니다. 컴포넌트의 상태는 컴포넌트 자체에서 초기화되고 변경될 수 있으며, 상태가 변경되면 컴포넌트는 자동으로 다시 렌더링됩니다. __State는 변경 가능한 데이터__ 로, 컴포넌트의 동작과 렌더링을 제어합니다.

#### __주요 특징__

* __내부 관리__: 상태는 컴포넌트 자체에서 관리되고 변경될 수 있습니다.

* __동적 데이터__: 상태는 사용자 상호작용, 네트워크 요청 등의 결과로 변경될 수 있습니다.

* __리렌더링__: 상태가 변경되면 컴포넌트는 자동으로 다시 렌더링됩니다.

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

### __State vs Props: 차이점__

#### __데이터 소유권 및 변경 가능성__

* __Props__: 부모 컴포넌트가 소유하고 관리하며, 자식 컴포넌트에서는 __읽기 전용__ 입니다.

* __State__: 컴포넌트 자체가 소유하고 관리하며, 컴포넌트 내부에서 __변경 가능__ 합니다.

#### __용도__

* __Props__: 컴포넌트 간 __데이터 전달__ 및 __구성__ 을 위해 사용됩니다.

* __State__: 컴포넌트의 __동적 데이터__ 를 관리하고, __사용자 상호작용__ 이나 __네트워크 요청__ 등의 결과를 반영합니다.

#### __리렌더링 트리거__

* __Props__: 부모 컴포넌트의 상태나 props가 변경되어 자식 컴포넌트에 새로운 props가 전달되면 리렌더링됩니다.

* __State__: 컴포넌트의 상태가 변경되면 해당 컴포넌트는 자동으로 리렌더링됩니다.

### __결합 사용 예시__
종종 __props__ 와 __state__ 는 함께 사용되어 컴포넌트 간 데이터를 효율적으로 관리합니다. 부모 컴포넌트는 상태를 관리하고, 이 상태를 자식 컴포넌트에 props로 전달하여 자식 컴포넌트가 이를 렌더링합니다.

```javascript
import React, { useState } from 'react';

function ChildComponent(props) {
  return <p>{props.message}</p>;
}

function ParentComponent() {
  const [message, setMessage] = useState('Hello from Parent!');

  return (
    <div>
      <ChildComponent message={message} />
      <button onClick={() => setMessage('Message Updated!')}>Update Message</button>
    </div>
  );
}

export default ParentComponent;
```

### __마무리__
리액트의 __state__ 와 __props__ 는 각각 __내부 상태 관리__ 와 __컴포넌트 간 데이터 전달__ 을 담당하는 중요한 개념입니다. __Props__ 는 부모 컴포넌트에서 자식 컴포넌트로 전달되는 __읽기 전용 데이터__ 이며, __State__ 는 컴포넌트 내부에서 __관리되고 변경__ 될 수 있는 __동적 데이터__ 입니다. 이 두 개념을 이해하고 적절히 활용하면 리액트 애플리케이션의 데이터 __흐름과 구조__ 를 효율적으로 관리할 수 있습니다.