---
layout: post
title: block, inline-block, inline 차이
date: 2024-05-15 19:24 +0900
description: html & css
image: ../assets/img/html_css.png
category: html & css
tags: html&css html css block inline-block inline차이
published: true
sitemap: true
---

# HTML & CSS
해당 포스팅에서는 block, inline-block, inline 차이에 대해 다룹니다.<br />


## __HTML & CSS 목차__
* 웹 표준, 웹 접근성 <br/>
* 반응형 작업 <br/>
* 레거시 코드, IR 효과 시멘틱 태그<br/>
* CSS 우선순위, Position 속성<br/>
* block, inline-block, inline 차이 ✔️<br/>
* data 속성<br/>
* seo, 최적화 방법, ID vs class 차이<br/>

## __Block__<br/>

### __Block_의 개념__
"__Block__"은 __HTML과 CSS에서 주로 사용되는 용어__ 로, 두 가지 주요 개념을 설명합니다. __HTML 요소의 디스플레이 속성과 그로 인해 발생하는 레이아웃 동작__ 입니다. 블록 요소는 __웹 페이지의 구조를 정의__ 하고, CSS를 통해 __레이아웃과 스타일을 조정__ 하는 데 중요한 역할을 합니다.

### __HTML 블록 요소__

#### __항상 새로운 줄에서 시작__

* 블록 요소는 __다른 콘텐츠와 구분__ 되어 __항상 새로운 줄에서 시작__ 합니다.<br/>
* 블록 __요소 하나가 끝나면 다음 블록 요소는 새로운 줄에서 시작__ 합니다.<br/>

#### __전체 너비를 차지__

* 블록 요소는 기본적으로 __부모 요소의 전체 너비를 차지__ 합니다. 이로 인해 __같은 줄에 다른 블록 요소가 있을 수 없습니다.__<br/>

#### __내부에 다른 블록 및 인라인 요소를 포함할 수 있음__

* 블록 요소는 __다른 블록 요소와 인라인 요소를 포함__ 할 수 있습니다.<br/>

#### __주요 블록 요소__

```html
<div></div>
<p></p>
<h1></h1>
<ul></ul>
<ol></ol>
<li></li>
<section></section>
<article></article>
<nav></nav>
<footer></footer>
```

### __CSS 디스플레이 속성__

CSS에서 `display` __속성을 사용하여 요소의 디스플레이 유형을 지정__ 할 수 있습니다. `display: block` 은 __요소를 블록 레벨로 지정__ 합니다.

```css
.block-element {
    display: block;
}
```

### __블록 요소의 레이아웃 특성__

#### __차지하는 공간__
* 블록 요소는 부모 요소의 전체 너비를 차지합니다. 예를 들어, `<div>`는 __기본적으로 부모의 전체 너비__ 를 가집니다.

#### __크기 조정__
* `width` 와 `height` 속성을 사용하여 블록 요소의 크기를 조정할 수 있습니다.
* __기본적으로 너비는 100%__ 이며, `width` 속성을 통해 이를 조정할 수 있습니다.
* `width: 50%` 로 설정하면 __부모 요소 너비의 50%를 차지__ 합니다.

#### __패딩, 마진 및 경계__
* 블록 요소는 __패딩, 마진, 경계(border)와 같은 박스 모델 속성을 적용__ 할 수 있습니다. 이러한 속성은 __요소의 레이아웃과 공간 배치를 관리__ 하는 데 사용됩니다.

```css
.block-element {
    display: block;
    width: 50%;
    padding: 10px;
    margin: 20px auto;
    border: 1px solid #000;
}
```

#### __내부 요소 배치__
* 블록 요소는 __내부에 포함된 다른 블록 요소와 인라인 요소를 정렬하고 배치__ 합니다.
* __블록 요소 안에 포함된 요소들은 순서대로 쌓입니다__(위에서 아래로).

### __우선순위 예제__

```css
<!DOCTYPE html>
<html lang="ko">
<head>

    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Specificity Example</title>
    <style>
        /* 특정성: 0,0,0,1 */
        p {
            color: black;
        }

        /* 특정성: 0,0,1,0 */
        .example {
            color: blue;
        }

        /* 특정성: 0,1,0,0 */
        #unique {
            color: green;
        }

        /* 특정성: 0,0,1,1 */
        p.example {
            color: red;
        }

        /* 특정성: 0,0,1,1, 중요도 높음 */
        p.example {
            color: yellow !important;
        }
    </style>
</head>
<body>
    <p class="example" id="unique">This is a test paragraph.</p>
</body>
</html>
```

위의 예쩨에서 `<p class="example" id="unique">` 요소는 여러 CSS 규칙에 의해 스타일이 적용됩니다. 우선순위에 따라 최종 색상은 다음과 같이 결정됩니다.

|선택자|코드|우선순위|
|---|---|---|
|기본 스타일| `p { color: black; }` |특정성: 0,0,0,1|
|클래스 선택자| `.example { color: blue; }` |특정성: 0,0,1,0|
|ID 선택자| `#unique { color: green; }` |특정성: 0,1,0,0|
|조합 선택자| `p.example { color: red; }` |특정성: 0,0,1,1|
|중요도 높은 규칙| `p.example { color: yellow !important; }` |특정성: 0,0,1,1 (중요도 높음)|

위 표를 살펴보면 `color: yellow` 뒤에 `!important`가 붙어있으므로 최종적으로는 요소의 텍스트는 노란색이 됩니다.

### __우선순위 충돌 해결 방벙__

#### __구체적인 선택자 사용__
* 선택자를 구체적으로 작성하여 특정성을 높입니다.

#### __중요도 조절__
* 가능한 한 `!important` 사용을 피하고, __구조적인 선택자 설계를 통해 해결__ 합니다

#### __스타일 정의 순서__
* 스타일을 __정의하는 순서를 고려__ 하여 후에 정의된 스타일이 우선 적용되도록 합니다.

#### __CSS 리셋 또는 노멀라이즈 사용__
* 브라우저 __기본 스타일을 일관__ 되게 만들기 위해 __CSS 리셋__ 또는 __노멀라이즈__ 를 사용합니다.