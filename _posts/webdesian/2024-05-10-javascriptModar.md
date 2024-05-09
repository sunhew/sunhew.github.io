---
layout: post
title: 자바스크립트 웹디 팝업창만 공부하기
date: 2024-05-10 17:00 +0900
description: 자바스크립트 웹디 팝업창
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

## __팝업창 전체 코드__<br/>

```javascript
$(".notice ul li:nth-child(1)").click(function () {
    $(".modal").show();
})
$(".modal a").click(function () {
    $(".modal").hide();
})
```

### __스크립트 실행 원리__ <br/>

* 전체 코드를 살펴보면 클래스 명 __notice__ 의 자식인 __ul__ 안에 있는 __첫번째 li__ 를 누를경우 jQuery가 실행되어 클래스 명 __modar__ 이 나타나게 됩니다. 그리고 modal 나타난 상태에서 modal 의 a 태그를 누르면 다시 사라지게끔 코드가 짜여있습니다. 그럼 이제 코드를 하나씩 살펴보기 전에 modal의 html과 css를 보여드리겠습니다.<br/>

#### __html, css 구조__
해당 포스팅에서는 전체적인 구조를 구성하는 방법에 대해서는 다루고 있지 않습니다. 아래의 코드들은 그저 예시로만 봐주세요.<br/>

```html
<div class="modal">
    <h4>서울 둘레길 공사중</h4>
    <p>안녕하세요. 서울 생태 공원입니다.
        이번에 사고 예방을 위해 다시 정비를 하게 되어 아래 안내 기간동안의
        통행이 불가 하게 되었습니다.
        이용에 불편을 드려 죄송합니다.
    </p>
    <a href="#" class="popup_clpse">닫기</a>
</div>
```

```css
.modal {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    width: 300px;
    height: 300px;
    background-color: #ffffff;
    border: 4px solid #9c9398;
    padding: 20px;
    z-index: 20000;
    display: none;
}

.modal h4 {
    font-size: 24px;
    margin-bottom: 15px;
}

.modal a {
    display: inline-block;
    padding: 2px 20px;
    background-color: #d9cfcf;
    color: #ffffff;
    position: absolute;
    left: 50%;
    bottom: 20px;
    transform: translateX(-50%);
}
```


#### __modal 팝업창 보이기__

```javascript
$(".notice ul li:nth-child(1)").click(function () {
    $(".modal").show();
})
```

##### __하나씩 살펴보기__

```javascript
$(".notice ul li:nth-child(1)")
```

* 이 선택자는 .notice 클래스를 가진 요소 내부의 ul 태그 아래에 있는 li 태그들 중 __첫 번째(nth-child(1)) 요소를 지정__ 합니다. <br/>

 <br/>

```javascript
.click(function () { ... })
```

* 지정된 요소에 클릭 이벤트 핸들러를 추가합니다. 이 경우 첫 번째 li 요소에 대한 클릭 이벤트입니다. <br/>

 <br/>

```javascript
$(".modal").show();
```

* 클릭 이벤트가 발생할 때 실행될 코드로, .modal 클래스를 가진 요소를 찾아서 보이게(show) 합니다. <br/>


#### __modal 팝업창 닫기__

```javascript
$(".modal a").click(function () {
    $(".modal").hide();
})
```

##### __하나씩 살펴보기__

```javascript
$(".modal a")
```

* modal 클래스를 가진 요소 내부에 있는 모든 a 태그(링크)를 선택합니다. 다만 이번의 경우에는 a 태그가 하나뿐입니다. <br/>

 <br/>

```javascript
.click(function () { ... })
```

* 위와 같이 클릭 이벤트 핸들러를 추가하는데, 이번에는 .modal 내의 모든 a 태그에 적용됩니다. <br/>

 <br/>

```javascript
$(".modal").hide();
```

* 클릭 이벤트가 발생하면, .modal 클래스를 가진 요소를 찾아 숨깁니다(hide). <br/>


#### 이상 modal 부분의 jQuery 였습니다.