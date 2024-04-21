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

#### __기본 문법__
* 아래의 코드에서 시간은 초(s)나 밀리초(ms) 단위로 지정됩니다. 예를 들어, 2s는 2초를 의미하고, 500ms는 500밀리초를 의미합니다.

```css
transition-duration: 시간;   
```

#### __전환 효과의 시간__ <br/>
* 아래 코드에서는 __div 요소의 opacity 속성에 대한 전환 효과가 1초 동안 지속__ 됩니다. 사용자가 어떤 상호작용(예: __마우스 오버(mouse over)__)을 통해 opacity 값이 변경되면, 이 변경은 부드럽게 1초에 걸쳐 일어납니다.<br/>

```css
div {
  transition-property: opacity;
  transition-duration: 1s;
} 
```

#### __다중 전환 효과 설정__ <br/>
* 여러 전환 효과를 적용하고 싶을 때는 각각의 지속 시간을 __쉼표로 구분하여 나열__ 합니다. 아래 코드에서는 __div 요소의 opacity 전환 효과가 1초 동안, transform 전환 효과가 500밀리초 동안 각각 지속__ 됩니다.<br/>

```css
div {
  transition-property: opacity, transform;
  transition-duration: 1s, 500ms;
}
```

#### __주의해야할 점__ <br/>

##### __지속 시간의 설정__ <br/>
* 전환 효과의 지속 시간을 너무 짧게 설정하면 사용자가 변화를 인지하기 어려울 수 있고, 너무 길게 설정하면 사용자 경험에 방해가 될 수 있습니다. 적절한 지속 시간 선택이 중요합니다.<br/>

##### __지정 규칙__ <br/>
* __transition-duration만 지정하고 transition-property를 지정하지 않으면, 기본값인 all이 적용되어 모든 속성에 대한 전환 효과가 적용__ 됩니다. 필요에 따라 특정 속성에만 전환 효과를 적용하는 것이 좋습니다.<br/>

---
### __transition-timing-function__ <br/>
transition-timing-function 속성은 CSS에서 전환(transition) __효과의 속도 곡선을 지정__ 합니다. 이 속성은 전환 효과의 시작과 끝에서 속도가 어떻게 변화할지 결정하여, 웹 페이지의 요소들이 보다 자연스럽고 동적으로 변화하도록 하며 기본적으로 아래와 같은 타이밍 함수와 함께 합니다. <br/>


|타이밍 함수|설명|
|---|---|
|linear|시작부터 끝까지 일정한 속도로 변화합니다. 속도 곡선은 직선입니다.|
|ease|시작할 때는 느리게, 중간에는 빠르게, 끝날 때는 다시 느리게 변화합니다. 대부분의 경우 자연스러운 움직임을 제공합니다.|
|ease-in|시작할 때 느리며, 점점 빨라집니다. 속도 곡선은 점점 가파르게 상승합니다.|
|ease-out|시작할 때는 빠르고, 끝날 때 느려집니다. 속도 곡선은 점점 완만해집니다.|
|ease-in-out|시작과 끝에서는 느리고, 중간에는 빠르게 변화합니다. ease보다 더 부드러운 전환을 제공합니다.|
|cubic-bezier(n,n,n,n)|사용자가 직접 곡선의 형태를 정의할 수 있게 해주는 함수입니다. 네 개의 값은 베지어 곡선의 제어점을 정의합니다.|


#### __예시__

아래 코드는 div 요소의 배경색이 0.5초 동안 변할 때, ease-in-out 타이밍 함수를 사용하여 부드럽게 전환되도록 합니다. 또한, cubic-bezier 함수를 사용하여 더 세밀하게 속도 곡선을 조정할 수 있습니다 아래 코드는 div 요소가 변형될 때 사용자가 정의한 특별한 속도 곡선을 따라 변화하도록 합니다.<br/>

```css
div {
  transition: background-color 0.5s ease-in-out;
}
```

```css
div {
  transition: transform 0.5s cubic-bezier(0.25, 0.1, 0.25, 1);
}
```

transition-timing-function 속성을 사용함으로써, 요소의 전환 효과를 더욱 생생하고 매력적으로 만들 수 있으며, 사용자에게 보다 개선된 인터랙티브 경험을 제공할 수 있습니다.<br/>


---
### __transition-delay__ <br/>
transition-delay 속성은 CSS에서 요소의 __전환 효과가 시작하기까지의 지연 시간을 설정__ 하는 데 사용됩니다. 이 속성은 __전환 효과가 즉시 시작되지 않고 지정된 시간만큼 지연된 후 시작__ 되도록 합니다. transition-delay는 전환 효과를 더욱 동적이고 흥미롭게 만들어 줄 수 있으며, 사용자 인터페이스의 시각적 피드백을 개선하는 데 유용하게 사용될 수 있습니다. <br/>

#### __기본 구문__
아래 코드에서 시간은 초(s) 또는 밀리초(ms) 단위로 지정될 수 있습니다. 예를 들어, transition-delay: 2s;는 전환 효과가 2초 후에 시작됨을 의미합니다. <br/>

```css
transition-delay: 시간;
```

#### __사용 예시__

```css
.element {
  background-color: blue;
  transition: background-color 1s;
  transition-delay: 500ms;
}

.element:hover {
  background-color: red;
}
```

위의 예시에서는 __.element 요소에 마우스를 올리면 배경색이 파란색에서 빨간색으로 변경__ 됩니다. __transition-delay 속성이 500ms로 설정__ 되어 있기 때문에, 마우스를 올린 후 __실제 전환 효과가 시작되기까지 0.5초의 지연 시간이 발생__ 합니다.<br/>

##### __함수에게 주는 영향__ <br/>
* __transition-delay는 전환 효과가 시작되기까지의 지연 시간만을 제어__ 하며, 전환 효과 자체의 지속 시간(duration)이나 __타이밍 함수(timing function)에는 영향을 주지 않습니다.__ <br/>

##### __음수 값의 사용__ <br/>
* __음수 값을 사용할 경우, 전환 효과는 지정된 시간만큼 이미 진행된 상태에서 시작__ 됩니다. 예를 들어, transition-delay: -1s;를 사용하면 전환 효과는 지정된 지연 시간 1초 전에 시작되며, 사용자에게는 전환 효과가 즉시 시작된 것처럼 보일 수 있습니다.<br/>

##### __순차적 발생__ <br/>
* 여러 전환 효과를 동시에 적용할 경우, 각 전환 효과에 대해 다른 transition-delay 값을 지정하여 효과가 순차적으로 발생하도록 할 수 있습니다.<br/>