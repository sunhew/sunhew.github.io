---
layout: post
title: data 속성
date: 2024-05-15 19:24 +0900
description: html & css
image: ../assets/img/html_css.png
category: html & css
tags: html&css html css data 속성 data속성
published: true
sitemap: true
---

# HTML & CSS
해당 포스팅에서는 bdata 속성에 대해 다룹니다.<br />


## __HTML & CSS 목차__
* 웹 표준, 웹 접근성 <br/>
* 반응형 작업 <br/>
* 레거시 코드, IR 효과 시멘틱 태그<br/>
* CSS 우선순위, Position 속성<br/>
* block, inline-block, inline 차이 <br/>
* data 속성 ✔️<br/>
* seo, 최적화 방법, ID vs class 차이<br/>

<br/>

## __Data Attribute__<br/>

### __Data Attribute의 개념__
"Data Attribute"는 __HTML 요소에 커스텀 데이터를 저장할 수 있도록 해주는 기능__ 입니다. 이를 통해 JavaScript를 사용하여 동적으로 데이터를 가져오거나 설정할 수 있으며, 웹 페이지의 구조를 보다 유연하게 설계 할 수 있습니다. 데이터 속성은 "data-"로 시작하는 사용자 정의 속성 을 의미하며, HTML5에서 도입 되었습니다. __유연하고 유지보수가 쉬우며, SEO에 미치는 영향이 적어__ 많은 웹 개발자들에게 사랑받는 기능입니다. 하지만 __대용량 데이터 저장에는 부적합할 수 있으며, 브라우저 호환성을 항상 염두에 두어야__ 합니다.

### __HTML Data Attribute__

#### __구문 및 사용 방법__

* 데이터 속성은 `data-` 로 시작 하고, __하이픈 뒤에 속성명을 지정__ 합니다.<br/>
* 데이터 __속성의 값은 문자열__ 이어야 합니다.<br/>

```html
<div data-role="admin" data-user-id="12345"></div>
```

#### __데이터 접근 및 조작__

* __데이터 속성에 접근하거나 값을 조작하려면 JavaScript를 사용__ 할 수 있습니다.<br/>

* `getAttribute` 메서드를 사용하여 데이터 속성 값을 가져올 수 있습니다.<br/>

* `setAttribute` 메서드를 사용하여 데이터 속성 값을 설정할 수 있습니다.<br/>

```html
<script>
    const div = document.querySelector('div');
    const role = div.getAttribute('data-role');  // 'admin'
    div.setAttribute('data-role', 'user');
</script>
```

### __JavaScript와의 상호작용__

CSS에서 `display` __속성을 사용하여 요소의 디스플레이 유형을 지정__ 할 수 있습니다. `display: block` 은 __요소를 블록 레벨로 지정__ 합니다.

#### __dataset 속성 사용__

* `dataset` 속성을 사용하면 간편하게 데이터 속성에 __접근하고 조작__ 할 수 있습니다.<br/>

* 데이터 속성 이름에서 __`data-` 부분은 제거되고, 카멜 케이스 로 변환__ 됩니다.<br/>

```html
<script>
    const div = document.querySelector('div');
    const userId = div.dataset.userId;  // '12345'
    div.dataset.role = 'user';
</script>
```

### __실용적인 예시__

#### __데이터 바인딩__
* 데이터 속성은 __요소에 데이터를 바인딩할 때 유용__ 합니다. 예를 들어,  __버튼 클릭 시 특정 데이터를 처리__ 할 수 있습니다.

```html
<!DOCTYPE html>
<html lang="ko">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Data Attribute Example</title>
    <script>
        function showData() {
            const button = document.querySelector('button');
            alert(button.dataset.info);
        }
    </script>
</head>

<body>
    <button data-info="This is some info" onclick="showData()">Click me</button>
</body>

</html>
```

#### __CSS와의 연계__
* CSS에서 데이터 속성을 선택자로 사용할 수 있습니다.
* 데이터 속성에 따라 특정 스타일을 적용 할 수 있습니다.

```html
<!DOCTYPE html>
<html lang="ko">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Data Attribute CSS Example</title>
    <style>
        div[data-role="admin"] {
            background-color: red;
            color: white;
        }

        div[data-role="user"] {
            background-color: blue;
            color: white;
        }
    </style>
</head>

<body>
    <div data-role="admin">Admin</div>
    <div data-role="user">User</div>
</body>

</html>
```

### __Data Attribute 사용의 장점__<br/>

#### __유연성 및 확장성__

* 데이터 속성을 사용하면 __HTML 요소에 추가 정보를 저장__ 할 수 있습니다.
* __별도의 자바스크립트 객체나 글로벌 변수를 사용하지 않고도 필요한 정보를 요소에 직접 바인딩__ 할 수 있습니다.

#### __간편한 유지보수__

* 데이터 속성을 사용하면 __HTML 구조와 데이터를 명확하게 분리__ 할 수 있습니다.
* __코드의 가독성과 유지보수성이 향상__ 됩니다.

#### __SEO 영향 최소화__

* __표준 HTML 속성__ 이기 때문에, __SEO에 큰 영향을 주지 않으면서__ 필요한 데이터를 저장할 수 있습니다.

### __Data Attribute의 제한사항__

#### __대용량 데이터 저장의 비효율성__
* __대량의 데이터를 저장__ 하는 데는 적합하지 않습니다. 대용량 데이터를 저장할 경우, __성능 저하__ 가 발생할 수 있습니다.

#### __브라우저 호환성__
* 대부분의 최신 브라우저는 데이터 속성을 지원하지만, __구형 브라우저에서는 일부 제한__ 이 있을 수 있습니다. 따라서, __호환성을 확인__ 해야 합니다.

### __활용 사례__

#### __폼 검증__
* 데이터 속성을 사용하여 __폼 필드의 유효성 검사를 수행__ 할 수 있습니다.

```html
<input type="text" data-required="true" data-min-length="5">
```

#### __동적 콘텐츠 로딩__
* 데이터 속성을 사용하여 __비동기 요청을 통해 콘텐츠를 동적으로 로딩__ 할 수 있습니다

```html
<div data-url="/api/data"></div>
```

끝..!