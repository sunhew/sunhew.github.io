---
layout: post
title: 불변성을 유지하려면 어떻게..
date: 2024-05-21 18:24 +0900
description: html & css
image: ../assets/img/html_css.png
category: html & css
tags: html&css html css block inline-block inline차이
published: true
sitemap: true
---

# HTML & CSS
해당 포스팅에서는 block, inline-block, inline 차이에 대해 다룹니다. 꽤 많이 길기에 오른쪽에 있는 목차를 활용해 주세요.<br />


## __HTML & CSS 목차__
* 웹 표준, 웹 접근성 <br/>
* 반응형 작업 <br/>
* 레거시 코드, IR 효과 시멘틱 태그<br/>
* CSS 우선순위, Position 속성<br/>
* block, inline-block, inline 차이 ✔️<br/>
* data 속성<br/>
* seo, 최적화 방법, ID vs class 차이<br/>

<br/>

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

<br/>

### __인라인 요소와의 차이점__

#### __인라인 요소__
* 인라인 요소는 __콘텐츠의 흐름을 유지__ 하며, __주변의 다른 콘텐츠와 같은 줄에 배치__ 됩니다.
* 주로 텍스트와 관련된 요소들이 인라인 요소입니다. 예를 들면 `<span>` , `<a>` , `<strong>` , `<em>` 이 있습니다.

#### __블록 요소__
* 블록 요소는 __항상 새로운 줄에서 시작__ 하며, __전체 너비를 차지__ 합니다. 주로 __구조적인 요소__ 들이 __블록 요소__ 입니다. 예를 들면 `<div>` , `<p>` , `<h1>` 이 있습니다.

<br/>

### __블록 요소 예시 코드__

```html
<!DOCTYPE html>
<html lang="ko">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Block Element Example</title>
    <style>
        .container {
            width: 80%;
            margin: 0 auto;
            border: 1px solid #ccc;
            padding: 20px;
        }

        .block-element {
            display: block;
            width: 100%;
            margin-bottom: 20px;
            padding: 10px;
            border: 1px solid #000;
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="block-element">Block Element 1</div>
        <div class="block-element">Block Element 2</div>
        <div class="block-element">Block Element 3</div>
    </div>
</body>

</html>
```

위의 예시예서 `.block-element` 클래스는 `display: block` 속성을 사용하여 __블록 요소로 지정__ 되었습니다. 각 __블록 요소는 부모 컨테이너의 전체 너비를 차지__ 하며, __아래로 쌓입니다.__

<br/>

## __inline-block__<br/>

### __inline-block의 개념__
`inline-block` 은 CSS에서 요소의 `display` __속성을 지정할 때 사용하는 값 중 하나로, 인라인 요소와 블록 요소의 특성을 모두 가집니다.__ 이를 통해 __요소를 블록처럼 취급하면서도 인라인 요소처럼 같은 줄에 배치__ 할 수 있습니다.

### __주요 특성__

#### __같은 줄에 배치__

* `inline-block` 요소는 __인라인 요소처럼 같은 줄에 배치__ 됩니다. 이는 여러 `inline-block` 요소들이 __한 줄에 나란히 배치될 수 있음을 의미__ 합니다.

#### __블록 요소처럼 크기 조절 가능__

* `inline-block` 요소는 블록 요소처럼 `width` 와 `height` 속성을 사용할 수 있으며, __블록 요소처럼 패딩(padding), 마진(margin), 경계(border) 등의 박스 모델 속성을 적용__ 할 수 있습니다.

#### __인라인 요소와의 차이__

* __인라인 요소__ 는 `width` 와 `height` __속성을 무시__ 하지만, `inline-block` __요소는 이를 존중__ 합니다. 또한 __인라인 요소는 주로 텍스트 콘텐츠와 함께 사용__ 되며, __블록 요소는 구조적인 레이아웃을 구성__ 합니다.

#### __inline-block 사용예시__

```html
<!DOCTYPE html>
<html lang="ko">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Inline-Block Example</title>
    <style>
        .inline-block-element {
            display: inline-block;
            width: 100px;
            height: 100px;
            margin: 10px;
            padding: 10px;
            border: 1px solid #000;
            background-color: lightblue;
            vertical-align: top;
        }
    </style>
</head>

<body>
    <div class="inline-block-element">Box 1</div>
    <div class="inline-block-element">Box 2</div>
    <div class="inline-block-element">Box 3</div>
</body>

</html>
```

위의 예제에서 `.inline-block-element` 클래스는 `display: inline-block` 속성을 사용합니다. __이 속성 덕분에 요소들이 같은 줄에 나란히 배치되며, 각 요소는 지정된 너비와 높이__ 를 가집니다.

### __주요 속성 설명__

#### __width와 height__
* `inline-block` 요소는 __블록 요소처럼 너비와 높이를 지정__ 할 수 있습니다.

#### __padding, margin, border__
* 모든 박스 모델 속성이 적용됩니다.

#### __수직 정렬(vertical-align)__
* 인라인 요소와 마찬가지로 __수직 정렬을 조정__ 할 수 있습니다.
* 기본값은 `baseline` 이지만, `top` , `middle` , `bottom` 등 __다양한 값을 사용__ 할 수 있습니다.
* 예를 들어, 위의 예제에서 `vertical-align: top` 을 __사용하여 요소들이 상단에 정렬__ 되도록 했습니다.

### __인라인 요소와 블록 요소와의 비교__

|특성|inline 요소|block 요소|inline-block 요소|
|---|---|---|---|
|줄 바꿈|같은 줄|항상 새로운 줄에서 시작|같은 줄|
|크기 속성|무시 ( `width` , `height` 적용 불가)|적용 가능|적용 가능|
|박스 모델 속성|일부 적용 가능 ( `padding` , `margin` 중 좌우만)|적용 가능|적용 가능|
|수직 정렬| `vertical-align` 가능|불가능| `vertical-align` 가능|

### __활용 사례__
`inline-block` 은 다양한 __레이아웃을 구성하는 데 유용__ 합니다. 특히 다음과 같은 경우에 많이 사용됩니다

#### __네비게이션 바__
* 메뉴 항목들을 __나란히 배치할 떄 유용__ 합니다.

#### __이미지 갤러리__
* 이미지나 썸네일을 __나란히 배치하여 갤러리를 구성할 때 사용__ 됩니다.

#### __카드 레이아웃__
* 카드형 레이아웃을 만들 때 각 카드를 `inline-block` 으로 설정하면, __카드를 한 줄에 여러 개 배치__ 할 수 있습니다.

#### __폼 요소__
* 폼의 __입력 요소들을 한 줄에 배치할 때 사용__ 됩니다.

### __주의 사항__

#### __화이트 스페이스 문제__
* HTML 코드에서 `inline-block` __요소들 사이에 공백이 있으면 그 공백이 요소들 사이에 간격으로 적용__ 됩니다. 이를 해결하기 위한 몇 가지 방법은 다음과 같습니다

    * 요소들 사이의 공백을 제거하거나 HTML 태그를 붙여 씁니다.
    * 부모 요소의 `font-size` 를 __0으로 설정__ 하고, 각 요소에 필요한 `font-size` 를 __개별적으로 지정__ 합니다.
    * CSS 그리드 또는 __플렉스 박스 레이아웃을 고려__ 할 수도 있습니다.

#### __브라우저 호환성__
대부분의 최신 브라우저는 `inline-block` 을 잘 지원하지만, 오__래된 브라우저에서는 일부 문제__ 가 있을 수 있습니다. __최신 CSS 레이아웃 기술과의 호환성을 확인__ 해야 합니다.

<br/>

## __inline__<br/>

### __inline의 개념__
`inline-block` 은 CSS에서 요소의 `display` __속성을 지정할 때 사용하는 값 중 하나로, 인라인 요소__ 를 나타냅니다. __인라인 요소는 블록 요소와 달리 같은 줄에 다른 요소들과 함께 배치__ 되며, 주로 텍스트와 관련된 __작은 요소들에 사용__ 됩니다.

### __주요 특성__

#### __같은 줄에 배치__

* 인라인 요소는 다른 인라인 요소들과 __함께 같은 줄에 배치__ 됩니다. 요소의 크기는 그 내용에 따라 결정됩니다.

#### __크기 조절 제한__

* `width` 와 `height` 속성을 사용할 수 없습니다. 인라인 요소의 크기는 주로 그 내용에 의해 결정됩니다.

#### __박스 모델 속성 제한__

* `padding` 과 `margin` 속성은 사용할 수 있지만, __상하 패딩과 마진은 요소의 레이아웃에 영향을 미치지 않습니다.__ 또한 경계(border) 속성은 적용할 수 있지만, 요소의 레이아웃을 변경하지 않습니다.

#### __주요 인라인 요소__
HTML에서 자주 사용되는 인라인 요소는 다음과 같습니다.

|코드|설명|
|---|---|
| `<a>` |하이퍼링크를 정의|
| `<span>` |일반 텍스트를 그룹화|
| `<strong>` |중요 텍스트를 강조|
| `<em>` |텍스트를 이탤릭체로 강조|
| `<img>` |이미지를 삽입|
| `<code>` |코드 조각을 나타냄|
| `<br>` |줄 바꿈을 삽입|
| `<label>` |폼 요소에 대한 라벨을 정의|

### __사용 예시__

```html
<!DOCTYPE html>
<html lang="ko">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Inline Elements Example</title>
    <style>
        .inline-element {
            color: red;
            border: 1px solid black;
            padding: 5px;
            margin: 10px;
        }
    </style>
</head>

<body>
    <p>This is a <span class="inline-element">span element</span> within a paragraph.</p>
    <p>Here is an <a href="#" class="inline-element">anchor element</a> in another paragraph.</p>
</body>

</html>
```
위의 예제에서 `.inline-element` 클래스는 `span` 과 `a` __요소에 적용__ 됩니다. 이들은 __모두 인라인 요소이기 때문에 다른 텍스트와 같은 줄에 배치__ 됩니다.

### __주요 속성 설명__

```css
.inline-element {
    display: inline;
    padding: 10px;  /* 좌우 패딩만 레이아웃에 영향을 줌 */
    margin: 10px;  /* 좌우 마진만 레이아웃에 영향을 줌 */
    border: 1px solid #000; /* 경계는 요소 주위에 나타남 */
}
```

#### __display: inline__
* 인라인 요소를 지정하는 기본 `display` 값입니다.

#### __width와 height__
* 인라인 요소는 `width` 와 `height` __속성을 무시__ 합니다. 대신, __요소의 크기는 그 내용에 따라 결정__ 됩니다.

#### __박스 모델 속성__
* 인라인 요소에 `padding` 과 `margin `을 적용할 수 있지만, __상하 패딩과 마진은 요소의 레이아웃에 영향을 미치지 않습니다.__
* __`border` 속성은 요소 주위에 경계를 그릴 수 있지만, 상하 경계는 요소의 크기를 변경하지 않습니다.__

### __인라인 요소와 블록 요소 비교__

|특성|inline 요소|block 요소|
|---|---|---|
|줄 바꿈|같은 줄에 다른 요소들과 함께 배치|항상 새로운 줄에서 시작|
|크기 속성|무시 ( `width` `height` 적용 불가)|적용 가능|
|박스 모델 속성|일부 적용 가능 ( `padding` `margin` 중 좌우만)|적용 가능|
|수직 정렬| `vertical-align` 가능|불가능|
|콘텐츠의 영향|요소의 내용에 따라 크기 결정|부모 요소의 전체 너비를 차지|

### __활용 사례__
인라인 요소는 주로 텍스트와 관련된 작업에서 유용합니다. 다음은 인라인 요고가 주로 사용되는 몇 가지 상황입니다.

#### __텍스트 강조__
* __특정 단어나 문장을 강조__ 하기 위해 `<strong>` , `<em>` 과 같은 요소를 사용합니다.

#### __링크__
* __텍스트나 이미지를 링크로 만들기 위해 `<a>` 요소를 사용합니다.__

#### __텍스트와 이미지 혼합__
* __텍스트와 함께 이미지를 배치할 때__ `<img>` 요소를 사용합니다.

#### __폼 레이블__
* __폼 요소와 관련된 텍스트를 설명__ 하기 위해 `<label>` 요소를 사용합니다.