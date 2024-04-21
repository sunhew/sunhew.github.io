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

## __display의 속성 값__<br/>
CSS의 __display 속성은 웹 페이지 내 요소가 어떻게 배치되고, 다른 요소들과 어떻게 상호작용할지 결정__ 합니다. 이 속성은 __요소의 레이아웃 및 박스 유형을 제어하는 데 핵심적인 역할__ 을 합니다. display 속성의 주요 값들에는 다음과 같은 것들이 있습니다<br/>

1. block <br/>
2. inline<br/>
3. inline-block<br/>
4. none<br/>
5. flex<br/>
5. grid<br/>
5. table, table-row, table-cell 등<br/>

---
### __display: block__ <br/>
display: block 은 CSS에서 사용되는 속성 값 중 하나로, 해당 속성을 가진 요소가 블록 레벨 요소로 표시되게 합니다. 블록 레벨 요소는 웹 페이지의 레이아웃을 구성하는 데 중요한 역할을 합니다. 웹 페이지의 레이아웃을 구성하고, 요소들을 적절히 조직화하는 데 필수적인 역할을 합니다.

```html
<div>첫 번째 블록 요소</div>
<div>두 번째 블록 요소</div>
```

```css
div {
  display: block;
  width: 50%;
  margin: 10px auto;
  padding: 20px;
  background-color: lightgray;
}
```
위의 예시에서는 두 개의 __div__ 요소가 블록 레벨로 표시되며, 각각 새로운 줄에서 시작합니다. 너비는 부모 요소의 50%로 설정되어 있고, 상하좌우 마진은 자동으로 설정되어 중앙 정렬됩니다. 패딩과 배경색도 추가되었습니다.<br/>

#### __블록 레벨 요소의 특징__ <br/>

##### __새로운 줄에서 시작__ <br/>
* 블록 레벨 요소는 새로운 줄에서 시작하며, 이전 요소가 끝나는 지점 이후에 위치합니다.<br/>

##### __가용 너비 차지__ <br/>
* 본적으로 블록 레벨 요소는 부모 요소의 가용 너비 전체를 차지합니다. 즉, 가로 폭이 부모 요소의 내부 너비만큼 넓어집니다.<br/>

##### __너비와 높이 지정 가능__ <br/>
* width와 height 속성을 사용하여 요소의 너비와 높이를 지정할 수 있습니다. 이는 인라인 요소와 대비됩니다.<br/>

##### __마진과 패딩__ <br/>
* 상, 하, 좌, 우 마진과 패딩을 적용할 수 있으며, 이는 요소의 크기와 페이지 내 위치에 영향을 줍니다.<br/>

#### __사용 사례__ <br/>

##### __단락__ <br/>
* __p__ 태그는 기본적으로 display: block 속성을 가지며, 텍스트의 단락을 표시하는 데 사용됩니다.<br/>

##### __컨테이너__ <br/>
* __div__ 태그는 웹 페이지의 다양한 섹션을 구분하는 데 사용되는 범용 컨테이너로, 기본적으로 블록 레벨 요소입니다.<br/>

##### __폼 요소__ <br/>
* 대부분의 폼 요소는 블록 레벨로 표시되어 사용자 입력을 위한 공간을 제공합니다.<br/>

---
### __display: inline__ <br/>
CSS에서 __display: inline 속성 값은 해당 요소가 인라인(inline) 요소로 처리되도록 지정__ 합니다. 인라인 요소는 몇 가지 특성을 가지고 있으며, 웹 페이지의 내용을 구성할 때 중요한 역할을 합니다. 웹 페이지에서 텍스트 또는 다른 요소들을 문장 내에서 스타일링하고자 할 때 유용하게 사용됩니다. 그러나 요소의 크기를 조절하거나 상하 마진과 패딩을 적용하고자 할 때는 다른 display 속성 값을 고려해야 합니다. <br/>

```html
<p>이것은 <span>인라인</span> 요소의 예시입니다.</p>
```

```css
span {
  display: inline;
  color: red;
}
```
위의 예시에서는 __span 태그는 인라인 요소로 지정되어 있어, 문장 내에서 다른 텍스트와 함께 한 줄에 배치__ 됩니다. color 속성을 통해 텍스트 색상만 변경할 수 있습니다.<br/>

#### __인라인 요소의 특성__ <br/>

##### __새로운 줄에서 시작하지 않음__ <br/>
* 인라인 요소는 새로운 줄에서 시작하지 않고, 문서의 흐름에 따라 이전 요소와 같은 줄에 배치됩니다.<br/>

##### __너비와 높이 지정 불가__ <br/>
* 인라인 요소는 __width와 height 속성을 사용하여 크기를 지정할 수 없습__ 니다. 요소의 크기는 내용에 의해 결정됩니다.<br/>

##### __상하 마진과 패딩 제한적__ <br/>
* __인라인 요소는 좌우 마진과 패딩은 적용되지만, 상하 마진과 패딩은 다른 요소에 영향을 주지 않습니다.__<br/>

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
### __display: inline-block__ <br/>
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
### __display: none__ <br/>
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

---
### __display: flex__ <br/>
isplay: flex속성은 __플렉스박스 레이아웃(Flexible Box Layout)을 설정하여, 컨테이너 내 아이템들의 배치, 정렬, 분배를 유연하게 조정할 수 있게 해줍니다.__ 이는 복잡한 레이아웃을 보다 간단하게 구성할 수 있도록 돕는 강력한 도구입니다. 플렉스박스는 반응형 웹 디자인을 구현할 때 특히 유용합니다. <br/>

```html
<div class="container">
  <div>Box 1</div>
  <div>Box 2</div>
  <div>Box 3</div>
</div>
```

```css
.container {
  display: flex;
  justify-content: center; /* 아이템들을 주축을 따라 중앙 정렬 */
  align-items: center; /* 아이템들을 교차축을 따라 중앙 정렬 */
}
```

위의 코드는 CSS와 HTML은 3개의 박스를 가로로 정렬하는 간단한 플렉스박스 레이아웃 예시입니다. __.container는 플렉스 컨테이너가 되며, 내부의 div들은 플렉스 아이템으로 작동__ 합니다. __justify-content와 align-items 속성을 사용해 아이템들을 가로축과 세로축에서 중앙에 정렬합니다.__<br/>

#### __주요 특징__ <br/>

##### __플렉스 컨테이너(Flex Container) 설정__ <br/>
* display: flex 속성을 사용하면 해당 요소는 __플렉스 컨테이너__ 가 됩니다. 이 컨테이너 내의 __직계 자식 요소들은 자동으로 플렉스 아이템(flex items)__ 이 됩니다.<br/>

##### __주축(Main Axis)과 교차축(Cross Axis)__ <br/>
* 주축(Main Axis): 플렉스 아이템들이 배치되는 주된 __방향__ 을 의미합니다. 기본값은 가로 방향입니다(flex-direction: row;).<br/>

* 교차축(Cross Axis): 교차축(Cross Axis): 주축에 __수직인 방향__ 입니다. 기본값에서는 세로 방향이 됩니다.<br/>

#### __중요한 속성들__ <br/>

##### __flex-direction__ <br/>
* 주축의 방향을 설정합니다. 예: __row__ (가로), __column__ (세로) <br/>

##### __justify-content__ <br/>
* 주축을 따라 플렉스 아이템의 정렬을 결정합니다. 예: __flex-start, center, space-between__ <br/>

##### __align-items__ <br/>
* 교차축을 따라 플렉스 아이템의 정렬을 결정합니다. 예: __flex-start, center, stretch__ <br/>

##### __flex-wrap__ <br/>
* 아이템들이 컨테이너를 벗어날 경우, 줄 바꿈 여부를 결정합니다. 예: __nowrap, wrap__ <br/>

##### __flex-flow__ <br/>
* flex-direction과 flex-wrap의 단축 속성입니다. <br/>

##### __align-content__ <br/>
* 여러 줄의 플렉스 아이템을 교차축을 따라 정렬합니다. 이는 __flex-wrap__ 속성이 __wrap__ 일 때만 작동합니다.<br/>

---
### __display: grid__ <br/>
isplay: grid는 __CSS Grid Layout을 활성화하는 속성__ 입니다. 이것은 웹 페이지의 레이아웃을 __더 유연하고, 간단하며, 강력하게 만들어주는 2차원 레이아웃 시스템__ 입니다. CSS Grid는 복잡한 레이아웃을 쉽게 구현할 수 있게 해주며, 행(row)과 열(column) 기반의 레이아웃을 생성할 수 있습니다. CSS Grid는 복잡한 웹 레이아웃을 손쉽게 구현할 수 있게 해주는 강력한 도구이며 Flexbox와 함께 사용하면 더욱 다양한 레이아웃을 구성할 수 있습니다.<br/>

```css
.container {
  display: grid;
  grid-template-columns: 100px 200px auto;
  grid-template-rows: 50px 100px;
  gap: 10px;
}
```

위의 코드는  CSS는 .container 클래스를 가진 요소에 그리드 레이아웃을 적용합니다. 이 __레이아웃은 세 개의 열(100px, 200px, 나머지 공간을 차지하는 auto)과 두 개의 행(50px, 100px)으로 구성__ 됩니다. __그리드 셀 사이의 간격은 10px__ 입니다.<br/>

#### __주요 특징__ <br/>

##### __그리드 컨테이너(Grid Container)__ <br/>
* display: grid를 적용한 요소는 그리드 컨테이너가 됩니다. 이 컨테이너 내의 직접적인 자식 요소들은 그리드 아이템(grid items)이 됩니다.<br/>

##### __그리드 트랙(Grid Tracks)__ <br/>
* 행(row)과 열(column)은 그리드 트랙을 형성합니다. 이들은 __grid-template-rows와 grid-template-columns__ 속성을 사용하여 정의할 수 있습니다.<br/>

##### __그리드 셀(Grid Cell)__ <br/>
* 그리드의 가장 작은 단위로, 하나의 그리드 아이템이 배치될 수 있는 공간입니다. <br/>

##### __그리드 라인(Grid Line)__ <br/>
* 그리드 셀을 구분하는 라인입니다. __행과 열의 시작점과 끝점을 정의__ 하는데 사용됩니다. <br/>

##### __그리드 갭(Grid Gap)__ <br/>
* 그리드 셀 사이의 공간입니다. __grid-gap, grid-row-gap, grid-column-gap__ 속성을 통해 조절할 수 있습니다.<br/>

#### __Grid 사용시 고려할 점__ <br/>

##### __브라우저 호환성__ <br/>
* 대부분의 최신 브라우저는 CSS Grid를 지원하지만, 오래된 브라우저나 특정 버전에서는 지원하지 않을 수 있습니다. 사용 전에 호환성을 확인하세요. <br/>

##### __반응형 디자인__ <br/>
* __auto-fill, auto-fit__ 과 같은 그리드 속성을 사용하여 __그리드 레이아웃을 반응형__ 으로 만들 수 있습니다.<br/>

---
### __display: table, table-row, table-cell 등__ <br/>
CSS에서 __display: table, table-row, table-cell__ 등의 속성들은 HTML의 __table, tr, td__ 태그와 유사한 레이아웃을 CSS만으로 구현할 수 있게 해줍니다. 이 방식은 표 형태의 데이터를 보여주는 것이 아니라도, 웹 페이지의 레이아웃을 구성하는 데 유용하게 사용될 수 있습니다.<br/>

```html
<div class="table">
  <div class="row">
    <div class="cell">셀 1</div>
    <div class="cell">셀 2</div>
  </div>
  <div class="row">
    <div class="cell">셀 3</div>
    <div class="cell">셀 4</div>
  </div>
</div>
```

```css
.table {
  display: table;
  border: 1px solid #000;
}

.row {
  display: table-row;
}

.cell {
  display: table-cell;
  border: 1px solid #000;
  padding: 5px;
}
```

위의 코드에서 __.table, .row, .cell__ 클래스를 가진 요소들은 각각 __table, tr, td__ 태그와 유사하게 동작하여 __2x2 테이블을 만듭니다.__<br/>

#### __각각의 설명__ <br/>

##### __display: table__ <br/>
* 이 속성은 요소를 __테이블과 같은 블록 레벨 컨테이너로 만듭니다.__ 즉, 원래의 _table_ 태그와 같은 역할을 합니다. 이 요소의 자식 요소들은 __table-row, table-cell 등의 속성을 사용하여 테이블의 행과 셀로 동작__ 하게 할 수 있습니다.<br/>

##### __display: table-row__ <br/>
* table-row 속성을 사용하면 그 요소는 __테이블의 한 행(tr)처럼 동작합니다.__ 이 요소의 자식들은 자동으로 __table-cell 역할을 하게 되어, 테이블의 셀(td 또는 th)처럼 동작__ 합니다.<br/>

##### __display: table-cell__ <br/>
* table-cell 속성을 적용한 요소는 __테이블의 셀(td 또는 th)처럼 동작__ 합니다. 이를 통해 요소들을 테이블 셀처럼 __나란히 배열할 수 있으며, vertical-align과 같은 테이블 셀에 특화된 속성들을 사용__ 할 수 있습니다.<br/>

#### __사용 시 고려사항__ <br/>
* CSS 테이블 레이아웃은 레거시 브라우저에서도 잘 동작하지만, 복잡한 테이블 레이아웃을 구현할 때는 __HTML의 table 태그를 사용하는 것이 더 의미적으로 적합__ 할 수 있으며 테이블 레이아웃을 사용할 때는 콘텐츠의 접근성을 고려해야 합니다. 데이터를 표현하는 목적이라면 __table__ 태그를 사용하는 것이 더 적합할 수 있습니다. <br/>

##### __display__ <br/>
* flex나 display: grid와 같은 더 현대적인 CSS 레이아웃 기술이 등장하면서, 테이블 레이아웃은 주로 __간단한 목적에 한정__ 되어 사용됩니다.<br/>