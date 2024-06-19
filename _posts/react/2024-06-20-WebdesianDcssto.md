---
layout: post
title: 반응형 작업
date: 2024-06-20 15:59 +0900
description: html & css
image: ../assets/img/react01.jpg
category: html & css
tags: html&css html css 반응형작업
published: true
sitemap: true
---

# HTML & CSS
해당 포스팅에서는 html & CSS 반응형 작업등을 다룹니다.  <br />


## __HTML & CSS 목차__
* 웹 표준, 웹 접근성 <br/>
* 반응형 작업 ✔️<br/>
* 레거시 코드, IR 효과 시멘틱 태그<br/>
* CSS 우선순위, Position 속성<br/>
* block, inline-block, inline 차이<br/>
* data 속성<br/>
* seo, 최적화 방법, ID vs class 차이<br/>

## __반응형 작업__<br/>

### __반응형 작업의 개념__
반응형 웹 디자인(Responsive Web Design)은 __다양한 장치와 화면 크기에서 일관된 사용자 경험을 제공__ 하기 위해 __웹 페이지의 레이아웃과 콘텐츠를 동적으로 조정하는 방법론__ 입니다. 반응형 디자인을 구현하기 위해 __HTML__ 과 __CSS__ 를 사용하여 __미디어 쿼리, 유연한 레이아웃, 유연한 이미지 및 기타 기술을 활용__ 합니다.

### __웹 디자인의 주요 개념과 기술__

#### __유연한 레이아웃 (Flexible Layouts)__

* __비율 기반의 크기__ : 픽셀 대신 비융 기반의 크기(__%, em, rem__)를 사용하여 요소의 너비와 높이를 정의합니다. 이런 방법을 사용하면 요소가 화면 크기에 따라 자동으로 조정되며, 아래의 코드는 사용 예시입니다.<br/>

```css
.container {
    width: 80%; /* 부모 요소의 80% 너비 */
    margin: 0 auto; /* 가운데 정렬 */
}

.box {
    width: 50%; /* 부모 요소의 50% 너비 */
    padding: 1em; /* 1em의 패딩 */
}

```

#### __유연한 이미지 (Flexible Images)__

* 이미지의 크기를 화면 크기에 맞게 조정합니다. __`max-width`__ 속성을 사용하여 이미지가 부모 요소를 넘어서지 않도록 합니다. <br/>

```css
img {
    max-width: 100%; /* 부모 요소의 너비를 넘지 않도록 설정 */
    height: auto; /* 이미지의 원본 비율을 유지 */
}
```

#### __미디어 쿼리 (Media Queries)__

* 미디어 쿼리를 사용하여 특정 화면 크기난 장치 유형에 따라 다른 CSS 규칙을 적용합니다. 미디어 쿼리는 CSS3의 중요한 기능입니다. <br/>

```css
@media (조건) {
    /* 조건이 충족될 때 적용할 CSS 규칙 */
}
```

```css
/* 예시 */

/* 기본 스타일 */
body {
    font-size: 16px;
}

/* 작은 화면용 스타일 */
@media (max-width: 600px) {
    body {
        font-size: 14px;
    }
}

/* 중간 크기 화면용 스타일 */
@media (min-width: 601px) and (max-width: 1024px) {
    body {
        font-size: 15px;
    }
}

/* 큰 화면용 스타일 */
@media (min-width: 1025px) {
    body {
        font-size: 16px;
    }
}
```

#### __반응형 그리드 시스템 (Responsive Grid System)__

* __CSS 그리드 또는 플렉스박스를 사용하여 다양한 화면 크기에서 유연__ 하게 레이아웃을 구성합니다. <br/>

```css
.container {
    display: flex;
    flex-wrap: wrap;
}

.item {
    flex: 1 1 200px; /* 최소 200px 너비, 공간이 허용되면 균등 분배 */
    margin: 10px;
}
```

```css
/* 그리드 예시 */

.container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 10px;
}

.item {
    background-color: lightgray;
    padding: 20px;
}
```

#### __뷰포트 메타 태그 (Viewport Meta Tag)__

* __HTML 문서의 헤드 부분에 뷰포트 메타 태그를 추가__ 하여 브라우저가 웹 페이지를 올바르게 렌더링하도록 지시합니다. <br/>

```css
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

#### __반응형 타이포그래피 (Responsive Typography)__

* __글꼴 크기, 줄 높이 등을 화면 크기에 맞게 조정__ 합니다. `vw` 단위는 __뷰포트 너비의 백분율__ 을 나타내며, __반응형 타이포그래피에 유용__ 합니다. <br/>

```css
h1 {
    font-size: 4vw; /* 뷰포트 너비의 4% */
}

p {
    font-size: 2vw; /* 뷰포트 너비의 2% */
}
```

#### __CSS 프레임워크 사용 (CSS Frameworks)__

* 반응형 웹 디자인을 더 쉽게 구현하기 위해 `Bootstrap` `Foundation` 과 같은 __CSS 프레임워크를 사용__ 할 수 있습니다. __이 프레임워크들은 미리 정의된 반응형 그리드 시스템과 UI 요소를 제공합니다.__<br/>

```html
<link href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css" rel="stylesheet">

<div class="container">
    <div class="row">
        <div class="col-md-6">Column 1</div>
        <div class="col-md-6">Column 2</div>
    </div>
</div>
```