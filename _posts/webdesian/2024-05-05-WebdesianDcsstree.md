---
layout: post
title: 웹 디자인기능사 실기 D유형 css footer
date: 2024-05-05 15:08 +0900
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


### __웹디자인기능사 실기 D유형의 CSS footer__
* header <br/>
* main <br/>
* footer ✔️<br/>

## __footer의 전체 구조__

![footer2](https://github.com/sunhew/sunhew.github.io/assets/161446039/17780bd2-95ea-4538-9cf8-fb1cd14c98fe)

![footer1](https://github.com/sunhew/sunhew.github.io/assets/161446039/9ba94d08-091e-4c32-9e61-c14ac6dd9eaa)

```css
/* footer */
#footer {
    width: 100%;
    height: 100px;
    background-color: #ffdbdb;
    display: flex;
}

.title {
    width: 200px;
    height: 100px;
    background-color: #d8bbbb;
}

.copy {
    width: 80%;
    height: 100px;
    background-color: #eed7ec;
    text-align: center;
    line-height: 4;
}

.copy p {
    font-size: 24px;
    color: #ffffff;
}

.family {
    width: 20%;
    height: 100px;
    text-align: center;
    background-color: #dfc1d4;
}

.family select {
    appearance: none;
    width: 50%;
    height: 40px;
    font-size: 16px;
    margin-top: 30px;
    text-align: center;
    border-radius: 20px 0;
    background-color: #d5e6d7;
    border: 2px solid #000000;
}

/* modal */
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

### __코드 설명__

#### __.title 스타일 설정__

![foologo](https://github.com/sunhew/sunhew.github.io/assets/161446039/d321afc3-dd88-46d3-a485-bdffa5b039bc)

```html
<div class="title">
    <h1 class="logo">
        <a href="#">서울 구석구석</a>
    </h1>
</div>
```

```css
.title {
    width: 200px;
    height: 100px;
    background-color: #d8bbbb;
}
```

타이틀의  __h1태그에 클래스 logo__ 를 줬습니다. 이유는 클래스는 중복 사용이 가능해서 처음 헤더 부분에서 설정했더 logo의 css를 재사용 가능하기 때문입니다.

* __width__ : footer의 전체 너비안에서 200px만큼 고정합니다. <br/>
* __height__: 높이 값을 100px로 고정했습니다.<br/>
* __background-color__: 배경 색상을 지정합니다.<br/>

#### __.copy의 스타일 설정__

![copy](https://github.com/sunhew/sunhew.github.io/assets/161446039/14da64f0-e8f7-4074-87a2-7a53121b9f36)

```html
<div class="copy">
    <p>COPYRIGHT 2024, ALL Rights Reserve</p>
</div>
```

```css
.copy {
    width: 80%;
    height: 100px;
    background-color: #eed7ec;
    text-align: center;
    line-height: 4;
}

.copy p {
    font-size: 24px;
    color: #ffffff;
}
```

##### __copy__
* __width 및 height__: 각각 80%와 100px로 설정하여, 부모 요소(#footer) 대비 상대적 크기를 결정합니다.<br/>
* __background-color__: 배경 색상을 지정합니다.<br/>* __text-align center__: 텍스트를 중앙에 위치하게 합니다.<br/>
* __text-align center__: 텍스트를 중앙에 위치하게 합니다.<br/>
* __line-height__: 텍스트의 줄 높이를 지정합니다.<br/>

##### __copy p__
* __font-size__: 폰트 사이즈를 24로 설정합니다.<br/>
* __color__: 색상을 지정합니다.<br/>

#### __.family의 스타일 설정__

![sle](https://github.com/sunhew/sunhew.github.io/assets/161446039/59f41a34-4fe3-4da2-8c99-30bb74703d5d)

```html
<div class="family">
    <select>
        <option value="1">서울 생태공원</option>
        <option value="2">서울 타워</option>
        <option value="3">서울 테마파크</option>
    </select>
</div>
```

```css
.family {
    width: 20%;
    height: 100px;
    text-align: center;
    background-color: #dfc1d4;
}

.family select {
    appearance: none;
    width: 50%;
    height: 40px;
    font-size: 16px;
    margin-top: 30px;
    text-align: center;
    border-radius: 20px 0;
    background-color: #d5e6d7;
    border: 2px solid #000000;
}
```

##### __family__
* __width 및 height__: 각각 20%와 100px로 설정하여, 부모 요소(#footer) 대비 상대적 크기를 결정합니다.<br/>
* __text-align center__: 텍스트를 중앙에 위치하게 합니다.<br/>
* __background-color__: 배경 색상을 지정합니다.<br/>

##### __family select__
* __appearance none__: 요소에 기본적으로 적용되는 브라우저의 스타일이나 테마를 제거하는 데 사용됩니다.<br/>
* __width 및 height__: 각각 50%와 40px로 설정하여, 부모 요소(.family) 대비 상대적 크기를 결정합니다.<br/>
* __font-size__: 폰트의 크기를 16px로 설정합니다.<br/>
* __margin-top__: 요소 위쪽에 30픽셀의 마진을 추가하여 다른 요소와의 간격을 조절합니다. <br/>
* __text-align center__: 텍스트를 중앙에 위치하게 합니다.<br/>
* __border-radius__: 모서리의 둥글기의 정도를 설정합니다.<br/>
* __background-color__: 배경 색상을 지정합니다.<br/>
* __border__: 요소 주변에 2픽셀 두께의 검은색 실선 테두리를 추가합니다. <br/>

#### __.modal의 스타일 설정__

![moder](https://github.com/sunhew/sunhew.github.io/assets/161446039/dd58d802-930f-4d40-b555-75b57d4f1e85)

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
<!-- //modal -->
```

```css
/* modal */
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

##### __modal__
* __position absolute__: 모달을 페이지의 __slider_wrap__ 에 배치합니다.<br/>
* __left, top__: 페이지를 화면의 중앙에 위치하게 하기 위해 각각 50%로 지정했습니다.<br/>
* __transform translate__: 모달의 중심을 정확하게 페이지 중앙에 맞추기 위해 각각 -50%가 지정되었습니다.<br/>
* __width height__: 넓이와 높이를 300px로 설정했습니다.<br/>
* __background-color__: 배경 색상을 지정합니다.<br/>
* __border__: 요소 주변에 4px 두께의 실선 테두리를 추가합니다. <br/>
* __padding__: 내부 여백을 20px로 설정합니다. <br/>
* __z-index__: 다른 요소들과 겹칠 때, 모달이 가장 위에 위치하도록 z-index 값을 20000으로 설정합니다. <br/>
* __display none__: 특정 조건을 만족할때에만 보여야 하기에 기본적으로 modal을 숨깁니다. <br/>

##### __modal h4__
* __font-size__: 글자의 크기를 24px로 지정합니다..<br/>
* __margin-bottom__: 제목 아래의 여백을 밑으로 15px 설정합니다. <br/>

##### __modal a__
* __display inline-block__: 링크를 인라인 블록 요소로 설정하여, padding 등의 블록 레벨 속성을 적용할 수 있습니다.<br/>
* __padding__: 링크 내부 여백을 상하 2px, 좌우 20px로 설정합니다.<br/>
* __background-color__: 배경 색상을 지정합니다.<br/>
* __position absolute__: 링크를 절대 위치로 설정합니다.<br/>
* __left, bottom__: a태그를 모달의 가로 중앙에 배치하고 하단에서 20PX 위에 위치시캅니다.<br/>
* __transform translate__: 가로 중앙 정렬을 맞추기 위해 -50%를 넣어서 위치를 지정했습니다.<br/>