---
layout: post
title: 자바스크립트의 연산자들
date: 2024-04-05 18:20 +0900
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

- 산술 연산자 

````javascript
{
        let a = 10;
        let b = 5;
        
        console.log(a + b); // 15 (더하기)
        console.log(a - b); // 5  (빼기)
        console.log(a * b); // 50 (곱하기)
        console.log(a / b); // 2  (나누기)
        console.log(a % b); // 0  (나머지)
}
````
산술 연산자는 수학적 계산을 위해 사용되며 각각의 의미를 확실하게 구분해야합니다.
<br><br>

- 비교 연산자

```javascript
{
        let c = 10;
        let d = "10";
        
        console.log(c == d);  // true  (동등 비교, 값만 비교)
        console.log(c === d); // false (일치 비교, 값과 타입 모두 비교)
        console.log(c != d);  // false (부등 비교)
        console.log(c !== d); // true  (불일치 비교)
        console.log(c > d);   // false (크다)
        console.log(c < d);   // false (작다)
        console.log(c >= d);  // true  (크거나 같다)
        console.log(c <= d);  // true  (작거나 같다)
}
```
비교 연산자는 언뜻 보기에는 산술 연산자와 비슷해보이지만 큰 차이점이 있는데, 바로 값을 계산하는것이 아닌 "비교" 하는 것입니다.
" = " ⬅️ 해당 기호가 몇개가 있는지, 혹은 존재하는지는 반드시 확인 해야하는데 그 이유는 바로 비교값이 완전히 달라지기때문입니다.

- 논리 연산자

```javascript
{
        let e = true;
        let f = false;
        
        console.log(e && f); // false (논리적 AND)
        console.log(e || f); // true  (논리적 OR)
        console.log(!e);     // false (논리적 NOT)
}
```
논리 연산자는 논리적 조합을 평가할때 사용됩니다. 이 역시 기호를 잘 살펴본 뒤 사용해야합니다. 
<br>

- 조건(삼항) 연산자
```javascript
{
        let age = 20;

        console.log(age >= 18 ? "성인" : "미성년자"); // "성인"
}
```
조건(삼항) 연산자의 경우에는 조건에 따라 두 개의 값을 변환할 수 있는 유일한 연산자입니다. 
<br>


아직 설명하지 못한 할당 연산자, 증가 및 감소 연산자, 문자열 연결 연산자는 다음 글에서 이어서 설명하겠습니다. 다음에 봐요!