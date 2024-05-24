---
layout: post
title: 웹 디자인기능사 실기 D유형 script
date: 2024-05-07 15:13 +0900
description: 웹 디자인기능사 실기 D유형
image: ../assets/img/javascript.png
category: 웹디자인기능사 실기
tags: 웹디자인기능사 실기 D유형
published: true
sitemap: true
---

# 웹디자인기능사 실기 D유형의 HTML.
html, css, script를 한곳에 포스팅 하기에는 너무나도 길어지면서 복잡해지기에 각각 나눠서 정리합니다.
해당 포스팅에서는 html 구조를 다루고있습니다. __작성 방식은 "설정할 스타일 🔜 완성 이미지 🔜 코드 🔜 설명" 입니다.__ <br />
아래의 이미지는 완성된 사이트의 사진입니다. <br />

![image 6](https://github.com/sunhew/sunhew.github.io/assets/161446039/7bb6ce69-fb40-453c-9c13-9953007e8e6e)


### __웹디자인기능사 실기 D유형__
* HTML  <br/>
* CSS <br/>
* script(jqery) ✔️<br/>

## __JQery 사용하기 위해 링크 연결하기__<br/>

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.7.1/jquery.min.js"></script>
```

JQery를 사용하기 위해서는 우선적으로 &lt;script&gt; 위에 링크를 연결해야 합니다. 해당 링크는 <https://developers.google.com/speed/libraries?hl=ko#jquery> 에서 가져올 수 있습니다.<br/>

## __마우스 오버 효과 주기__

![header1](https://github.com/sunhew/sunhew.github.io/assets/161446039/9b38a073-c4c8-4d35-bd93-7627a5781602)
![header2](https://github.com/sunhew/sunhew.github.io/assets/161446039/6228ede6-a1a9-4bb4-8526-c9565421de14)

```javascript
$(".nav > ul > li").mouseover(function () {
    $(this).find(">ul").stop().slideDown();
});
$(".nav > ul > li").mouseout(function () {
    $(this).find(">ul").stop().slideUp();
});
```

### __코드의 세분화__

```javascript
$(".nav > ul > li").mouseover(function () {
    $(this).find(">ul").stop().slideDown();
});
```
__.nav > ul > li__ 에 마우스가 오버되었을때 function안에 있는 함수가 실행됩니다. 이 경우에는 nav의 메인 메뉴에 마우스를 올렸을 경우에 .nav > ul > li의 자식인 ul(서브메뉴)가 아래로 내려오게 됩니다.stop()을 넣는 이유는 반복되서 실행되는것을 막기 위함입니다.<br/>

```javascript
$(".nav > ul > li").mouseout(function () {
    $(this).find(">ul").stop().slideUp();
});
```

위와 비슷하지만 이번에는 __.nav > ul > li__ 에 마우스가 나갔을때 function안에 있는 함수가 실행되어 ul(서브메뉴)가 다시 위로 올라가게 됩니다. <br/>

## __notice의 한 부분을 클릭하면 moder이 나오게 하기__

![moder](https://github.com/sunhew/sunhew.github.io/assets/161446039/dd58d802-930f-4d40-b555-75b57d4f1e85)

```javascript
$(".notice ul li:nth-child(1)").click(function () {
    $(".modal").show();
})
$(".modal a").click(function () {
    $(".modal").hide();
})
```

### __코드의 세분화__

```javascript
$(".notice ul li:nth-child(1)").click(function () {
    $(".modal").show();
})
```

__.notice ul li:nth-child(1)__ notice의 첫번째 자식을 누르면 함수가 실행되어 modal이 나타나게 됩니다.<br/>


```javascript
$(".modal a").click(function () {
    $(".modal").hide();
})
```
__.modal a__ 을 누르면 함수가 실행되어 modal이 다시 숨겨집니다.<br/>

## __슬라이드 이동 시키기__

![banner01](https://github.com/sunhew/sunhew.github.io/assets/161446039/ab0c2108-d475-4058-8949-d85cb46cb69f)

```javascript
$(function () {
    let currentIndex = 0;
    $(".slider_wrap").append($(".slider").first().clone(true));

    setInterval(() => {
        currentIndex++;

        $(".slider_wrap").animate({ marginTop: -400 * currentIndex + "px" }, 600);

        if (currentIndex == 3) {
            setTimeout(() => {
                $(".slider_wrap").animate({ marginTop: 0 }, 0);
                currentIndex = 0;
            }, 700);
        }
    }, 3000)
})
```

### __코드의 세분화__

```javascript
$(function () { ... });
```

문서가 준비되면 주어진 함수를 실행합니다. 이는 jQuery의 준비 이벤트를 의미합니다.<br/>


```javascript
let currentIndex = 0;
```
현재 슬라이더의 인덱스를 추적하는 변수입니다. 초기값은 0으로 설정됩니다.<br/>

```javascript
$(".slider_wrap").append($(".slider").first().clone(true));
```
슬라이더의 첫 번째 항목을 __복제하여(clone(true)) 슬라이더 랩(.slider_wrap)의 마지막에 추가__ 합니다. 이는 무한 슬라이더 효과를 위해 사용됩니다.<br/>

```javascript
setInterval(() => { ... }, 3000)
```
3초마다 주어진 함수를 반복 실행합니다. 이는 슬라이더가 자동으로 넘어가게 하는 타이머 역할을 합니다.<br/>

```javascript
$(".slider_wrap").animate({ marginTop: -400 * currentIndex + "px" }, 600);
```
3슬라이더 랩을 위로 이동시켜 다음 슬라이더를 보여줍니다. __-400 * currentIndex는 슬라이더가 이동해야 하는 거리를 계산__ 합니다. 600은 애니메이션의 지속 시간(밀리초)입니다.<br/>

```javascript
if (currentIndex == 3) { ... }
```
currentIndex가 3일 때, 즉 마지막 슬라이더에 도달했을 때 실행됩니다.<br/>

```javascript
setTimeout(() => { ... }, 700);
```
지정된 시간(700밀리초) 후에 함수를 실행합니다. 이는 마지막 슬라이더에서 첫 번째 슬라이더로 부드럽게 전환하기 위한 대기 시간입니다.<br/>

```javascript
$(".slider_wrap").animate({ marginTop: 0 }, 0);
```
슬라이더 랩의 marginTop을 0으로 설정하여 첫 번째 슬라이더 위치로 즉시 이동합니다.<br/>

```javascript
currentIndex = 0;
```
currentIndex를 0으로 재설정하여 슬라이더 순환을 계속할 수 있게 합니다.<br/>