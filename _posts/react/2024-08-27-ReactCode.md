---
layout: post
title: HTML과 React의 차이점과 React와 Node.js의 차이점과 서버 구축 
date: 2024-08-27 13:15 +0900
description: REACT
image: ../assets/img/reactcode.gif
category: 리액트 개념정리
tags: 리액트코드 REACTCODE code react node.js react와node.js의차이점 HTML PHP
published: true
sitemap: true
---

# REACT
해당 포스팅에서는 REACT의 코드와 REACT와 NODE.JS의 차이점을 다룹니다. <br />


## __이번 포스팅 목차__
1. HTML과 React의 차이점과 React와 Node.js의 차이점과 서버 구축 ✔️<br/>
2. Axios와 Fetch API의 차이점 <br/>
3. npm start와 npm run dev의 차이점 <br/>
4. npm audit fix와 npm audit fix --force의 차이점 <br/>

## __HTML과 React을 사용하는 이유와 장단점__<br/>

### __HTML과 React의 기본 개념__

* __HTML (HyperText Markup Language)__

   HTML은 웹페이지의 구조를 정의하는 __기초적인 마크업언어__ 입니다. 웹페이지에서 텍스트, 이미지, 링크 등을 배치하고 구성하는데 사용됩니다. 모든 웹 페이지는 HTML을 기본으로 하고 있으며, 브라우저는 HTML을 해석해 사용자가 보는 화면을 구성합니다.

* __React__

   React는 __JavaScript 라이브러리__ 로, HTML과 달리 웹 페이지의 __동적인 사용자 인터페이스(UI)__ 를 구축하는 데 사용됩니다. React는 컴포넌트 기반으로 동작하며, 필요한 부분만 빠르게 업데이트하는 __부분 렌더링__ 과 같은 고급 기능을 제공합니다.

### __HTML 대신 React를 주로 사용하는 이유__

1. __동적인 웹 애플리케이션__
 
   HTML은 __정적 웹페이지(내용이 바뀌지 않는 웹피이지)를 만드는 데 적합__ 하지만, 현대의 웹 애플리케이션은 __사용자와의 상호작용이 많고, 데이터가 자주 변경__ 됩니다. React는 이러한 동적인 웹 애플리케이션을 쉽게 개발할 수 있게 해줍니다.

2. __컴포넌트 재사용__
 
   React에서는 웹페이지의 각 부분을 __컴포넌트__ 라는 독립된 단위로 관리합니다. 컴포넌트는 __UI의 특정 부분을 독립적으로 구성하는 코드 블록__ 으로, 이를 통해 한 번 만든 컴포넌트를 여러 곳에서 재사용할 있어 __개발 속도와 유지보수의 효율성이 크게 향상__ 됩니다.

3. __빠른 업데이트와 부분 렌더링__
 
   기존의 HTML에서는, 웹페이지의 내용이 변경되면 __전체 페이지를 다시 로드__ 해야 하는 경우가 많았습니다. 예를 들어, 버튼을 눌러서 내용을 바꾸려면 전체 페이지를 서버에서 다시 받아와야 했기에 화면이 깜빡이기도 하고, 불필요한 데이터도 많이 전송되기 때문에 __웹사이트가 느려지는__ 원인이 됩니다. <br />
  <br />

   __3-1. React와 부분 렌더링__ <br/>
   
   React는 이런 문제를 해결하기 위해 __부분 렌더링__ 이라는 개념을 도입했습니다. React에서는 __Virtual DOM__ 을 사용해서 실제 DOM(HTML 문서의 구조)를 조작하기 전에 가상 DOM에서 변경사항을 먼저 계산한뒤 필요한 __부분만 선택적으로 업데이트__ 합니다. <br />

   예를 들면 `Main.jsx` 파일에 `props.children` 을 사용하면, 부모 컴포넌트(Main 컴포넌트)안에 있는 자식 컴포넌트들이 어떤 역활을 하는지 알 수 있게 됩니다. 이떄 React는 자식 컴포넌트에서 __변경된 부분만 다시 렌더링__ 하게 됩니다. <br />
   
   이 과정의 어떻게 동작하는지 설명한뒤 `props.children` 사용 예시 코드를 보여드리겠습니다.

   __첫번째, Virtual DOM에서 변경 감지__
   
     React는 사용자가 어떤 동작을 했을 때, 그로 인해 웹페이지에서 어떤 부분이 바뀌었는지 Virtual DOM에서 미리 계산합니다.

   __두번째, 필요한 부분만 업데이트__

     이 계산 결과에 따라 실제 DOM에서 바꿔야 할 부분만 업데이트합니다. 예를 들어, 사용자가 버튼을 눌러서 글자를 바꾼다면, 그 글자 부분만 다시 그려주고 나머지 부분은 __그대로 유지__ 합니다.

    * __Main.jsx__

   ```r
    <main id='main' role='main'>
        {props.children}
    </main>
   ```

    * __App.js__
    
   ```r
    import Header from "./components/Header";
    mport Main from "./components/Main";
    mport Aside from "./components/Aside";
    mport Search from "./components/Search";

    mport Home from "./pages/Home";
    mport Mymusic from "./pages/Mymusic";
    mport ChartList from "./pages/ChartList";
    mport PlayList from "./pages/PlayList";
    mport MusicPlayerProvider from "./context/MusicPlayerProvider";
    mport SearchResults from "./components/SearchResults";
    mport DarkModeToggle from "./context/DarkModeToggle";

    const App = () => {
       return (
          <BrowserRouter>
              <Header />
              <Main>
                  <Search />
                  <Routes>
                      <Route path="/" element={<Home />} />
                      <Route path="/search/:searchID" element={<SearchResults />} />
                      <Route path="/mymusic" element={<Mymusic />} />
                      <Route path="/playlist/:id" element={<PlayList />} />
                      <Route path="/chart/:id" element={<ChartList />} />
                  </Routes>
              </Main>
              <Aside />
              <ToastContainer />
          </BrowserRouter>
       );
    };
   ```
3. __빠른 업데이트와 부분 렌더링__
