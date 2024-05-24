---
layout: post
title: 웹 디자인기능사 실기 D유형 html
date: 2024-05-03 10:48 +0900
description: 웹 디자인기능사 실기 D유형
image: ../assets/img/webdesian.png
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
* HTML ✔️ <br/>
* CSS <br/>
* script(jqery) <br/>

## __폴더 링크 연결과 타이틀 적기__<br/>

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>서울 구석구석</title>
    <link rel="stylesheet" href="css/style.css">
</head>
```

구조를 구성하기 이전에 실기에서는 index 와 css, script를 각각의 폴더에서 작성한 뒤 링크로 연결해야 하기에 css스타일부터 연결한뒤에 &lt;title&gt;에 제목을 적습니다.<br/>

## __기본적인 구조부터 잡기__

![image 7](https://github.com/sunhew/sunhew.github.io/assets/161446039/a3fa16fe-5f38-45ab-9486-2da00e729d20)

```html
<div id="wrap">
        <header id="header">
          
        </header>
        <!-- header -->
        <main id="main">
            
        </main>
        <!-- main -->
        <footer id="footer">
            
        </footer>
        <!-- footer -->

        <div class="modal">
           
        </div>
        <!-- //modal -->
    </div>
```

우선은 전체 구조를 감싸기 위해 body 태그 안에 &lt;div id __"wrap"__ &gt;을 설정해줍니다. 그 뒤에는 만들어야 하는 사이트의 구조를 살펴본 뒤에 wrap안에 구역별로 나눠줍니다. 여기에서는 3단 구조로 갈것이며 공지사항의 글자를 누르면 팝엉창이 나와야하기에 __header, main, footer, modal__ 를 만들었습니다.<br/>
후에 세부 구조를 구성할때에는 태그들이 더욱 많아지므로 구분할수있게 구역이 끝나는곳마다 주석처리를 해서 보기 쉽게 정리했습니다.
나중에 해당 영역을 찾아야 할때에 큰 도움이 됩니다.<br/>

## __메인 구조 잡기__

![image 8](https://github.com/sunhew/sunhew.github.io/assets/161446039/c453db1e-f844-4600-ae1b-7d8dec2b5be8)

```html
<div id="wrap">
        <header id="header">
            <h1 class="logo">
                <a href="#">서울 구석구석</a>
            </h1>
            <nav class="nav">
                <ul>
                    <li><a href="#">지금의 서울</a></li>
                    <li><a href="#">추천</a></li>
                    <li><a href="#">여행지</a></li>
                    <li><a href="#">여행정보</a></li>
                </ul>
            </nav>
        </header>
        <!-- header -->
        <main id="main">
            <section class="cont1">
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
                <div class="banner">
                    <div>
                        <h3>서울 풍경</h3>
                        <p>매력적인 풍경에 빠져보세요.</p>
                        <a href="#">클릭하기</a>
                    </div>
                </div>
            </section>

            <section class="cont2">
                <div class="notice">
                    <h3>공지사항</h3>
                    
                </div>
                <div class="gallery">
                    <h3>서울 구석 갤러리</h3>
                    
                </div>
            </section>
        </main>
        <!-- main -->
        <footer id="footer">
            <div class="title">
                <h1 class="logo">
                    <a href="#">서울 구석구석</a>
                </h1>
            </div>
            <div class="copy">
                <p>COPYRIGHT 2024, ALL Rights Reserve</p>
            </div>
            <div class="family">
                <select>
                    <option value="1">서울 생태공원</option>
                    <option value="2">서울 타워</option>
                    <option value="3">서울 테마파크</option>
                </select>
            </div>
        </footer>
        <!-- footer -->

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
    </div>
```

아직 구조 잡기에 익숙하지 않은 경우에는 __세부 구조를 잡기 전에 반드시 위의 기본적인 구조를 잡은뒤에 반드시 CSS 스타일까지 설정해서 원하는대로 영역이 적용되었는지 확인 후에 넘어가야합니다.__ 그렇지 않으면 어디서부터 잘못된것인지 찾기 힘들어집니다.<br/>

이어서 기본 구조를 완성한 뒤에는 세부 구조를 잡게 되는데 웹 디자인 기능사 실기시험의 경우에는 대부분의 구조안에 메인 메뉴와 서브메뉴가 있어 우선적으로는 메인 구조부터 잡은 뒤에 서브 구조를 잡겠습니다. 그리고 슬라이드 부분은 CSS에서 다룰 예정입니다.<br/>

* &lt;a href="#"&gt; 의 작성 이유는 웹 표준중 하나인 __tab__ 키만으로도 이동할 수있어야 한다를 충족시키기 위해 작성되었습니다. 만약 눌렀을때에 다른 링크로 보내고 싶으면 href = __"#"__ 부분에 해당 링크를 적어주세요.<br/>

## __서브 구조 잡기__

![image 9](https://github.com/sunhew/sunhew.github.io/assets/161446039/47e07150-2f5a-404f-8d55-172cafd828b1)

```html

        <header id="header">
            <h1 class="logo">
                <a href="#">서울 구석구석</a>
            </h1>
            <nav class="nav">
                <ul>
                    <li><a href="#">지금의 서울</a>
                        <ul>
                            <li><a href="#">이벤트</a></li>
                            <li><a href="#">축제, 행사</a></li>
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
                            <li><a href="#">가이브북, 지도</a></li>
                            <li><a href="#">시티투어버스</a></li>
                            <li><a href="#">날씨</a></li>
                        </ul>
                    </li>
                </ul>
            </nav>
        </header>
        <!-- header -->
        <main id="main">
            <section class="cont1">
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
                <div class="banner">
                    <div>
                        <h3>서울 풍경</h3>
                        <p>매력적인 풍경에 빠져보세요.</p>
                        <a href="#">클릭하기</a>
                    </div>
                </div>
            </section>

            <section class="cont2">
                <div class="notice">
                    <h3>공지사항</h3>
                    <ul>
                        <li><a href="#">낮과 밤이 아름다운 서울 축제</a><span>2024.04.01</span></li>
                        <li><a href="#">서울 길거리 축제</a><span>2024.04.03</span></li>
                        <li><a href="#">서울 지하철 2호선 운행 시간 변경 안내</a><span>2024.04.06</span></li>
                        <li><a href="#">서울 박물관 특별 전시회 개최</a><span>2024.04.12</span></li>
                        <li><a href="#">서울 지하철 노선 추가 확정</a><span>2024.04.20</span></li>
                    </ul>
                </div>
                <div class="gallery">
                    <h3>서울 구석 갤러리</h3>
                    <ul>
                        <li>
                            <a href="#">
                                <img src="images/galley01.jpg" alt="한옥">
                                <span>서울 한옥</span>
                            </a>
                        </li>
                        <li>
                            <a href="#">
                                <img src="images/galley02.jpg" alt="한옥 정원">
                                <span>한옥 정원</span>
                            </a>
                        </li>
                        <li>
                            <a href="#">
                                <img src="images/galley03.jpg" alt="한옥">
                                <span>서울 풍경</span>
                            </a>
                        </li>
                    </ul>
                </div>
            </section>
        </main>
        <!-- main -->
        <footer id="footer">
            <div class="title">
                <h1 class="logo">
                    <a href="#">서울 구석구석</a>
                </h1>
            </div>
            <div class="copy">
                <p>COPYRIGHT 2024, ALL Rights Reserve</p>
            </div>
            <div class="family">
                <select>
                    <option value="1">서울 생태공원</option>
                    <option value="2">서울 타워</option>
                    <option value="3">서울 테마파크</option>
                </select>
            </div>
        </footer>
        <!-- footer -->

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

여기까지 했다면 html 부분은 모두 끝났습니다. 세부 구조까지 작성하게 되면 구조는 한눈에 파악하기 어려워져 문제 부분을 찾기 힘들어질 수 있으니 반드시 주석을 사용해 정리 해주세요.<br/>

슬라이드가 넘어가는 부분은 jqery로 작성할것이며 마우스 오버 할때의 색상 변경은 CSS, Ui가 나오는 부분은 jqery로 정리하겠습니다!<br/>