---
layout: post
title: 웹 디자인기능사 실기 D유형 css header
date: 2024-05-11 22:51 +0900
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


### __웹디자인기능사 실기 D유형의 CSS header__
* header ✔️<br/>
* main <br/>
* footer <br/>

## __폴더 링크 연결확인하기와 언어 설정하기__<br/>

```css
@charset "UTF-8";
```

다시 한번 style 링크가 index와 연결되었는지 확인 한 뒤에 가장 위에 사용할 언어부터 설정해줍니다. 위의 코드는 __CSS 파일이 UTF-8 문자 인코딩을 사용하여 작성되었음을 나타내는 선언__ 입니다. 이 선언은 __CSS 파일의 맨 처음 줄에 위치해야 하며, 다른 어떤 문자나 공백도 이 선언 앞에 오면 안 됩니다.__ UTF-8 인코딩은 국제적으로 가장 널리 사용되는 문자 인코딩 방식 중 하나로, 다양한 언어의 문자를 포함할 수 있으며, 웹 개발에서 표준적으로 사용됩니다. 이 선언을 사용함으로써 CSS 파일 내에서 다양한 언어의 문자를 정확하게 표현하고, 해석될 수 있도록 보장합니다.<br/>

## __기본적인 구조 디자인하기__

![image 7](https://github.com/sunhew/sunhew.github.io/assets/161446039/a3fa16fe-5f38-45ab-9486-2da00e729d20)

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    color: #333;
}

a {
    text-decoration: none;
    color: #333;
}

li {
    list-style: none;
}

#wrap {
    display: flex;
    flex-wrap: wrap;
}

/* header */
#header {
    width: 200px;
    height: 650px;
    background-color: #AA9FA6;
}

/* main */
#main {
    width: calc(100% - 200px);
    height: 650px;
    background-color: #626262;
}

/* footer */
#footer {
    width: 100%;
    height: 100px;
    background-color: #ffdbdb;
    display: flex;
}
```

우선은 시작하기에 앞서 이름을 불러올때 html에서 __id__ 를 줬으면 __#__, __class__ 를 주었다면 __.__ 이 붙어야합니다. id는 한번만 사용가능하고 class는 재사용이 가능하다는 차이점이 있습니다. <br/>
전체 구조를 감싸기 위해 body 태그 안에 &lt;div id __"wrap"__ &gt;을 설정해줍니다. 그 뒤에는 만들어야 하는 사이트의 구조를 살펴본 뒤에 wrap안에 구역별로 나눠줍니다
후에 세부 구조를 구성할때에는 태그들이 더욱 많아지므로 구분할수있게 구역이 끝나는곳마다 주석처리를 해서 보기 쉽게 정리해두면 나중에 해당 영역을 찾아야 할때에 큰 도움이 됩니다.<br/>

### __코드 설명__

#### __전체 스타일 재설정__

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    color: #333;
}
```

* __"*"__ 선택자는 모든 HTML 요소를 대상으로 합니다. <br/>
* __margin__ 0과 padding: 0은 __모든 요소의 기본 마진과 패딩을 제거__ 합니다. 이는 브라우저 간 일관성을 확보하고, 레이아웃을 설계할 때 예상치 못한 여백으로 인한 문제를 방지하기 위함입니다.<br/>
* __box-sizing__: border-box는 __요소의 크기 계산 방법을 변경__ 합니다. 이 설정은 요소의 너비와 높이가 테두리와 패딩을 포함하여 계산되도록 합니다. 이는 레이아웃을 더 예측 가능하게 만듭니다.<br/>
* __color__: #333는 모든 요소의 기본 텍스트 색상을 어두운 회색(#333)으로 설정합니다.<br/>

#### __a와 li의 스타일 재설정__

```css
a {
    text-decoration: none;
    color: #333;
}

li {
    list-style: none;
}
```

* __a__ 선택자는 모든 링크(a 태그)에 적용됩니다. text-decoration: none은 링크 밑줄을 제거하고, color: #333로 링크 색상을 설정합니다.<br/>
* __li__ 선택자는 모든 리스트 항목(li 태그)에 적용됩니다. list-style: none은 리스트 앞의 기본 마커(예: 원형 불릿)를 제거합니다.<br/>

#### __레이아웃 스타일링__

```css
#wrap {
    display: flex;
    flex-wrap: wrap;
}
```

* __#wrap은 ID 선택자로, id="wrap"인 요소에 적용__ 됩니다. __display: flex는 플렉스박스 레이아웃을 활성화__ 하고, __flex-wrap: wrap은 자식 요소들이 부모 요소의 너비를 넘어갈 경우 다음 줄로 넘어가게 합니다.__<br/>

#### __기본구조 스타일링__

```css
#header {
    width: 200px;
    height: 650px;
    background-color: #AA9FA6;
}

#main {
    width: calc(100% - 200px);
    height: 650px;
    background-color: #626262;
}

#footer {
    width: 100%;
    height: 100px;
    background-color: #ffdbdb;
    display: flex;
}
```

* #header, #main, #footer 선택자는 각각 헤더, 메인 콘텐츠, 푸터 영역을 대상으로 합니다.<br/>
* __header__: 너비 200px, 높이 650px로 설정되고, 배경색을 설정했습니다.<br/>
* __main__: 너비가 __header 영역을 제외한 나머지 영역을 차지하도록 calc(100% - 200px)로 설정__ 되었습니다. 실기에서는 (100% - 200px)가 지정되어 있다면 __calc__ 를 사용해야 합니다. 또한 main은 높이는 650px, 배경색은 어두운 회색(#626262)입니다.<br/>
* __footer__: 너비가 전체 페이지를 차지하도록 100%, 높이는 100px로 설정했습니다.<br/>

## __헤더 부분의 logo, nav 디자인하기__

![header1](https://github.com/sunhew/sunhew.github.io/assets/161446039/9b38a073-c4c8-4d35-bd93-7627a5781602)
![header2](https://github.com/sunhew/sunhew.github.io/assets/161446039/6228ede6-a1a9-4bb4-8526-c9565421de14)

```css
/* header */
#header {
    width: 200px;
    background-color: #AA9FA6;
}

.logo {
    height: 100px;
    line-height: 100px;
    text-align: center;
    background-color: #e0dbde;
}

.logo a {
    color: #fff;
    font-size: 24px;
}

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

구조를 확인해보면 header에는 크게 logo와 nav가 존재하며 각각의 클래스들을 가지고 있습니다. 특히나 nav의 경우에는 __ul안에 다중의 li가 있고 그안에 a가 있는구조__ 이며 한번 더 들어가서는 __li안에 또 다른 ul이 있는구조__ 입니다. 이 경우에는 나중에 찾기 복잡하므로 반드시 주석으로 표시를 해두세요.<br/>

### __코드 설명__

#### __logo__

```css
.logo {
    height: 100px;
    line-height: 100px;
    text-align: center;
    background-color: #e0dbde;
}

.logo a {
    color: #fff;
    font-size: 24px;
}
```

##### __logo__
* __height__: 로고의 높이를 100px로 고정시킵니다.<br/>
* __line-height__: 로고의 높이 위치를 100px로 설정해서 세로 중앙에 위치하게 합니다.<br/>
* __text-align__: 세로 중앙에 있던 로고를 logo 영역의 중앙에 위치하게 합니다.<br/>
* __background-color__: 배경색을 설정합니다.<br/>

##### __logo a__
* __color__: 글자의 색상을 설정합니다.<br/>
* __font-size__: 글자의 크기를 설정하며 폰트마다의 크기는 제각각이니 정확한 수치는 아닙니다.<br/>

#### __메인 내비게이션 (Nav) 스타일링__

```css
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
```

##### __nav의 구조__
html의 구조를 보면 nav의 자식으로는 ul이 있고 그안에 li가, li안에는 a와 또다른 ul이 있는 구조입니다. li의 안에 있는 ul은 서브 메뉴입니다. 또한 __"__&gt;__" 표식은 바로 아래에 있는 자식에게만 적용한다는 뜻__ 이라 다중으로 있을떄 사용하기에 유용합니다. __".nav&gt;ul"__ 부분이 없는 이유는 속성을 주지 않았기 때문에 삭제한것입니다. <br/>

##### __nav &gt; ul &gt;li &gt; a__
* __width: 100%__: a링크의 너비를 __부모 요소의 100%로 설정__ 하여, 전체 너비를 차지하게 합니다. 이는 메뉴 항목이 부모 컨테이너의 전체 너비를 사용하도록 합니다.<br/>
* __padding: 10px__: __nav 내부의 상단, 하단, 좌우에 10픽셀의 패딩을 추가__ 합니다. 이 패딩은 링크의 클릭 가능 영역을 늘f립니다.<br/>
* __display: inline-block__: a 링크를 __인라인 블록 요소__ 로 만듭니다. 이는 __요소가 텍스트처럼 한 줄에 나란히 배열되면서도 블록 요소처럼 너비와 높이를 가질 수 있게 합니다.__ 따라서, 링크가 전체 너비를 차지하면서도 패딩과 마진을 적용할 수 있습니다.<br/>
* __text-align: center__:  __텍스트를 가운데 정렬__ 합니다. 메뉴 항목의 텍스트가 __링크 내에서 가운데 위치__ 하도록 합니다.<br/>
* __font-size: 18px__: 글자의 크기를 설정하며 폰트마다의 크기는 제각각이니 정확한 수치는 아닙니다.<br/>
* __margin-bottom: 5px__: a링크 아래에 __5픽셀의 마진을 추가__ 하여, 다음 메뉴 항목과의 거리를 만듭니다.<br/>
* __color__: 글자의 색상을 지정합니다.<br/>
* __background-color__: a링크의 영역만큼의 배경색을 지정합니다.<br/>

##### __nav &gt; ul &gt;li &gt; a:hover__
* __background-color__: a링크에 마우스를 올리면 색상이 변하게 합니다. 다음에 다룰 jqery에서도 마우스 오버(mouseover) 효과를 사용합니다.<br/>


이상 CSS의 header이였습니다. 메인 부분은 이 포스팅의 두배 정도가 예상됩니다.