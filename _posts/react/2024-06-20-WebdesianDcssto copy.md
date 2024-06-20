---
layout: post
title: 리액트의 DOM
date: 2024-06-17 18:50 +0900
description: html & css
image: ../assets/img/react03.jpg
category: react
tags: reactDOM DOM react react개념
published: true
sitemap: true
---

# HTML & CSS
해당 포스팅에서는 REACT의 DOM을 다룹니다.  <br />


## __이번 포스팅 목차__
* REACT의 DOM <br/>

## __리액트 DOM의 주요 특징__<br/>
DOM(Document Object Model)은 __HTML, XHTML__ 및 __XML__ 문서의 __프로그래밍 인터페이스__ 입니다. DOM은 __문서의 구조화된 표현__ 을 제공하고, __프로그래밍 언어__ 가 문서의 __내용과 구조를 수정__ 할 수 있도록 합니다. DOM은 문서의 구조를 트리 구조로 표현하며, 이 구조에서 각 요소는 __객체__ 로 취급됩니다. 더 자세히 적어보자면 __DOM(Document Object Model)__ 은 __문서의 구조를 트리 형태로 표현__ 하며, 이를 통해 자바스크립트가 문서를 조작하고 상호작용할 수 있게 합니다. DOM을 사용하면 __엘리먼트를 선택, 생성, 수정, 삭제__ 할 수 있으며, __다양한 이벤트를 처리__ 할 수 있습니다

### __DOM의 기본 개념__

#### __노드(Node)__

* __엘리먼트 노드(Element Node)__: __HTML 태그__ 를 나타내며, 트리 구조의 __기본 단위__ 입니다. `<div>`, `<p>`가 기본적인 예입니다.

* __텍스트 노드(Text Node)__: 엘리먼트 내의 __텍스트__ 를 나타냅니다. 예를 들면 `Hello World` (엘리먼트 `<p>` 안에 있는 텍스트)가 있습니다.

* __어트리뷰트 노드(Attribute Node)__: 엘리먼트의 속성을 나타냅니다. 예를 들면 `id="example"`가 있습니다.

* __주석 노드(Comment Node)__: 주석을 나타냅니다. 예를 들면  `<!-- This is a comment -->`  가 있습니다.

#### __트리 구조(Tree Structure)__

* DOM은 __트리 구조__ 로 문서를 표현합니다. 트리의 각 노드는 문서의 특정 부분을 나타내며, __루트 노드__ 부터 시작하여 __자식 노드__ 로 구성됩니다. 루트 노드는 __`document` 객체__ 로, 문서의 __최상위 객체__ 입니다.

### __DOM의 주요 구성 요소__

#### __JSX__

* __document 객체__: 웹 페이지 전체를 나타내는 __최상위 객체__ 입니다. `document` 객체를 통해 __DOM의 다른 모든 요소에 접근__ 할 수 있습니다.

* __엘리먼트(Element)__: HTML 태그를 나타내며, `document.getElementById` 또는 `document.querySelector`와 같은 메서드를 사용하여 __특정 엘리먼트에 접근__ 할 수 있습니다.

* __어트리뷰트(Attribute)__: 엘리먼트의 속성을 나타내며, `element.getAttribute` 또는 `element.setAttribute`와 같은 메서드를 사용하여 __속성을 가져오거나 설정__ 할 수 있습니다.

* __텍스트(Text)__: 엘리먼트 내의 텍스트를 나타내며, `element.textContent` 또는 `element.innerText` 를 사용하여 __텍스트를 가져오거나 설정__ 할 수 있습니다.

### __DOM 조작 방법__

#### __엘리먼트 선택__

* __`document.getElementById(id)`__: 특정 __id__ 를 가진 엘리먼트를 선택합니다.

* __`document.getElementsByClassName(className)`__: 특정 __클래스__ 를 가진 모든 엘리먼트를 선택합니다.

* __`document.getElementsByTagName(tagName)`__: 특정 __태그 이름__ 을 가진 모든 엘리먼트를 선택합니다.

* __`document.querySelector(selector)`__: __CSS 선택자__ 를 사용하여 __일치하는 첫 번째 엘리먼트__ 를 선택합니다.

* __`document.querySelectorAll(selector)`__: __CSS 선택자__ 를 사용하여 __일치하는 모든 엘리먼트__ 를 선택합니다.

#### __엘리먼트 생성 및 추가__

* __`document.createElement(tagName)`__: __새로운 엘리먼트__ 를 생성합니다.

* __`parentNode.appendChild(newNode)`__: 부모 노드의 자식 노드 목록에 __새로운 노드__ 를 추가합니다.

* __`parentNode.insertBefore(newNode, referenceNode)`__: __참조 노드 앞에 새로운 노드__ 를 삽입합니다.

#### __엘리먼트 제거__

* __`parentNode.removeChild(childNode)`__: 부모 노드에서 자식 노드를 제거합니다.

* __`element.remove()`__: __특정 엘리먼트__ 를 제거합니다.

#### __엘리먼트 속성 조작__

* __`element.setAttribute(name, value)`__: 엘리먼트에 __새로운 속성__ 을 설정합니다.

* __`element.getAttribute(name)`__: 엘리먼트의 __속성 값을 가져옵니다.__

* __`element.removeAttribute(name)`__: 엘리먼트의 __속성을 제거__ 합니다.

#### __엘리먼트 내용 조작__

* __`element.innerHTML`__: 엘리먼트의 __HTML 내용을 가져오거나 설정__ 합니다.

* __`element.textContent`__: 엘리먼트의 __텍스트 내용을 가져오거나 설정__ 합니다.

### __DOM 이벤트__
DOM은 사용자와의 상호작용을 처리하기 위해 __이벤트 모델을 제공__ 합니다. 주요 이벤트 유형은 다음과 같습니다:

* __마우스 이벤트의 종류__: `click`, `dblclick`, `mouseover`, `mouseout`, `mousedown`, `mouseup`, `mousemove`.

* __키보드 이벤트의 종류__: `keydown`, `keyup`, `keypress`.

* __폼 이벤트의 종류__: `submit`, `reset`, `change`, `focus`, `blur`.

* __문서 이벤트의 종류__: `DOMContentLoaded`, `load`, `unload`, `beforeunload`.

```javascript
element.addEventListener('click', function(event) {
  // 이벤트 처리 로직
});
```