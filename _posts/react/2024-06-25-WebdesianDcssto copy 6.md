---
layout: post
title: 리액트의 상태 관리 라이브러리와 필요성
date: 2024-06-21 00:37 +0900
description: REACT
image: ../assets/img/react07.jpg
category: react
tags: react상태관리라이브러리 상태관리라이브러리 라이브러리 react
published: true
sitemap: true
---

# REACT
해당 포스팅에서는 REACT의 상태 관리 라이브러리에 대해 다룹니다.  <br />


## __이번 포스팅 목차__
* REACT의 상태 관리 라이브러리와 필요성 <br/>

## __리액트 훅의 주요 특징__<br/>
리액트에서 __상태 관리는 컴포넌트 간의 데이터와 UI 상태를 효과적으로 관리__ 하기 위해 중요합니다. __복잡한 애플리케이션에서는 상태가 여러 컴포넌트 간에 공유될 필요가 있으며, 상태 변경 시 효율적으로 업데이트__ 해야 합니다. 이러한 요구 사항을 충족하기 위해 다양한 상태 관리 라이브러리가 등장했으며, 리액트 애플리케이션에서 상태 관리 라이브러리는 애플리케이션의 규모와 복잡성에 따라 선택됩니다.

### __리액트 라이브러리__

#### __상태 관리 라이브러리가 필요한 이유__

* __상태의 복잡성 증가__: 애플리케이션이 커질수록 상태를 관리하고 업데이트하는 것이 __복잡해집니다.__

* __컴포넌트 간 상태 공유__: 여러 컴포넌트가 동일한 상태를 공유하고 있을 때, 이를 __효율적으로 관리__ 해야 합니다.

* __성능 최적화__: 불필요한 렌더링을 방지하고 __성능을 최적화__ 할 필요가 있습니다.

* __코드 구조화__: 상태 관리 로직을 일관되게 __구조화하여 코드 가독성__ 을 높이고 __유지 보수__ 를 용이하게 합니다.

#### __주요 상태 관리 라이브러리__

##### __Redux__
Redux는 리액트 애플리케이션에서 상태를 __중앙 집중식으로 관리__ 하는 가장 널리 사용되는 라이브러리 중 하나입니다. 상태를 __단일 스토어__ 에서 관리하며, 액션(action)과 리듀서(reducer)를 사용하여 상태를 업데이트합니다.

###### __장점__
* 상태의 __중앙 집중식 관리__

* 상태 변화 __추적 및 디버깅 용이__

* __미들웨어__ 를 통한 확장성 (예: Redux Thunk, Redux Saga)

###### __단점__
* __보일러플레이트 코드__ 가 많음

* 작은 프로젝트에서는 __오버헤드__ 가 있을 수 있음
  
```javascript
import { createStore } from 'redux';

// 리듀서
function counterReducer(state = { count: 0 }, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      return state;
  }
}

// 스토어 생성
const store = createStore(counterReducer);

// 액션 디스패치
store.dispatch({ type: 'increment' });
console.log(store.getState()); // { count: 1 }
```

##### __MobX__
MobX는 상태를 자동으로 __추적__ 하고, 상태가 변경될 때 자동으로 __UI를 업데이트__ 하는 __반응형 상태 관리__ 라이브러리입니다. __객체 지향적__ 접근을 사용하며, 상태를 __관찰 가능한(observable)__ 객체로 만들고 이를 **관찰(observe)**합니다.

###### __장점__
* 간결하고 __직관적인 API__

* __자동 상태 추적__ 및 업데이트

* 적은 __보일러플레이트 코드__

###### __단점__
* 복잡한 프로젝트에서는 __성능 최적화__ 를 신경 써야 함

* Redux만큼의 __커뮤니티__ 및 __생태계 지원 부족__
  
```javascript
import { observable, action } from 'mobx';

class CounterStore {
  @observable count = 0;

  @action.bound
  increment() {
    this.count++;
  }

  @action.bound
  decrement() {
    this.count--;
  }
}

const counterStore = new CounterStore();
```

##### __Context API__
리액트의 __Context API__ 는 컴포넌트 트리 전체에 걸쳐 __데이터를 전달__ 할 수 있도록 도와줍니다. Redux나 MobX에 비해 가벼운 상태 관리를 제공합니다.

###### __장점__
* 간단하고 __내장된 API__

* __보일러플레이트 코드__ 가 적음

* 작은 프로젝트에 __적합__

###### __단점__
* 상태가 많아지면 __복잡해질 수 있음__

* __성능 최적화__ 를 신경 써야 함
  
```javascript
import React, { createContext, useContext, useState } from 'react';

const CounterContext = createContext();

function CounterProvider({ children }) {
  const [count, setCount] = useState(0);

  return (
    <CounterContext.Provider value={{ count, setCount }}>
      {children}
    </CounterContext.Provider>
  );
}

function useCounter() {
  return useContext(CounterContext);
}
```
##### __Context API__
리액트의 __Context API__ 는 컴포넌트 트리 전체에 걸쳐 __데이터를 전달__ 할 수 있도록 도와줍니다. Redux나 MobX에 비해 가벼운 상태 관리를 제공합니다.

###### __장점__
* 간단하고 __내장된 API__

* __보일러플레이트 코드__ 가 적음

* 작은 프로젝트에 __적합__

###### __단점__
* 상태가 많아지면 __복잡해질 수 있음__

* __성능 최적화__ 를 신경 써야 함
  
```javascript
import React, { createContext, useContext, useState } from 'react';

const CounterContext = createContext();

function CounterProvider({ children }) {
  const [count, setCount] = useState(0);

  return (
    <CounterContext.Provider value={{ count, setCount }}>
      {children}
    </CounterContext.Provider>
  );
}

function useCounter() {
  return useContext(CounterContext);
}
```

##### __Recoil__
Recoil은 페이스북에서 개발한 리액트 상태 관리 라이브러리로, __글로벌 상태__ 를 다루기 쉽게 만들어줍니다. Recoil은 **atom(상태의 단위)**과 __selector(파생 상태 및 비동기 로직)__ 개념을 사용합니다.

###### __장점__
* 간결한 __API__

* __비동기 상태 관리 용이__

* 리액트 __Concurrent Mode__ 와 잘 __호환됨__

###### __단점__
* 비교적 __새로운 라이브러리__ 로, 생태계가 작음

* 사용 방법에 익숙해지기 위해 __학습 필요__
  
```javascript
import { atom, selector, useRecoilState, useRecoilValue } from 'recoil';

const countState = atom({
  key: 'countState',
  default: 0,
});

const doubledCountState = selector({
  key: 'doubledCountState',
  get: ({ get }) => {
    const count = get(countState);
    return count * 2;
  },
});

function Counter() {
  const [count, setCount] = useRecoilState(countState);
  const doubledCount = useRecoilValue(doubledCountState);

  return (
    <div>
      <p>Count: {count}</p>
      <p>Doubled Count: {doubledCount}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

#### __마무리__

리액트 애플리케이션에서 상태 관리 라이브러리는 애플리케이션의 규모와 복잡성에 따라 선택됩니다. 작은 애플리케이션에서는 __Context API__ 나 기본적인 __`useState`__, __`useReducer`__ 로 충분할 수 있지만, 큰 애플리케이션에서는 __Redux, MobX, Recoil__ 과 같은 라이브러리가 필요할 수 있습니다. 각 라이브러리는 고유한 장점과 단점을 가지고 있으므로, 프로젝트의 요구 사항에 따라 적절한 라이브러리를 선택하는 것이 중요합니다.