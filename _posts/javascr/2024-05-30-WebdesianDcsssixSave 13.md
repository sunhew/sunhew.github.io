---
layout: post
title: 제이쿼리 메서드 중 attr(), prop() 차이
date: 2024-05-30 14:05 +0900
description: JAVASCRIPT
image: ../assets/img/javascript.png
category: JAVASCRIPT
tags: JAVASCRIPT 제이쿼리 메서드  attr() prop() 차이 제이쿼리_메서드_중_attr()_prop()_차이
published: true
sitemap: true
---

# JAVASCRIPT
해당 포스팅에서는 자바스크립트의 __제이쿼리 메서드 중 attr(), prop() 차이__ 에 대해 다룹니다.<br />


## __JAVASCRIPT__
* 자바스크립트 장단점 <br/>
* 데이터 타입 <br/>
* 데이터 형 변환<br/>
* 불변성을 유지하려면 어떻게..<br/>
* 프로토타입 <br/>
* var, let, const 차이 <br/>
* 호이스팅(Hoisting) <br/>
* es6 문법 특징과 차이<br/>
* this<br/>
* 제이쿼리 메서드 중 attr(), prop() 차이 ✔️<br/>
* 화살표 함수와 일반 함수 차이<br/>
* 스코프(scope)<br/>
* 객체 지향<br/>
* 클로저(closure)<br/>
* 타입스크립트<br/>
* 프로세스<br/>
* 스레드, 싱글 스레드<br/>
* 콜백 함수 / 재귀 함수 차이<br/>
* 콜백 지옥, 콜백 지옥을 해결하는 방법<br/>
* promise / 콜백 지옥<br/>
* ajax<br/>
* 함수 선언식/ 표현식 차이<br/>
* 이벤트 버블링 / 이벤트 캡처 예시<br/>
* 이벤트 위임 (Event Delegation)<br/>
* 렉시컬 환경<br/>
* 프로퍼티<br/>
* stack이 코드 실행할 때 queue에 미뤄두는 것<br/>
* 얕은 복사 / 깊은 복사<br/>
* 동기 / 비동기<br/>

## __jQuery의 attr()와 prop() 차이__<br/>
해당 포스팅에서는 호이스팅(Hoisting)의 __jQuery의 attr()와 prop() 차이__ 에 대해 다룹니다.

### __jQuery의 attr()와 prop() 차이__
__jQuery에서는 HTML 요소의 속성(attribute)과 속성(property)을 조작하기 위해 `attr()`와 `prop` 메서드를 사용__ 합니다. 이 두 메서드는 비슷하게 보이지만, __다루는 대상과 동작 방식에서 중요한 차이__ 가 있습니다. 이를 이해하는 것은 jQuery를 효과적으로 사용하는데 매우 중요합니다.

### __attr() 메서드__

#### __기본 개념__
`attr()` 메서드는 __HTML 요소의 속성을 가져오거나 설정할 때 사용__ 됩니다. HTML속성은 __문서의 정적 구조를 나타내며, 요소가 처음 로드될 때 정의된 값__ 입니다.

#### __사용 예시__

##### __속성 값 가져오기__
아래 코드는 __첫번쨰 `<a>` 요소의 `href` 속성 값을 가져와서 콘솔에 출력__ 합니다. 이 값은 __HTML에서 설정된 정적 속성 값__ 입니다.

```javascript
const hrefValue = $('a').attr('href');
console.log(hrefValue); // 링크의 href 값을 출력
```

##### __속성 값 설정하기__
아래 코드는 __첫번쨰 `<a>` 요소의 `href` 속성 값을 `https://www.example.com`으로 설정__ 합니다. 이로 인해 해당 __링크를 클릭하면 설정된 URL로 이동__ 합니다.

```javascript
const hrefValue = $('a').attr('href');
console.log(hrefValue); // 링크의 href 값을 출력
```

##### __여러 속성 설정하기__
아래 코드는 __첫번쨰 `<img>` 요소의 `src`와 `alt` 속성을 각각 `image.jpg`와 `An image`로 설정__ 합니다.

```javascript
$('img').attr({
    src: 'image.jpg',
    alt: 'An image'
});
```

#### __주의사항__
`attr()`메서드는 __요소가 처음 로드될 때 정의된 속성 값만을 반환__ 합니다. 만약 자바스크립트를 통해 __속성 값을 동적으로 변경했다면, `attr()`메서드는 이를 반영하지 않습니다.__

### __prop() 메서드__

#### __기본 개념__
`prop()` 메서드는 __HTML 요소의 속성(property)을 가져오거나 설정할 때 사용__ 됩니다. 속성은 __요소의 현재 상태를 나타내며, DOM 객체의 프로퍼티로 관리__ 됩니다.

#### __사용 예시__

##### __프로퍼티 값 가져오기__
아래 코드는 __첫 번쨰 `<input>` 요소(유형이 체크박스인)의 `checked`프로퍼티 값을 가져와서 콘솔에 출력__ 합니다. 이 값은 __현재 체크박스가 체크되어 있는지 여부__ 를 나타냅니다.

```javascript
const checked = $('input[type="checkbox"]').prop('checked');
console.log(checked); // 체크박스가 체크되어 있는지 여부를 출력
```

##### __프로퍼티 값 설정하기__
아래 코드는 __첫 번째 `<input>` 요소(유형이 체크박스인)의 `checked` 프로퍼티 값을 `true` 로 설정__ 합니다. 이로 인해 체크박스가 체크됩니다.

```javascript
$('input[type="checkbox"]').prop('checked', true);
```

##### __여러 프로퍼티 설정하기__
아래 __코드는 모든 `<input>` 요소의 `disabled` 프로퍼티를 `true`로, `checked` 프로퍼티를 `false`로 설정__ 합니다. 이로 인해 __모든 입력 요소가 비활성화되고, 체크박스는 체크 해제__ 됩니다.

```javascript
$('input').prop({
    disabled: true,
    checked: false
});
```

#### __주의사항__
`prop()` 메서드는 __요소의 현재 상태를 반영__ 합니다. 예를 들어, 동적으로 변경된 체크박스의 상태를 `prop()` 메서드를 통해 정확하게 가져올 수 있습니다.

### __attr()와 prop()의 차이점__

#### __대상__
* __attr()__ : HTML 속성(attribute)을 다룹니다.
* __prop()__ : DOM 프로퍼티(property)를 다룹니다.

#### __반환값__
* __attr()__ : 요소가 __처음 로드될 때의 정적 속성 값을 반환__ 합니다.
* __prop()__ : 요소의 __현재 상태를 나타내는 동적 속성 값을 반환__ 합니다.

#### __사용 시기__
* __attr()__ : 정적 속성 값을 가져오거나 설정할 때 사용합니다. 예를 들어, `href`, `src`, `title` 등.
* __prop()__ : 동적 속성 값을 가져오거나 설정할 때 사용합니다. 예를 들어, `checked`, `disabled`, `selected` 등.

### __예시 코드__

#### __체크박스 예시__
아래 예제에서, __체크박스의 `checked` 속성을 `attr()` 메서드를 사용해 가져오면 초기 HTML 속성 값을 반환__ 합니다. 반면, __`prop()` 메서드를 사용하면 현재 DOM 상태 값을 반환__ 합니다. __체크박스 상태를 변경한 후, `prop()` 메서드는 변경된 상태를 반영하지만 `attr()` 메서드는 여전히 초기 값을 반환__ 합니다.

```html
<input type="checkbox" id="checkbox" checked>
```

```javascript
// 초기 HTML 속성 값
console.log($('#checkbox').attr('checked')); // "checked"

// 현재 DOM 상태 값
console.log($('#checkbox').prop('checked')); // true

// 체크박스의 상태를 변경
$('#checkbox').prop('checked', false);

// 변경 후 확인
console.log($('#checkbox').attr('checked')); // "checked" (변경되지 않음)
console.log($('#checkbox').prop('checked')); // false (변경됨)
```

#### __링크 예시__
이 예제에서는 `<a>` 요소의 `href` 속성을 `attr()` 메서드를 사용해 가져오고 변경합니다. `attr()` 메서드는 정적 HTML 속성을 조작하는 데 사용되므로, `href` 속성을 성공적으로 변경할 수 있습니다.

```html
<a href="https://www.google.com">Google</a>
```

```javascript
// 초기 href 속성 값 가져오기
console.log($('a').attr('href')); // "https://www.google.com"

// href 속성 값 변경
$('a').attr('href', 'https://www.example.com');

// 변경 후 확인
console.log($('a').attr('href')); // "https://www.example.com"
```

### __마무리__
`attr()`와 `prop()` 메서드는 __각각 HTML 속성과 DOM 프로퍼티를 조작하는 데 사용__ 됩니다. __`attr()`는 정적 속성__ 을 다루고, __`prop()`는 동적 속성__ 을 다룹니다. 이 두 메서드를 적절히 사용하면 jQuery로 요소의 속성과 상태를 효과적으로 관리할 수 있습니다!