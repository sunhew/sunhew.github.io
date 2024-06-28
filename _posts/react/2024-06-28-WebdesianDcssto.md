---
layout: post
title: 리액트의 SPA, Router와 SPA의 단점
date: 2024-06-28 09:12 +0900
description: REACT
image: ../assets/img/react12.jpg
category: react
tags: reactSPA,Router와SPA의단점 SPA Router SPA의단점 react
published: true
sitemap: true
---

# REACT
해당 포스팅에서는 REACT의 SPA, Router와 SPA의 단점에 대해 다룹니다.  <br />


## __이번 포스팅 목차__
* REACT의 SPA, Router와 SPA의 단점 <br/>

## __리액트의 SPA (Single Page Application)__<br/>
__SPA (Single Page Application)__ 는 사용자와의 상호작용을 위해 하나의 HTML 페이지를 로드하고, 필요한 경우 동적으로 콘텐츠를 갱신하는 웹 애플리케이션입니다. SPA는 전통적인 멀티 페이지 애플리케이션과 달리 페이지 전체를 새로 고치는 대신, __클라이언트 사이드에서 콘텐츠를 로드하고 업데이트__ 합니다.

### __특징__

* __클라이언트 사이드 렌더링__: 서버로부터 전체 HTML 페이지를 로드하는 대신, 필요한 데이터를 가져와 클라이언트에서 렌더링합니다.

* __빠른 상호작용__: 페이지 전체를 새로 고치지 않으므로, 사용자 상호작용이 빠릅니다.

* __단일 진입접__: 하나의 HTML 파일을 사용하여 여러 뷰를 동적으로 관리합니다.

## __React Router__
__React Router__ 는 리액트 애플리케이션에서 __라우팅__ 을 관리하는 표준 라이브러리입니다. 이를 통해 SPA에서 URL에 따라 서로 다른 컴포넌트를 렌더링할 수 있습니다.

### __주요 개념__

* __Router__: 애플리케이션의 라우팅 컨텍스트를 제공합니다.

* __Route__: 특정 URL 경로에 따라 렌더링할 컴포넌트를 정의합니다.

* __Link__: 용자가 클릭할 수 있는 네비게이션 링크를 제공합니다.

```javascript
import React from 'react';
import { BrowserRouter as Router, Route, Switch, Link } from 'react-router-dom';

function Home() {
  return <h2>Home</h2>;
}

function About() {
  return <h2>About</h2>;
}

function App() {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/about">About</Link>
            </li>
          </ul>
        </nav>
        <Switch>
          <Route path="/" exact component={Home} />
          <Route path="/about" component={About} />
        </Switch>
      </div>
    </Router>
  );
}

export default App;
```

### __SPA의 단점__

* __초기 로딩 시간 증가__: SPA는 __초기 로딩 시__ 모든 필요한 자바스크립트, CSS 파일을 불러와야 하므로 초기 로딩 시간이 길어질 수 있습니다. 이는 사용자 경험을 저하시킬 수 있습니다.

* __SEO 문제__: SPA는 클라이언트 사이드에서 콘텐츠를 동적으로 생성하므로, __검색 엔진 최적화(SEO)__ 가 어렵습니다. 검색 엔진 크롤러가 자바스크립트를 실행하지 못하면 페이지 콘텐츠를 인덱싱하지 못할 수 있습니다.

* __네트워크 및 성능 문제__: SPA는 __네트워크 상태__ 와 __클라이언트 성능__ 에 민감합니다. 클라이언트의 성능이 낮거나 네트워크 상태가 불안정하면 애플리케이션 성능에 부정적인 영향을 미칠 수 있습니다.

* __복잡한 상태 관리__: SPA는 복잡한 사용자 상호작용과 다양한 상태를 관리해야 하므로, __상태 관리__ 가 복잡해질 수 있습니다. 이는 코드의 복잡성을 증가시키고 유지보수를 어렵게 만듭니다.

* __메모리 누수__: SPA는 한 페이지에서 여러 컴포넌트를 동적으로 교체하면서 실행되므로, __메모리 누수__ 문제가 발생할 수 있습니다. 적절한 정리 작업을 수행하지 않으면 메모리 사용량이 계속 증가할 수 있습니다.

### __마무리__
__SPA (Single Page Application)__ 는 빠른 상호작용과 사용자 경험을 제공하지만, __초기 로딩 시간, SEO 문제, 네트워크 및 성능 문제, 복잡한 상태 관리, 메모리 누수__ 등의 단점이 존재합니다. __React Router__ 를 사용하여 SPA에서 효율적으로 라우팅을 관리할 수 있으며, 이러한 단점을 보완하기 위해 코드 스플리팅, 서버 사이드 렌더링(SSR) 등의 기술을 적용할 수 있습니다.