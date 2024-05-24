---
layout: post
title: 웹 디자인기능사 실기 D유형 css main
date: 2024-05-04 12:48 +0900
description: 웹 디자인기능사 실기 D유형
image: ../assets/img/webdesian.png
category: 웹디자인기능사 실기
tags: 웹디자인기능사 실기 D유형
published: true
sitemap: true
---

# 웹디자인기능사 실기 D유형의 HTML.
html, css, script를 한곳에 포스팅 하기에는 너무나도 길어지면서 복잡해지기에 각각 나눠서 정리합니다.
css을 세부적으로 나누어 다루고있지만 꽤나 길어서 __header, main, footer 나눠서 다룹니다.__ <br/>
__"설정할 스타일 🔜 완성 이미지 🔜 코드 🔜 설명" 입니다.__<br/> 
아래의 이미지는 완성된 사이트의 사진입니다. <br />

![image 6](https://github.com/sunhew/sunhew.github.io/assets/161446039/7bb6ce69-fb40-453c-9c13-9953007e8e6e)


### __웹디자인기능사 실기 D유형의 CSS main__
* header <br/>
* main ✔️<br/>
* footer <br/>

## __main의 전체구조__<br/>

![slider](https://github.com/sunhew/sunhew.github.io/assets/161446039/e0e68bc0-1094-4314-881e-7ec375c9f3b3)

```css
/* main */
#main {
    width: calc(100% - 200px);
    height: 650px;
    background-color: #626262;
}

/* main cont1 */
.cont1 {
    width: 100%;
    display: flex;
}

.cont1 .sliders {
    width: calc(100% - 230px);
    overflow: hidden;
}

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

.cont1 .banner {
    width: 230px;
    height: 400px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: url(../images/banner.jpg) center / cover;
}

.banner>div {
    text-align: center;
    width: 90%;
    height: 90%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    background-color: #4f4f4f5f;
}

.banner>div h3 {
    color: #ffffff;
    font-size: 24px;
}

.banner>div p {
    color: #ffffff;
    padding: 10px;
}

.banner>div a {
    background-color: #000000;
    color: #ffffff;
    padding: 10px 20px;
    border-radius: 50px;
}

/* main cont2 */
.cont2 {
    display: flex;
}

.cont2 .notice {
    width: 50%;
    height: 250px;
    padding: 40px;
    background-color: #e9e9e9;
}

.cont2 .notice h3 {
    font-size: 30px;
    margin-bottom: 10px;
}

.cont2 .notice ul li {
    line-height: 1.7;
    display: flex;
    justify-content: space-between;
}

.cont2 .notice ul li::before {
    content: '*';
}

.cont2 .notice ul li a {
    width: 70%;
    overflow: hidden;
    /* 범위 밖으로 나갔을때 안보임 */
    text-overflow: ellipsis;
    /* 화면 넘어가면 ...으로 표시됨 */
    white-space: nowrap;
    /* 한줄로 나오게 함 위에 두개랑 한 세트 */
}

.cont2 .notice ul li a:hover {
    text-decoration: underline;
    text-decoration-skip: under;
}

.cont2 .notice ul li span {
    width: 30%;
    text-align: right;
}

.cont2 .gallery {
    width: 50%;
    height: 250px;
    padding: 30px;
    background-color: #e4e4e4;
}

.cont2 .gallery h3 {
    font-size: 30px;
    margin-bottom: 10px;
}

.cont2 .gallery ul {
    display: flex;
    justify-content: space-between;
}

.cont2 .gallery ul li {
    text-align: center;
    width: 32%;
}

.cont2 .gallery ul li a img {
    width: 100%;
    max-width: 180px;
    display: block;
    margin: 0 auto;
}

.cont2 .gallery ul li a span {
    margin-top: 5px;
    display: block;
}

.cont2 .gallery ul li a:hover {
    opacity: 0.5;
}
```

메인의 경우에는 너무 길어서 cont1, cont2로 구분지어 정리하겠습니다. 이미지가 움직이는것은 jqery로 코드작성 한 것입니다.<br/>

## __cont1__

![slider1](https://github.com/sunhew/sunhew.github.io/assets/161446039/91bfc5fa-94a1-4b39-adf8-e3f4cf776bdd)

```css
/* main cont1 */
.cont1 {
    width: 100%;
    display: flex;
}

.cont1 .sliders {
    width: calc(100% - 230px);
    overflow: hidden;
}

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

.cont1 .banner {
    width: 230px;
    height: 400px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: url(../images/banner.jpg) center / cover;
}

.banner>div {
    text-align: center;
    width: 90%;
    height: 90%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    background-color: #4f4f4f5f;
}

.banner>div h3 {
    color: #ffffff;
    font-size: 24px;
}

.banner>div p {
    color: #ffffff;
    padding: 10px;
}

.banner>div a {
    background-color: #000000;
    color: #ffffff;
    padding: 10px 20px;
    border-radius: 50px;
}
```

### __코드 설명__

#### __.cont1과 그 하위의 클래스틀의 스타일__

```css
.cont1 {
    width: 100%;
    display: flex;
}

.cont1 .sliders {
    width: calc(100% - 230px);
    overflow: hidden;
}

.cont1 .banner {
    width: 230px;
    height: 400px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: url(../images/banner.jpg) center / cover;
}
```

##### __cont1__
* __width__: 부모 요소의 100%로 설정하여, 부모 요소의 전체 너비를 차지하도록 합니다.<br/>

##### __.cont1 .sliders__
* __width__: 부모 요소인 __cont1의 너비인 100%에서 230px을 뺀 값__ 으로 계산하여 설정합니다. <br/>
* __overflow hidden__:  .sliders __요소의 경계를 넘어서는 내용을 숨깁니다.__ <br/>

##### __.cont1 .banner__
* __width__: 넓이를 230px로 설정합니다<br/>
* __height__: 높이를 400px로 설정합니다<br/>
* __display flex__: 배너 내의 항목들을 가로로 정렬시켜 배치합니다. <br/>
* __align-items center, justify-content center__:  Flexbox의 정렬 속성을 사용하여 배너 내의 항목들을 수직 및 수평 중앙에 배치합니다. <br/>
* __background url()center / cover__: Flexbox의 정렬 속성을 사용하여 배너 내의 항목들을 수직 및 수평 중앙에 배치합니다. <br/>


#### __slider_wrap의 스타일 설정__

![banner01](https://github.com/sunhew/sunhew.github.io/assets/161446039/ab0c2108-d475-4058-8949-d85cb46cb69f)

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

##### __.slider_wrap__
* __width__: 부모 요소의 100%로 설정하여, 부모 요소의 전체 너비를 차지하도록 합니다.<br/>
* __height__: 슬라이더의 높이를 400px로 고정합니다.<br/>
* __display flex__: 슬라이더 내의 항목들을 가로로 정렬시켜 배치합니다.<br/>
* __position relative__: 슬라이더 내부의 절대 위치를 가진 항목들이 기준이 될 수 있도록 설정합니다.<br/>
* __flex-direction column__: 슬라이더 내의 항목들을 세로 방향으로 정렬합니다.<br/>

##### __.slider_wrap .slider__
* __width__: 부모 요소의 100%로 설정하여, 부모 요소의 전체 너비를 차지하도록 합니다.<br/>
* __min-height__: 최소 높이를 부모 요소의 100%로 설정하여 내용에 관계없이 항상 전체 높이를 유지합니다.<br/>
* __background-size cover__: 배경 이미지가 슬라이더 요소의 크기에 맞춰 조절되도록 합니다.<br/>
* __background-position center__: 배경 이미지가 슬라이더의 중앙에 위치하도록 합니다.<br/>
* __background-repeat no-repeat__: 배경 이미지가 반복되지 않도록 설정합니다.<br/>
* __align-items center, justify-content center__: 항목들을 수직 및 수평 중앙에 배치합니다.<br/>
* __flex-direction column__: 슬라이더 내의 항목들을 세로 방향으로 정렬합니다.<br/>

##### __.slider_wrap .slider h2, .slider_wrap .slider p__
* __background-color__: 텍스트 배경색으로 투명도를 포함한 색상을 설정합니다.<br/>
* __padding__: 내용과 테두리 사이의 여백을 설정합니다.<br/>
* __border-radius__: 모서리의 둥글기의 정도를 설정합니다. <br/>
* __color__: 텍스트 색상을 설정합니다. <br/>

##### __.slider_wrap .slider.s1, .slider_wrap .slider.s2, .slider_wrap .slider.s3__
* __background-image__: 각 슬라이더에 특정 배경 이미지를 설정합니다.<br/>

#### __.banner 스타일 설정__

![banner02](https://github.com/sunhew/sunhew.github.io/assets/161446039/6abfbe3f-e06f-4b86-bb7b-3c860198df50)

```css
.banner>div {
    text-align: center;
    width: 90%;
    height: 90%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    background-color: #4f4f4f5f;
}

.banner>div h3 {
    color: #ffffff;
    font-size: 24px;
}

.banner>div p {
    color: #ffffff;
    padding: 10px;
}

.banner>div a {
    background-color: #000000;
    color: #ffffff;
    padding: 10px 20px;
    border-radius: 50px;
}
```

##### __.banner&gt;div__
* __text-align center__: 텍스트를 중앙에 위치하게 합니다.<br/>
* __width 및 height__: 각각 90%로 설정하여, 부모 요소(.banner) 대비 상대적 크기를 결정합니다.<br/>
* __display flex__: 배너 내의 항목들을 가로로 정렬시켜 배치합니다.<br/>
* __align-items center, justify-content center__: 배너 내의 항목들을 수직 및 수평 중앙에 배치합니다.<br/>
* __flex-direction column__: 배너 내의 항목들을 세로 방향으로 정렬합니다.<br/>
* __background-color__: 배경 색상을 지정합니다.<br/>

##### __.banner&gt;div h3__
* __color__: h3 태그의 텍스트 색상을 변경합니다.<br/>
* __font-size__: h3 태그의 글자 크기를 지정합니다.<br/>

##### __.banner&gt;div p__
* __color__: p 태그의 텍스트 색상을 변경합니다.<br/>
* __padding__: 내용과 테두리 사이의 여백을 설정합니다.<br/>

##### __.banner&gt;div a__
* __background-color__: 배경 색상을 지정합니다.<br/>
* __color__: a 태그의 텍스트 색상을 변경합니다.<br/>
* __padding__: div박스 내부의 상하(10px)와 좌우(20px) 공간을 추가하여 텍스트 주변에 여백을 설정합니다.<br/>
* __border-radius__: 모서리의 둥글기의 정도를 설정합니다.<br/>