---
layout: post
title: REACT의 key props를 사용하는 이유
date: 2024-07-04 19:53 +0900
description: REACT
image: ../assets/img/react20.jpg
category: react
tags: reactkeyprops를사용하는이유 key props react
published: true
sitemap: true
---

# REACT
해당 포스팅에서는 REACT의 key props를 사용하는 이유에 대해 다룹니다.  <br />


## __이번 포스팅 목차__
* REACT의 key props를 사용하는 이유 <br/>

## __리액트의 key props를 사용하는 이유__<br/>
리액트에서 __`key` props__ 는 __리스트__ 나 __동적인 컴포넌트 배열__ 을 렌더링할 때 사용됩니다. 이는 각 컴포넌트를 __고유하게 식별__ 할 수 있게 하여 __효율적인 업데이트__ 를 가능하게 합니다. __`key` props__ 를 사용하는 이유와 그 중요성에 대해 자세히 설명하겠습니다.

### 1. __Key props의 역할__
리액트는 __가상 DOM(Virtual DOM)__ 을 사용하여 실제 DOM 조작을 최소화하고 성능을 최적화합니다. __`key` props__ 는 리액트가 __어떤 항목이 변경, 추가 또는 제거되었는지 효율적으로 파악__ 할 수 있도록 도와줍니다. 이는 리액트의 __재조정(reconciliation)__ 과정에서 중요한 역할을 합니다.

### 2. __Key props가 필요한 이유__ 

* __고유한 식별자 제공__: __`key` props__ 는 각 컴포넌트를 __고유하게 식별__ 합니다. 이를 통해 리액트는 리스트 내에서 __어떤 항목이 변경되었는지 정확하게 추적__ 할 수 있습니다. 

* __효율적인 업데이트__: __`key` props__ 를 사용하면 리액트는 항목의 변경 사항을 더 __효율적으로 감지__ 하고 __필요한 부분만 업데이트__ 합니다. 이는 불필요한 재렌더링을 방지하여 성능을 향상시킵니다.

* __정렬과 재정렬__: 리스트 항목이 __정렬되거나 재정렬__ 될 때 __`key` props__ 는 리액트가 항목의 위치 변경을 정확하게 인식하고 처리할 수 있도록 합니다.

### 3. __Key props 사용 예시__
리스트를 렌더링할 때 __`key` props__ 를 사용하는 예시를 살펴보겠습니다.

#### __기본 사용 예시__
아래 예시에서 `numbers` 배열의 각 항목에 대해 __고유한 `key`__ 를 제공하여 리액트가 각 항목을 고유하게 식별할 수 있도록 합니다.

```javascript
import React from 'react';

function ListItem({ value }) {
  return <li>{value}</li>;
}

function NumberList({ numbers }) {
  const listItems = numbers.map((number) =>
    <ListItem key={number.toString()} value={number} />
  );
  return (
    <ul>
      {listItems}
    </ul>
  );
}

export default NumberList;
```

#### __객체 배열 사용 예시__
아래 예시에서 객체 배열을 렌더링하며, 각 객체의 `id` 속성을 __`key`__ 로 사용합니다. 객체의 `id`는 일반적으로 고유하기 때문에, 적절한 __`key`__ 로 사용될 수 있습니다.

```javascript
import React from 'react';

function ListItem({ item }) {
  return <li>{item.name}</li>;
}

function ItemList({ items }) {
  const listItems = items.map((item) =>
    <ListItem key={item.id} item={item} />
  );
  return (
    <ul>
      {listItems}
    </ul>
  );
}

export default ItemList;
```

### 4. __잘못된 Key 사용 예시__

#### __인덱스를 Key로 사용하는 경우__
인덱스를 __`key`__ 로 사용하는 것은 권장되지 않습니다. 리스트 항목이 재정렬되거나 삽입/삭제될 때 인덱스는 변할 수 있으며, 이는 리액트의 효율적인 업데이트를 방해할 수 있습니다.

```javascript
function ListItem({ value }) {
  return <li>{value}</li>;
}

function NumberList({ numbers }) {
  const listItems = numbers.map((number, index) =>
    <ListItem key={index} value={number} />
  );
  return (
    <ul>
      {listItems}
    </ul>
  );
}
```

### 5. __Key props의 중요한 점__ 

* __고유해야 함__: __`key`__ 는 같은 리스트 내에서 고유해야 합니다. 중복된 __`key`__ 는 리액트가 항목을 제대로 식별하지 못하게 합니다. 

* __불변성__: __`key`__ 는 항목이 변경되거나 재정렬될 때 변하지 않아야 합니다. 일반적으로 데이터베이스의 __고유 ID__ 나 객체의 __고유 속성__ 을 사용합니다.

### __마무리__
리액트에서 __`key` props__ 는 리스트와 동적인 컴포넌트 배열을 렌더링할 때 __효율적인 업데이트와 정확한 식별__ 을 위해 __매우 중요__ 합니다. __`key`__ 를 사용하면 리액트가 어떤 항목이 변경되었는지 효율적으로 파악할 수 있으며, 이는 성능 최적화와 안정적인 UI 업데이트를 가능하게 합니다. 따라서 항상 리스트를 렌더링할 때 __적절한 `key`__ 를 사용하여 리액트가 컴포넌트를 정확하게 관리할 수 있도록 해야 합니다.