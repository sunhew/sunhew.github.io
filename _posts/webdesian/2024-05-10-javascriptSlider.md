---
layout: post
title: 자바스크립트 웹디 슬라이드만 공부하기
date: 2024-05-10 04:12 +0900
description: 자바스크립트 웹디 슬라이드
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

## __슬라이드 전체 코드__<br/>

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

### __스크립트 실행 원리__ <br/>

* 전체 코드를 살펴보면 클래스 명 __slider_wrap__ 의 자식중 클래스명이 __slider__ 의 첫번째 자식을 복사한뒤 css를 이용해 애니메이션 효과를 준뒤 함수를 통해 계속해서 슬라이드를 자연스럽게 위로 올라가는 효과를 줄 수 있습니다.<br/>

#### __html, css 구조__
해당 포스팅에서는 전체적인 구조를 구성하는 방법에 대해서는 다루고 있지 않습니다. 아래의 코드들은 그저 예시로만 봐주세요.<br/>

```html
<div class="sliders">
    <div class="slider_wrap">
        <div class="slider s1">
            <h2>서울 봄꽃 축제 안내</h2>
            <p>2024년 봄꽃 축제를 개최합니다.</p>
        </div>
        <div class="slider s2">
            <h2>서울 봄꽃 축제 안내</h2>
            <p>2024년 봄꽃 축제를 개최합니다.</p>
        </div>
        <div class="slider s3">
            <h2>서울 봄꽃 축제 안내</h2>
            <p>2024년 봄꽃 축제를 개최합니다.</p>
        </div>
    </div>
</div>
```

```css
.slider_wrap {
    width: 100%;
    height: 400px;
    display: flex;
    position: relative;
    flex-direction: column;
}

.slider_wrap .slider {
    width: 100%;
    min-height: 100%;
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
}

.slider_wrap .slider h2 {
    background-color: #0f0f0f23;
    padding: 20px;
    border-radius: 20px;
    color: #ffffff;
}

.slider_wrap .slider p {
    background-color: #0f0f0f39;
    padding: 20px;
    color: #ffffff;
}

.slider_wrap .slider.s1 {
    background-image: url(../images/silder01.jpg);
}

.slider_wrap .slider.s2 {
    background-image: url(../images/silder02.jpg);
}

.slider_wrap .slider.s3 {
    background-image: url(../images/silder03.jpg);
}
```


#### __변수 선언과 함께 첫번째 이미지 복사하기__

```javascript
$(function () {
    let currentIndex = 0;
    $(".slider_wrap").append($(".slider").first().clone(true));
})
```

##### __하나씩 살펴보기__

```javascript
$(function () { ... })
```

* 문서가 준비되면 실행되는 함수입니다. 즉, 웹 페이지의 모든 요소가 로드된 후에 이 코드 블록 내의 스크립트가 실행됩니다. <br/>

 <br/>

```javascript
let currentIndex = 0;
```

* 현재 표시되고 있는 슬라이더의 인덱스를 저장하는 변수입니다. 슬라이더가 처음으로 전환될 때 이 값은 0입니다.<br/>

 <br/>

```javascript
$(".slider_wrap").append($(".slider").first().clone(true));
```

* 현첫 번째 슬라이더(.slider)를 복제하여 .slider_wrap 요소의 마지막에 추가합니다. 이는 슬라이드 효과가 끊어지지 않는것처럼 보이게 하기 위함입니다. <br/>

 <br/>

#### __이미지 슬라이드 실행하기__

```javascript
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
```

##### __하나씩 살펴보기__

```javascript
setInterval(() => { ... }, 3000)
```

* 3초(3000밀리초)마다 괄호 안의 함수를 반복 실행합니다. 이 함수는 슬라이더의 위치를 변경하고, 마지막 슬라이더에 도달했을 때 슬라이더를 처음 위치로 되돌립니다. <br/>

 <br/>

```javascript
currentIndex++;
```

* 함수가 실행될 때마다 currentIndex를 1씩 증가시킵니다. 이는 다음 슬라이더로 전환하기 위함입니다.<br/>

 <br/>

```javascript
$(".slider_wrap").animate({ marginTop: -400 * currentIndex + "px" }, 600);
```

* slider_wrap 요소를 수직으로 이동시키는 애니메이션을 실행합니다.<br/>
* marginTop의 값으로 -400 * currentIndex를 사용하여 현재 인덱스에 해당하는 슬라이더가 보이도록 합니다.<br/>
* 애니메이션의 지속 시간은 600밀리초입니다.<br/>

 <br/>

 <br/>

```javascript
if (currentIndex == 3) { ... }
```

* currentIndex가 3에 도달했을 때 (즉, 마지막 슬라이더에 도달했을 때) 조건문이 실행됩니다.<br/>

 <br/>

```javascript
setTimeout(() => { ... }, 700);
```

* 700밀리초 후에 괄호 안의 함수를 실행합니다. 이는 마지막 슬라이더의 애니메이션이 완료된 후에 실행되도록 하기 위함입니다.<br/>

 <br/>

```javascript
$(".slider_wrap").animate({ marginTop: 0 }, 0);
```

* slider_wrap 요소의 위치를 처음 위치로 즉시 되돌립니다.<br/>
* 애니메이션 지속 시간을 0으로 설정하여 즉각적으로 위치가 변경됩니다.<br/>

 <br/>

 <br/>

```javascript
currentIndex = 0;
```

* currentIndex를 0으로 재설정하여 슬라이더가 다시 첫 번째 이미지부터 시작하도록 합니다.<br/>
