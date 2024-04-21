---
layout: post
title: CSS display 정리
date: 2024-04-21 21:08 +0900
description: CSS의 속성들 정리 세번째
image: ../assets/img/css.png
category: CSS 속성
tags: CSS 속성
published: true
sitemap: true
---

# CSS의 속성들의 정보 정리 세번째.
### CSS의 속성 목록
* ~~transform~~ <br/>
* ~~position~~ <br/>
* ~~display~~ <br/>
* transition <br/>
* z-index <br/>
* height: inherit <br/>

## __transition의 속성들__<br/>
CSS의 transition 속성은 __요소의 스타일 변경이 일어날 때 그 변화를 일정 시간에 걸쳐 부드럽게 전환하도록 설정하는데 사용__ 됩니다. 이를 통해 __간단한 애니메이션 효과를 생성할 수 있으며, 사용자 인터페이스의 상호작용을 더 부드럽고 매력적__ 으로 만들 수 있습니다. 또한 성능 상의 이유로, 가능하면 __opacity와 transform과 같은 속성에 전환 효과를 적용__ 하는 것이 좋습니다. 이들은 브라우저에서 __하드웨어 가속을 사용할 수 있기 때문에 더 부드럽고 효율적인 애니메이션 효과__ 를 낼 수 있습니다.<br/>

1. transition-property <br/>
2. transition-duration<br/>
3. transition-timing-function<br/>
4. transition-delay<br/>

---
### __transition-property__ <br/>
transition-property는 CSS에서 요소의 __스타일 변경이 시간에 따라 어떻게 전환될지를 정의할 때 사용하는 속성__ 입니다. 이는 CSS 트랜지션(transition) 기능의 일부로, 사용자 인터페이스의 상호작용을 보다 __부드럽고 시각적으로 매력적__ 으로 만드는데 활용됩니다. <br/>

```css
transition-property: none all property;
```

#### __구문__
* __none__: 어떠한 속성도 전환되지 않음을 의미합니다.<br/>

* __all__: 요소의 모든 속성이 전환 대상에 포함됩니다. 이는 기본값입니다.<br/>

* __property__: 전환을 적용하고자 하는 특정 속성의 이름을 지정합니다. 여러 속성에 대해 전환을 적용하고자 할 경우, 쉼표로 구분하여 나열할 수 있습니다.<br/>

```css
div {
  transition-property: background-color, transform;
  transition-duration: 2s, 1s;
  transition-timing-function: linear, ease-in;
}
```

위 예시에서는 div 요소에 대해 __background-color와 transform 속성에 트랜지션이 적용__ 됩니다. __background-color는 2초 동안, transform은 1초 동안 각각 전환__ 됩니다. 또한, __background-color는 linear 타이밍 함수를, transform은 ease-in 타이밍 함수를 사용__ 합니다.

#### __주의사항__
* 상, 하, 좌, 우 마진과 패딩을 적용할 수 있으며, 이는 요소의 크기와 페이지 내 위치에 영향을 줍니다.<br/>

##### __transition-property는 특정 속성에 대한 전환을 지정할 때 사용__
* 전환의 지속 시간(transition-duration), 타이밍 함수(transition-timing-function), 그리고 전환 지연 시간(transition-delay)과 함께 사용됩니다.<br/>

##### __모든 CSS 속성이 트랜지션 효과와 호환되는 것은 아니다.__
* 대체로 시각적 속성(예: __opacity, transform__)에 트랜지션을 적용하는 것이 더 효과적입니다.<br/>

##### __주로 사용되는 부분__
* 트랜지션은 사용자 상호작용에 의해 스타일이 변경될 때(예: __호버(Hover), 포커스(Focus), 클릭(Click)__) 주로 사용됩니다.<br/>

---
### __transition-duration__
transition-duration 속성은 CSS에서 요소의 __전환 효과가 지속되는 시간을 정의__ 합니다. 이 속성은 __요소의 스타일이 어떻게 변화할지를 결정하는 transition-property와 함께 사용되어, 스타일 변화가 시작되어 완료되기까지의 지속 시간을 지정__ 합니다. <br/>

#### 예시 첫번째

```css
transition-duration: 시간;   
```

#### __구문__
* __none__: 어떠한 속성도 전환되지 않음을 의미합니다.<br/>

* __all__: 요소의 모든 속성이 전환 대상에 포함됩니다. 이는 기본값입니다.<br/>

* __property__: 전환을 적용하고자 하는 특정 속성의 이름을 지정합니다. 여러 속성에 대해 전환을 적용하고자 할 경우, 쉼표로 구분하여 나열할 수 있습니다.<br/>

##### __텍스트나 다른 인라인 요소와 함께 묶여서 표시__ <br/>
* 인라인 요소는 텍스트나 다른 인라인 요소와 함께 한 줄에 나란히 배치됩니다.<br/>

#### __사용 사례__ <br/>

##### __텍스트 강조__ <br/>
* span 태그는 텍스트 일부분에 스타일을 적용할 때 사용합니다.<br/>

##### __링크__ <br/>
* a 태그는 하이퍼링크를 생성하며 기본적으로 인라인 요소입니다.<br/>

##### __텍스트 요소__ <br/>
* __strong, em__ 등의 태그는 텍스트를 강조하거나 기울이기 위해 사용되며 인라인 요소입니다.<br/>

---
### __transition-timing-function__ <br/>
display: inline-block은 CSS에서 사용되는 속성 값으로, 해당 속성을 가진 요소는 인라인(inline) 요소처럼 동작하지만, 블록(block) 요소의 특성도 일부 가집니다. 이는 display: inline과 display: block의 중간 형태로 볼 수 있습니다. 특히 메뉴 바, 이미지 격자 등을 구현할 때 유용하게 사용됩니다. 그러나 현대 웹 디자인에서는 __Flexbox나 Grid와 같은 레이아웃 시스템이 더 선호되는 추세입니다.__ 그럼에도 불구하고, __inline-block은 여전히 간단한 레이아웃을 구현할 때 유용한 도구__ 입니다.<br/>

```html
<div class="container">
  <span class="inline-block-example">Text 1</span>
  <span class="inline-block-example">Text 2</span>
</div>
```

```css
.inline-block-example {
  display: inline-block;
  width: 100px;
  height: 100px;
  background-color: lightblue;
  margin: 5px;
  text-align: center;
  vertical-align: top;
}
```
위의 예시에서는 __inline-block-example 클래스를 가진 두 개의 span 요소가 inline-block으로 설정__ 되어 있습니다. 각 요소는 동일한 줄에 배치되면서도, 지정된 너비와 높이를 가지고, 배경색과 여백이 적용됩니다. 또한, __text-align과 vertical-align 속성을 통해 텍스트 정렬이 가능__ 합니다.<br/>

#### __주요 특징__ <br/>

##### __인라인 배치__ <br/>
* inline-block 요소는 __문서 흐름상 다른 인라인 요소들과 같은 줄에 배치__ 됩니다. 즉, 새로운 라인을 시작하지 않습니다.<br/>

##### __크기 지정 가능__ <br/>
* inline-block 요소는 상하 여백과 패딩을 지정할 수 있습니다. __인라인 요소에서는 좌우 여백과 패딩만 적용되는 반면, inline-block 요소에서는 상하 여백과 패딩도 효과적으로 적용__ 됩니다.<br/>

##### __상하 여백(margin)과 패딩(padding) 지정__ <br/>
* width와 height 속성을 사용하여 요소의 너비와 높이를 지정할 수 있습니다. 이는 인라인 요소와 대비됩니다.<br/>

##### __내부 배치__ <br/>
* __inline-block 요소 내부에는 인라인 요소와 블록 요소 모두 배치할 수 있습니다.__ 는 레이아웃 구성에 유연성을 제공합니다.<br/>

##### __텍스트나 다른 인라인 요소와 함께 묶여서 표시__ <br/>
* 인라인 요소는 텍스트나 다른 인라인 요소와 함께 한 줄에 나란히 배치됩니다.<br/>

#### __사용 시 고려 사항__ <br/>

##### __화이트 스페이스__ <br/>
* __inline-block 요소들은 HTML 소스 코드상의 공백 문자로 인해 요소 사이에 작은 간격이 생길 수 있습니다.__ 이를 해결하기 위해 HTML 코드에서 요소 사이의 공백을 제거하거나, __CSS의 font-size: 0; 기법을 부모 요소에 적용하는 방법__ 등을 사용할 수 있습니다. <br/>

---
### __transition-delay__ <br/>
display: none은 CSS 속성 중 하나로, __지정된 요소를 문서 레이아웃에서 완전히 제거하고 화면에 표시하지 않습니다.__ 이 속성은 요소를 숨기고 싶을 때 유용하게 사용될 수 있으며, __요소가 문서의 흐름에서 완전히 제거되므로 다른 요소들이 그 자리를 차지하게 됩니다.__ none은 요소를 완전히 숨기고 싶을 때 사용하는 반면, __visibility: hidden은 요소를 숨기되 그 위치를 유지__ 하고 싶을 때 사용합니다. <br/>

```html
<div id="hiddenMessage">이 메시지는 숨겨집니다.</div>
<button onclick="showMessage()">메시지 보기</button>
```

```css
#hiddenMessage {
  display: none;
}
```

```javascript
function showMessage() {
  document.getElementById('hiddenMessage').style.display = "block";
}
```
위의 예시에서는 __div 요소가 처음에는 숨겨져 있으며, 사용자가 버튼을 클릭하면 JavaScript 함수가 호출되어 display 속성을 block으로 변경하여 요소를 보이게 합니다.__<br/>

#### __주요 특징__ <br/>

##### __문서 레이아웃에서 제거__ <br/>
* display: none으로 설정된 요소는 렌더링되지 않으며, 해당 요소에 할당된 공간도 사라집니다. 즉, __화면에서 요소가 차지하던 공간이 다른 요소들로 채워지게 됩니다.__ <br/>

##### __접근성 영향__ <br/>
* 스크린 리더와 같은 보조 기술도 display: none으로 설정된 요소를 인식하지 못할 수 있으므로, 접근성 측면에서 고려해야 합니다.<br/>

##### __자바스크립트와의 상호작용__ <br/>
* __display: none 속성은 JavaScript를 통해 동적으로 적용하거나 제거할 수 있습니다.__ 이를 통해 사용자 인터랙션에 따라 요소를 보이거나 숨길 수 있습니다.<br/>

#### __display: none VS visibility: hidden__ <br/>

##### __display: none__ <br/>
* 요소가 문서 레이아웃에서 완전히 제거됩니다.<br/>

##### __visibility: hidden__ <br/>
* 요소가 보이지 않지만, 레이아웃에서 여전히 공간을 차지합니다.<br/>
