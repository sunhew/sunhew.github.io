---
layout: post
title: 자바스크립트의 연산자들 마무리
date: 2024-04-06 12:28 +0900
description:
image: ../assets/img/favicons/javascript01.jpg
category: 자바스크립트
tags:
published: true
sitemap: true
---

# 자바스크립트 함수
#### <span style = "color:#fabdbd" >연산자</span> 라는게 뭘까요?
> 자바스크립트에서 사용되는 다양한 연산자에 대해 코드로 크게 "논리 연산자", "산술 연산자", "비교 연산자", "조건(삼항) 연산자", "할당 연산자", "증가 및 감소 연산자", "문자열 연결 연산자" 로 구분할 수 있습니다.
<br>

  #연산자의 종류를 자세하게!# <br>

- 할당 연산자 

````javascript
{
        let g = 10;
        g += 5; // g = g + 5와 동일
        console.log(g); // 15
        
        g *= 2; // g = g * 2와 동일
        console.log(g); // 30
}
````
할당 연산자는 변수에 값을 할당할 때 사용됩니다.
<br><br>

- 증가 및 감소 연산자

```javascript
{
        let h = 10;
        console.log(h++); // 10 (후위 증가 연산자, 출력 후 증가)
        console.log(++h); // 12 (전위 증가 연산자, 증가 후 출력)
        
        let i = 10;
        console.log(i--); // 10 (후위 감소 연산자, 출력 후 감소)
        console.log(--i); // 8  (전위 감소 연산자, 감소 후 출력)
}
```
증가 및 감소 연산자는 변수의 값을 증가 시키거나 감소 시킬 수 있는 방법인데 연산자 기호가 어디에 붙냐에 따라 값이 변 할 수있으니 잘 확인 하셔야합니다.

- 문자열 연결 연산자

```javascript
{
        let firstName = "홍";
        let lastName = "길동";
        
        console.log(firstName + " " + lastName); // "홍 길동"
}
```
문자열 연결 연산자의 경우에는 문자열을 연결할때, 혹은 출력되는 값 사이에 문자열을 추가하고 싶을때 사용합니다, 
<br>

이렇게 마지막 연산자까지 설명이 끝났네요! 다음 포스팅때는 자바스크립트의 자료형으로 찾아오겠습니다.