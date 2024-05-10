---
layout: post
title: 자바스크립트 웹디 메뉴 버튼만 공부하기
date: 2024-05-08 04:00 +0900
description: 자바스크립트 웹디 메뉴 버튼
image: ../assets/img/javascript.png
category: 웹디 기능사 스크립트
tags: 웹디 기능사 스크립트
published: true
sitemap: true
---

# 웹 디자인 기능사 실기의 스크립트 공부
### 스크립트 목록
1. 팝업창 <br/>
2. 메뉴버튼 <br/>
3. 슬라이드 <br/>

## __메뉴 버튼 전체 코드__<br/>

```javascript
$(".nav > ul > li").mouseover(function () {
    $(this).find(">ul").stop().slideDown();
});
$(".nav > ul > li").mouseout(function () {
    $(this).find(">ul").stop().slideUp();
});
```

### __스크립트 실행 원리__ <br/>

* 전체 코드를 살펴보면 클래스 명 __nav__ 의 자식인 __ul__ 안에 있는 __li__ 에 마우스 커서가 올라갈경우 함수가 실행되어 ul이 아래로 내려오며 보입니다. 또한 그 아래에는 마우스가 벗어날 경우 ul이 다시 올라가며 보이지 않게 됩니다.<br/>

#### __html, css 구조__
해당 포스팅에서는 전체적인 구조를 구성하는 방법에 대해서는 다루고 있지 않습니다. 아래의 코드들은 그저 예시로만 봐주세요.<br/>

```html
<nav class="nav">
    <ul>
        <li><a href="#">지금의 서울</a>
            <ul>
                <li><a href="#">이벤트</a></li>
                <li><a href="#">축제&행사</a></li>
                <li><a href="#">전시</a></li>
            </ul>
        </li>
        <li><a href="#">추천</a>
            <ul>
                <li><a href="#">에디터 추천</a></li>
                <li><a href="#">테마코스</a></li>
                <li><a href="#">도보해설관광</a></li>
                <li><a href="#">한류관광</a></li>
            </ul>
        </li>
        <li><a href="#">여행지</a>
            <ul>
                <li><a href="#">명소</a></li>
                <li><a href="#">엔터테인먼트</a></li>
                <li><a href="#">음식</a></li>
                <li><a href="#">게스트하우스</a></li>
            </ul>
        </li>
        <li><a href="#">여행정보</a>
            <ul>
                <li><a href="#">가이브죽&지도</a></li>
                <li><a href="#">시티투어버스</a></li>
                <li><a href="#">날씨</a></li>
            </ul>
        </li>
    </ul>
</nav>
```

```css
.nav {
    height: 550px;
    padding: 10px;
}

/* 메인 메뉴 */
.nav>ul>li>a {
    width: 100%;
    padding: 10px;
    display: inline-block;
    text-align: center;
    font-size: 18px;
    margin-bottom: 5px;
    color: #9ea1c7;
    background-color: #ededed;
}

.nav>ul>li>a:hover {
    background-color: #d9d9d9;
}

/* 서브 메뉴 */
.nav>ul>li>ul {
    margin-bottom: 10px;
    display: none;
}

.nav>ul>li>ul>li {
    margin-bottom: 2px;
}

.nav>ul>li>ul>li>a {
    width: 100%;
    padding: 10px;
    display: inline-block;
    text-align: center;
    font-size: 18px;
    color: #6e719c;
    background-color: #dbdbdb;
}

.nav>ul>li>ul>li>a:hover {
    background-color: #bfbebe;
}
```


#### __서브 메뉴가 슬라이드 형식으로 내려오게 하기__

```javascript
$(".nav > ul > li").mouseover(function () {
    $(this).find(">ul").stop().slideDown();
});
```

##### __하나씩 살펴보기__

```javascript
$(".nav > ul > li")
```

* nav 클래스를 가진 요소의 직속 자식 ul, 그리고 그 ul의 직속 자식 li를 선택합니다. <br/>

 <br/>

```javascript
.mouseover(function () {})
```

* 선택된 li 요소들 위에 마우스를 올려놓을 때 실행될 함수를 정의합니다. <br/>

 <br/>

```javascript
$(this).find(">ul")
```

* 현재 마우스 오버된 li 요소 내에서 직속 자식 ul을 찾습니다. <br/>

 <br/>

```javascript
.stop()
```

* 현재 진행 중인 애니메이션을 즉시 멈춥니다. 이는 애니메이션이 중첩 실행되는 것을 방지합니다.<br/>

 <br/>

```javascript
.slideDown()
```

* 선택된 요소를 아래로 슬라이드 효과와 함께 보여줍니다. 이는 기능사 실기때 슬라이드 효과가 있는 메뉴 등을 구현할 때 유용합니다.<br/>


#### __서브 메뉴가 슬라이드 형식으로 올라가게 하기__

```javascript
$(".nav > ul > li").mouseout(function () {
    $(this).find(">ul").stop().slideUp();
});
```

##### __하나씩 살펴보기__

```javascript
$(".nav > ul > li")
```

* 위와 동일하게 .nav 클래스를 가진 요소의 직속 자식 ul, 그리고 그 ul의 직속 자식 li를 선택합니다. <br/>

 <br/>

```javascript
.mouseout(function () {})
```

* 선택된 li 요소들에서 마우스가 벗어날 때 실행될 함수를 정의합니다. <br/>

 <br/>

```javascript
$(this).find(">ul")
```

* 현재 마우스 아웃된 li 요소 내에서 직속 자식 ul을 찾습니다.<br/>

 <br/>

```javascript
.stop()
```

* 현재 진행 중인 애니메이션을 즉시 멈춥니다. 이는 애니메이션이 중첩 실행되는 것을 방지합니다.<br/>

 <br/>

```javascript
.slideUp()
```

* 선택된 요소를 위로 슬라이드 효과와 함께 숨깁니다. 이는 기능사 실기때 슬라이드 효과가 있는 메뉴 등을 구현할 때 유용합니다.<br/>

#### 이상 modal 부분의 jQuery 였습니다.