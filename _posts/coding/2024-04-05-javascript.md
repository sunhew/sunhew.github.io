---
layout: post
title: 자바스크립트 while문, do while문 활용하기
date: 2024-04-05 18:20 +0900
description:
image: ../assets/img/favicons/javascript01.jpg
category: 자바스크립트
tags: 함수 자바스크립트 while문 dowhile문 활용 
published: true
sitemap: true
---

# 자바스크립트 함수
#### <span style = "color: red" >While문</span> 이란?
> while문은 프로그래밍에서 반복적으로 코드 블록을 실행하는 제어 구조 중 하나입니다. 주어진 조건이 참(True)인 동안 코드를 반복해서 실행합니다. 조건이 거짓(False)이 될 때까지 반복이 계속됩니다. 이를 통해 반복 작업을 간단하게 처리할 수 있습니다. 종종 반복 횟수가 정해지지 않은 경우에 사용됩니다.

for문이랑 비슷하다고 생각하면 편하다.
<br>

👍 활용 예시 👍 <br>

- 1부터 10까지 출력하기 

````javascript
{
    let num = 1;            // 초깃값
    while (num <= 10) {     // 조건식;
        console.log(num);   // 실행문
        num++;  // 증감값;
    }
}
````
<div class="result">
<details>
   <summary>결과 확인하기</summary>
   <div>
         <b> 1~10 </b>
   </div>
</details>
</div>

<br>
While문을 보면 앞에 했던 for문이랑 비슷하다는 점을 볼 수가 있다. for문에서는 for 문안에다가 변수를 선언하고 그 변수의 값이 어떤 값보다 큰지 작은지를 구별 후 값을 ++ 했었는데 While문은 먼저 초깃값을 설정하고 조건식을 건 후 실행문을 그 다음에 넣고 증감값을 마지막에 넣은 것을 볼 수가 있다. 다른 활용 예제를 보고 기억하고 넘어가도록 하자 
<br><br>

- for문이랑 같은 1부터 100까지 출력 하는 것을  while문으로 해볼것이다.

```javascript
  {
        let num = 1;
        while (num <= 100) {
            console.log(num);
            num++;
        }
    }
```
<div class="result">
<details>
   <summary>결과 확인하기</summary>
   <div>
         <b> 1~100 </b>
   </div>
</details>
</div>
<br>

앞에 했던 for문을 기억하고 있었다면 while문을 이해하는것은 쉬울것이다.
for문이랑 다른것은 초깃값을 먼저 선언한 후 조건식을 달았다는 점이다. 이 부분만 알고 넘어가면 for문이랑 while문에 차이 점을 명확하게 짚고 넘어갈 수 있을것이다.

<br>
다음으로 do while문에 대해 알아보자

#### <span style = "color : red"> do while문 </span> 이란?
> `do-while`문은 프로그래밍에서 반복적으로 코드 블록을 실행하는 제어 구조 중 하나입니다. `do-while`문은 `while`문과 유사하지만, 코드 블록을 실행한 후 조건을 검사합니다. 따라서 최소한 한 번은 코드 블록이 실행됩니다. 조건이 참(True)인 경우 코드 블록을 계속해서 반복 실행하고, 조건이 거짓(False)이 되면 반복을 멈춥니다. 이를 통해 일단 코드를 실행한 후에 조건을 검사할 수 있습니다. 일부 프로그래밍 언어에서는 `do-while`문을 지원하지 않을 수도 있습니다.

<br>

👍 활용 예시 👍

- 1부터 10까지 출력하기

```javascript
{
    let num = 1;    // 초깃값;

    do {
        console.log(num);   //  실행문
        num++;              // 증감값;
    } while (num <= 10);     // 조건식
}
```
<div class="result">
<details>
   <summary>결과 확인하기</summary>
   <div>
         <b> 1~10 </b>
   </div>
</details>
</div>
<br>

while문이랑 확실하게 다른점이 눈에 보인다.
while문 같은 경우 초깃값을 먼저 선언 후 조건식을 달았지만 do while문 같은 경우 초깃값을 선언 후 do 를 이용해 실행문과 증감밗을 불러온 다음 조건식을 선언하였다는 점이다. 두 함수가 같아보여도 쓰이는건 다르니 확실하게 기억하고 넘어가야한다.
>while문은 초기값 선언 -> 조건식 -> 실행문 > 증감값 이고 do while문은  초깃값 선언 -> do 실행문 -> 증감값 -> 조건식이다. 
<br>

👍 활용 예시 👍

- do while문으로 1부터 100까지 출력 
```javascript
{
    {
        let num = 1;
        do {
            console.log(num);
            num++;
        } while (num <= 100);
    }
}
```
while문이랑 다르게 do가 들어갔다는 것을 꼭 알고 넘어가도록 하자!! 

다음시간에 계속.