---
layout: post
title: REACT의 async-await와 Promise의 차이
date: 2024-07-04 10:13 +0900
description: REACT
image: ../assets/img/react21.jpg
category: react
tags: reactasync-await와Promise의차이 async-await와Promise의차이 async-await Promise react
published: true
sitemap: true
---

# REACT
해당 포스팅에서는 REACT의 async-await와 Promise의 차이에 대해 다룹니다.  <br />


## __이번 포스팅 목차__
* REACT의 async-await와 Promise의 차이 <br/>

## __리액트의 async-await와 Promise의 차이__<br/>
리액트에서 __비동기 작업__ 을 처리할 때 __Promise__ 와 __async-await__ 는 중요한 역할을 합니다. 이 두 가지 방법은 비동기 코드를 다루는 방식을 단순화하고, 코드를 더 가독성 있게 만들어 줍니다. __Promise__ 와 __async-await__ 의 차이점, 사용 방법, 그리고 각각의 특성을 자세히 설명하겠습니다.

### 1. __Promise__
__Promise__ 는 비동기 작업의 최종 완료 또는 실패를 나타내는 자바스크립트 객체입니다. 이는 미래에 완료될 작업을 다루기 위해 사용됩니다.

#### __주요 특징__ 

##### __상태__ 
Promise는 세 가지 상태를 가질 수 있습니다.

* __Pending__: 초기 상태, 아직 완료되지 않음.

* __Fulfilled__: 작업이 성공적으로 완료됨.

* __Rejected__: 작업이 실패함.

##### __then 및 catch__ 
Promise 객체는 `.then()` 및 `.catch()` 메서드를 통해 완료 및 오류 처리 콜백을 등록할 수 있습니다.

##### __사용 예시__
아래 예시에서 `numbers` 배열의 각 항목에 대해 __고유한 `key`__ 를 제공하여 리액트가 각 항목을 고유하게 식별할 수 있도록 합니다.

```javascript
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('Success!');
  }, 1000);
});

promise
  .then(result => {
    console.log(result); // 'Success!'
  })
  .catch(error => {
    console.error(error);
  });
```

### 2. __Async-Await__
__Async-Await__ 는 비동기 작업을 더 __직관적__ 으로 작성할 수 있게 해주는 ES8(ECMAScript 2017) 문법입니다. __async-await__ 는 __Promise__ 를 기반으로 하며, 비동기 작업을 __동기식 코드처럼__ 작성할 수 있게 합니다.

#### __주요 특징__ 

* __async 함수__: `async` 키워드를 함수 앞에 붙여 해당 함수가 비동기 함수를 반환하도록 합니다.

* __await__: `await` 키워드는 __Promise__ 가 해결될 때까지 함수 실행을 일시 중단하고, 해결된 값을 반환합니다. `await`는 __async 함수 내에서만__ 사용할 수 있습니다.

##### __사용 예시__

```javascript
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Error:', error);
  }
}

fetchData();
```

## __Promise와 Async-Await의 차이점__

### 1. __코드 가독성__ 

#### __Promise__
콜백 지옥(callback hell)을 피하기 위해 `.then()` 체인을 사용하지만, 복잡한 비동기 로직에서는 가독성이 떨어질 수 있습니다.

```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => {
    console.log(data);
  })
  .catch(error => {
    console.error('Error:', error);
  });
```

#### __async-await__
비동기 코드를 동기식 코드처럼 작성할 수 있어 가독성이 높아집니다.

```javascript
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Error:', error);
  }
}

fetchData();
```

### 2. __에러 처리__ 

#### __Promise__
`.catch()`를 사용하여 에러를 처리합니다.

```javascript
promise
  .then(result => {
    console.log(result);
  })
  .catch(error => {
    console.error(error);
  });
```

#### __async-await__
`try-catch` 블록을 사용하여 에러를 처리합니다.

```javascript
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Error:', error);
  }
}
```

### 2. __에러 처리__ 

#### __Promise__
`.catch()`를 사용하여 에러를 처리합니다.

```javascript
promise
  .then(result => {
    console.log(result);
  })
  .catch(error => {
    console.error(error);
  });
```

#### __async-await__
`.catch()`를 사용하여 에러를 처리합니다.

```javascript
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Error:', error);
  }
}
```

### 3. __복잡한 비동기 흐름 관리__ 

#### __Promise__
여러 비동기 작업을 처리할 때 `.then()` 체인이 복잡해질 수 있습니다.

```javascript
fetch('https://api.example.com/data1')
  .then(response1 => {
    return fetch('https://api.example.com/data2');
  })
  .then(response2 => {
    return fetch('https://api.example.com/data3');
  })
  .then(response3 => {
    console.log('All data fetched');
  })
  .catch(error => {
    console.error('Error:', error);
  });
```

#### __async-await__
비동기 작업의 순차적 흐름을 더 직관적으로 작성할 수 있습니다.

```javascript
async function fetchMultipleData() {
  try {
    const response1 = await fetch('https://api.example.com/data1');
    const response2 = await fetch('https://api.example.com/data2');
    const response3 = await fetch('https://api.example.com/data3');
    console.log('All data fetched');
  } catch (error) {
    console.error('Error:', error);
  }
}

fetchMultipleData();
```

### __마무리__
리액트에서 __Promise__ 와 __async-await__ 는 비동기 작업을 처리하는 두 가지 주요 방법입니다. __Promise__ 는 비동기 작업의 결과를 나타내는 객체이며, `.then()`과 `.catch()` 메서드를 통해 작업 완료와 에러 처리를 다룹니다. 반면, __async-await__ 는 __Promise__ 를 기반으로 하며, 비동기 코드를 동기식 코드처럼 작성할 수 있게 해줍니다. __async-await__ 는 가독성이 높고, 복잡한 비동기 로직을 더 쉽게 작성할 수 있게 해줍니다. 각각의 방법은 상황에 따라 적절히 사용해야 하며, __async-await__ 는 특히 코드의 가독성을 중시하는 경우에 유용합니다.