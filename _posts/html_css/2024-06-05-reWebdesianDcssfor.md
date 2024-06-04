---
layout: post
title: CSS 우선순위, Position 속성
date: 2024-06-03 16:00 +0900
description: html & css
image: ../assets/img/htmlcss03.jpg
category: html & css
tags: html&css html CSS css우선순위 Position속성
published: true
sitemap: true
---

# HTML & CSS
해당 포스팅에서는 CSS 우선순위, Position 속성에 대해 다룹니다. 이전에 한번 다뤘었지만 한번 더 복습하는 개념으로 포스팅 했습니다.<br />


## __HTML & CSS 목차__
* 웹 표준, 웹 접근성 <br/>
* 반응형 작업 <br/>
* 레거시 코드, IR 효과 시멘틱 태그<br/>
* CSS 우선순위, Position 속성 ✔️<br/>
* block, inline-block, inline 차이<br/>
* data 속성<br/>
* seo, 최적화 방법, ID vs class 차이<br/>

## __CSS 우선순위__<br/>

### __CSS 우선순위의 개념__
__CSS 우선순위(CSS Specificity)__ 는 __여러 스타일 규칙이 동일한 요소에 적용될 때 어떤 규칙이 우선적으로 적용될지를 결정하는 방법__ 입니다. 우선순위는 선택자의 __특정성(Specificity)__ 과 __중요도(Importance)__ 에 따라 결정됩니다.

### __CSS 우선순위 규칙__

#### __중요도 (Importance)__

* `!important` 가 붙은 규칙은 __우선순위에서 가장 높습니다.__ 다른 어떤 규칙보다 __우선 적용__ 됩니다<br/>

```css
.example {
    color: red !important;
}
```

#### __인라인 스타일 (Inline Style)__

* 인라인 스타일은 `!important` 를 __제외한 다른 어떤 규칙보다 높은 우선순위__ 를 가집니다.<br/>

```css
<div style="color: blue;"></div>
```

#### __특정성 (Specificity)__

* 선택자의 특정성은 선택자의 구성 요소에 따라 계산됩니다. 특정성이 높을수록 우선순위가 높습니다.<br/>

* 특정성은 다음과 같은 규칙에 따라 계산됩니다. <br/>

    1. __인라인 스타일__ : 1,0,0,0
    2. __ID 선택자__ : 0,1,0,0
    3. __클래스, 속성, 가상 클래스 선택자__ : 0,0,1,0
    4. __태그 선택자, 가상 요소 선택자__ : 0,0,0,1

#### __소스 순서 (Source Order)__

* __특정성과 중요도가 동일한 경우, 스타일 규칙이 나중에 정의된 것이 우선 적용__ 됩니다.

### __특정성 계산 방법__
특정성은 __네 자리 숫자(a,b,c,d)로 계산__ 되며, 각 자리수는 다음과 같이 계산됩니다

* __a__: 인라인 스타일 수
* __b__: ID 선택자 수
* __c__: 클래스, 속성, 가상 클래스 선택자 수
* __d__: 태그, 가상 요소 선택자 수

```css
/* 특정성: 0,0,1,1 */
div.class {
    color: red;
}

/* 특정성: 0,1,0,0 */
#id {
    color: blue;
}

/* 특정성: 0,0,2,0 */
.class1.class2 {
    color: green;
}
```

### __우선순위 예제__

```css
<!DOCTYPE html>
<html lang="ko">
<head>

    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Specificity Example</title>
    <style>
        /* 특정성: 0,0,0,1 */
        p {
            color: black;
        }

        /* 특정성: 0,0,1,0 */
        .example {
            color: blue;
        }

        /* 특정성: 0,1,0,0 */
        #unique {
            color: green;
        }

        /* 특정성: 0,0,1,1 */
        p.example {
            color: red;
        }

        /* 특정성: 0,0,1,1, 중요도 높음 */
        p.example {
            color: yellow !important;
        }
    </style>
</head>
<body>
    <p class="example" id="unique">This is a test paragraph.</p>
</body>
</html>
```

위의 예쩨에서 `<p class="example" id="unique">` 요소는 여러 CSS 규칙에 의해 스타일이 적용됩니다. 우선순위에 따라 최종 색상은 다음과 같이 결정됩니다.

|선택자|코드|우선순위|
|---|---|---|
|기본 스타일| `p { color: black; }` |특정성: 0,0,0,1|
|클래스 선택자| `.example { color: blue; }` |특정성: 0,0,1,0|
|ID 선택자| `#unique { color: green; }` |특정성: 0,1,0,0|
|조합 선택자| `p.example { color: red; }` |특정성: 0,0,1,1|
|중요도 높은 규칙| `p.example { color: yellow !important; }` |특정성: 0,0,1,1 (중요도 높음)|

위 표를 살펴보면 `color: yellow` 뒤에 `!important`가 붙어있으므로 최종적으로는 요소의 텍스트는 노란색이 됩니다.

### __우선순위 충돌 해결 방벙__

#### __구체적인 선택자 사용__
* 선택자를 구체적으로 작성하여 특정성을 높입니다.

#### __중요도 조절__
* 가능한 한 `!important` 사용을 피하고, __구조적인 선택자 설계를 통해 해결__ 합니다

#### __스타일 정의 순서__
* 스타일을 __정의하는 순서를 고려__ 하여 후에 정의된 스타일이 우선 적용되도록 합니다.

#### __CSS 리셋 또는 노멀라이즈 사용__
* 브라우저 __기본 스타일을 일관__ 되게 만들기 위해 __CSS 리셋__ 또는 __노멀라이즈__ 를 사용합니다.