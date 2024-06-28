---
layout: post
title: 리액트의 생명 주기 메서드와 메서드 종류
date: 2024-06-28 10:45 +0900
description: REACT
image: ../assets/img/react14.jpg
category: react
tags: react생명주기메서드와종류 생명주기메서드 메서드 메서드종류 react
published: true
sitemap: true
---

# REACT
해당 포스팅에서는 REACT의 생명 주기 메서드와 메서드 종류에 대해 다룹니다.  <br />


## __이번 포스팅 목차__
* REACT의 생명 주기 메서드와 메서드 종류 <br/>

## __리액트의 생명 주기 메서드와 메서드 종류__<br/>
__생명 주기 메서드와 메서드 종류__ 는 클래스형 컴포넌트에서 컴포넌트가 생성되고, 업데이트되며, 소멸되는 과정을 제어하기 위해 사용됩니다. 생명주기 메서드는 크게 __마운팅(Mounting), 업데이트(Updating), 언마운팅(Unmounting), 에러 처리(Error Handling)__ 단계로 나눌 수 있습니다.

### __클래스형 컴포넌트의 생명주기 메서드 종류와 역활__

1. __마운팅(Mounting)__: 컴포넌트가 처음 DOM에 삽입될 때 발생합니다.

2. __업데이트(Updating)__: 컴포넌트의 상태나 props가 변경될 때 발생합니다.

3. __언마운팅(Unmounting)__: 컴포넌트가 DOM에서 제거될 때 발생합니다.

4. __에러 처리(Error Handling)__: 컴포넌트에서 에러가 발생할 때 호출됩니다.

### __1. 마운팅(Mounting)의 생명주기 함수__

#### __마운팅(Mounting)__
__마운팅__ 단계는 컴포넌트가 처음 DOM에 삽입될 때 발생합니다. 이 과정에서 호출되는 메서드는 다음과 같습니다

##### __constructor(props)__
__컴포넌트가 생성될 때 호출되며 상태(state) 초기화 및 클래스 메서드 바인딩을 수행__ 합니다.

```javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }
}
```

##### __static getDerivedStateFromProps(nextProps, prevState)__
__컴포넌트가 생성되거나 업데이트될 때 호출하며 새로운 props를 기반으로 상태를 업데이트__ 할 수 있습니다. __정적 메서드__ 이며, 인스턴스 메서드가 아닙니다.

```javascript
static getDerivedStateFromProps(nextProps, prevState) {
  if (nextProps.value !== prevState.value) {
    return { value: nextProps.value };
  }
  return null;
}
```

##### __render()__
__필수 메서드로, 컴포넌트의 UI을 정의__ 합니다. 순수 함수로, __상태나 props를 변경하지 않고 렌더링만 수행__ 합니다.

```javascript
render() {
  return <div>{this.state.count}</div>;
}
```

##### __componentDidMount()__
__컴포넌트가 처음 렌더링된 후 호출__ 됩니다. __AJAX 요청, 타이머 설정 등의 작업을 수행__ 할 수 있습니다.

```javascript
componentDidMount() {
  console.log('Component has mounted');
}
```

### __2. 업데이트(Updating)의 생명주기 함수__

#### __업데이트(Updating)__
__업데이트__ 단계는 컴포넌트의 상태나 props가 변경될 때 발생합ㄴ디ㅏ. 이 과정에서 호출되는 메서드는 다음과 같습니다.

##### __static getDerivedStateFromProps(nextProps, prevState)__
마운팅 단계와 동일하게, __새로운 props를 기반으로 상태를 업데이트__ 할 수 있습니다.

##### __shouldComponentUpdate(nextProps, nextState)__
__컨포넌트가 리렌더링될지 여부를 결정__ 하며, __성능 최적화를 위해 사용됩니다. 기본적으로는 true를 반환합니다.__

```javascript
shouldComponentUpdate(nextProps, nextState) {
  return nextState.count !== this.state.count;
}
```

##### __render()__
__상태나 props가 변경될 때마다 호출되어 Ul을 다시 렌더링합니다.__

##### __getSnapshotBeforeUpdate(prevProps, prevState)__
__컴포넌트의 변경된 내용이 DOM에 반영되기 직전에 호출__ 되며, __스크롤 위치 등의 정보를 캡처__ 할 수 있습니다.

```javascript
getSnapshotBeforeUpdate(prevProps, prevState) {
  if (prevProps.list.length < this.props.list.length) {
    return this.listEnd.scrollHeight;
  }
  return null;
}
```

##### __componentDidUpdate(prevProps, prevState, snapshot)__
__컴포넌트의 업데이트가 완료된 후 호출__ 되며, __이전 상태와 새로운 상태를 비교하여 DOM 조작 등의 작업을 수행__ 할 수 있습니다.

```javascript
componentDidUpdate(prevProps, prevState, snapshot) {
  if (snapshot !== null) {
    this.listEnd.scrollTop = this.listEnd.scrollHeight - snapshot;
  }
}
```

### __3. 언마운팅(Unmounting)의 생명주기 함수__

#### __언마운팅(Unmounting)__
__언마운팅__ 단계는 컴포넌트가 DOM에서 제거될 떄 발생합니다. 이 과정에서 호출되는 메서드는 다음과 같습니다.

##### __componentWillUnmount()__
__컴포넌트가 DOM에서 제거되기 전에 호출__ 되며, __타이머 정리, 구독 해제__ 등의 작업을 수행할 수 있습니다.

```javascript
componentWillUnmount() {
  console.log('Component will unmount');
}
```

### __4. 에러 처리(Error Handling)의 생명주기 함수__

#### __에러 처리(Error Handling)__
__에러 처리 단계는 컴포넌트에서 에러가 발생할떄 호출__ 되며, 이 과정에서 호출되는 메서드는 다음과 같습니다.

##### __static getDerivedStateFromError(error)__
컴포넌트에서 __에러가 발생하면 호출__ 되며, __에러 상태를 업데이트__ 할 수 있습니다.

```javascript
componentWillUnmount() {
  console.log('Component will unmount');
}
```

##### __componentDidCatch(error, info)__
컴포넌트에서 __에러가 발생하면 호출__ 되며, __로그 기록등의 작업을 수행__ 할 수 있습니다.

```javascript
componentDidCatch(error, info) {
  console.log('Error:', error);
  console.log('Info:', info);
}
```

### __마무리__
클래스형 컴포넌트의 __생명주기 메서드__ 는 컴포넌트의 __생성, 업데이트, 소멸, 에러 처리 과정에서 호출되는 특정 메서드__ 들로, __각 메서드는 컴포넌트의 특정 상태에서 특정 작업을 수행__ 할 수 있게 합니다. 함수형 컴포넌트에서는 이러한 생명주기 작업을 __훅(Hooks)__ 을 통해 처리할 수 있습니다. 마무리로 생명주기 메서드를 요약해보겠습니다.

* __constructor(props)__: 상태 초기화 및 클래스 메서드 바인딩

* __static getDerivedStateFromProps(nextProps, prevState)__: props 변경 시 상태 업데이트

* __render()__: UI 정의

* __componentDidMount()__: 컴포넌트가 마운트된 후 실행

* __shouldComponentUpdate(nextProps, nextState)__: 컴포넌트가 리렌더링될지 여부 결정

* __getSnapshotBeforeUpdate(prevProps, prevState)__: DOM 업데이트 직전에 호출

* __componentDidUpdate(prevProps, prevState, snapshot)__: 컴포넌트가 업데이트된 후 실행

* __componentWillUnmount()__: 컴포넌트가 언마운트되기 전에 실행

* __static getDerivedStateFromError(error)__: 에러 발생 시 상태 업데이트

* __componentDidCatch(error, info)__: 에러 발생 시 호출

__오늘도 제 블로그에 방문해주셔서 감사합니다!__