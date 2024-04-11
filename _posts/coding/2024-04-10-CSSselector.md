---
layout: post
title: 선택자(selector)
date: 2024-04-10 16:25 +0900
description: CSS의 선택자의 종류
image: ../assets/img/yahossinnanda.jpg
category: CSS
tags: CSS
published: true
sitemap: true
---

# CSS의 선택자(selector)에 대한것을 알아봅시다.
CSS(Cascading Style Sheets)를 정의하는 방법으로는 "내부 스타일시트", "외부 스타일시트", "인라인 스타일시트" 등이 있습니다. 실제로는 외부 스타일시트를 많이 사용하지만 간단한 스타일은 내부 스타일만으로도 사용 할 수 있습니다.

## 1. Type 선택자 (요소 선택자)
Type 선택자, 또는 요소 선택자는 CSS에서 가장 기본적인 선택자 유형 중 하나입니다. 이 선택자는 특정 유형의 HTML 요소를 대상으로 스타일을 적용할 때 사용됩니다. 즉, 특정 태그 이름을 가진 모든 요소에 스타일 규칙을 적용하고자 할 때 사용하는 선택자입니다. <br/>

````css
p {
  color: red;
  font-size: 16px;
}
````
__Type 선택자의 특징__ <br/>
* 범용성: Type 선택자는 해당 유형의 모든 요소에 스타일을 적용합니다. 따라서, 특정 클래스나 ID를 지정하지 않고도 동일한 태그를 가진 모든 요소를 쉽게 스타일링할 수 있습니다. <br/>

* 간단함: 선택자의 구문이 매우 간단하고 직관적이어서, CSS를 처음 배우는 사람들도 쉽게 이해하고 사용할 수 있습니다.<br/>

* 우선순위: Type 선택자는 ID 선택자나 클래스 선택자보다 우선순위가 낮습니다. 따라서, 같은 요소에 대해 Type 선택자와 더 구체적인 선택자(예: 클래스, ID)가 모두 스타일을 정의하고 있다면, 더 구체적인 선택자의 스타일이 적용됩니다.<br/>

__Type 선택자의 활용__<br/>
Type 선택자는 웹 페이지 전체의 일관된 스타일을 설정하는 데 유용합니다. 예를 들어, 모든 제목(h1, h2, h3 등)에 동일한 폰트 스타일을 적용하거나, 모든 리스트(ul, ol)에 특정 마진을 설정하는 등의 경우에 활용할 수 있습니다.

## 2. id 선택자
ID 선택자는 CSS에서 매우 구체적인 요소를 대상으로 스타일을 적용할 때 사용되는 선택자입니다. 각 ID 속성은 문서 내에서 유일해야 하며, 이를 통해 단일 요소에 대해 매우 구체적인 스타일 규칙을 적용할 수 있습니다. ID 선택자는 # 기호를 사용하여 표시됩니다.<br/>

아래 CSS 규칙은 id="unique-element" 속성을 가진 HTML 요소에 적용됩니다. 이 요소의 텍스트 색상을 녹색으로, 그리고 폰트 크기를 20px로 설정합니다.

````css
#unique-element {
    color: green;
    font-size: 20px;
}
````
__ID 선택자의 특징.__<br/>
* 유일성: ID 선택자는 문서 내에서 고유해야 합니다. 즉, 한 문서 내에 같은 ID를 가진 요소가 두 개 이상 있어서는 안 됩니다.<br/>

* 구체성: ID 선택자는 클래스 선택자나 태그 선택자보다 우선순위가 높습니다. 따라서, 같은 요소에 대해 여러 선택자가 스타일을 정의하고 있을 경우, ID 선택자로 지정된 스타일이 우선적으로 적용됩니다.<br/>

* 용도: ID 선택자는 문서 내에서 단 하나의 요소에 대해 매우 구체적인 스타일을 적용할 필요가 있을 때 사용됩니다. 예를 들어, 페이지 내에서 유일한 헤더, 특정 섹션 등에 사용될 수 있습니다.<br/>


__ID 선택자의 사용 주의사항__ <br/>
* 유일성 위반: HTML 문서 내에서 같은 ID를 가진 요소가 여러 개 있는 경우, 예상치 못한 스타일 문제가 발생할 수 있습니다. <br/>

* 재사용성 제한: ID는 유일해야 하기 때문에, 여러 요소에 동일한 스타일을 적용하고자 할 때는 클래스 선택자의 사용이 더 적합합니다.<br/>

* 스타일 우선순위: ID 선택자는 매우 높은 우선순위를 가지고 있어, 다른 선택자를 통해 스타일을 재정의하기 어려울 수 있습니다. 이는 때때로 CSS의 유지 보수를 어렵게 할 수 있으므로 신중하게 사용해야 합니다.

__text-decoration-style 값__ <br/>
* solid: 실선을 그립니다. <br/>

* double: 이중 선을 그립니다. <br/>

* dotted: 점선을 그립니다. <br/>

* dashed: 파선을 그립니다. <br/>
* wavy: 파동 모양의 선을 그립니다.


## 3. Class 선택자
Class 선택자는 CSS에서 스타일을 적용할 HTML 요소의 그룹을 지정하는 데 사용됩니다. Class 선택자는 동일한 스타일을 여러 요소에 적용하고자 할 때 특히 유용합니다. 이를 통해, 웹 페이지 내에서 재사용 가능한 스타일을 생성하여, 코드의 재사용성과 유지 관리를 향상시킬 수 있습니다. Class 선택자는 점(.)으로 시작합니다.<br/>

아래 CSS 규칙은 class="highlight" 속성을 가진 모든 HTML 요소에 적용됩니다.

````css
.highlight {
    background-color: yellow;
    font-weight: bold;
}
````
__Class 선택자의 특징__ <br/>
* 재사용성: Class 선택자는 하나 이상의 HTML 요소에 동일한 스타일을 적용할 수 있게 합니다. 이를 통해 스타일 규칙의 재사용성이 높아지고, 코드의 중복을 줄일 수 있습니다. <br/>

* 조합 가능성: 하나의 요소에 여러 클래스를 적용할 수 있습니다. 이를 통해, 다양한 스타일을 조합하여 더 복잡한 스타일링을 쉽게 구현할 수 있습니다. <br/>

* 구체성: Class 선택자는 태그 선택자보다 우선순위가 높으나, ID 선택자보다는 낮습니다. 이는 스타일 적용시 우선순위를 고려해야 함을 의미합니다. <br/>

__Class 선택자의 활용__ <br/>
Class 선택자는 웹 페이지의 다양한 요소에 공통 스타일을 적용하고자 할 때 매우 유용합니다. 예를 들어, 경고 메시지, 버튼 스타일, 글씨 스타일 등을 일관되게 유지하고자 할 때 사용할 수 있습니다. 또한, 하나의 요소에 여러 클래스를 적용함으로써, 다양한 스타일을 조합해 유연한 디자인을 구현할 수 있습니다. <br/>

__Class 선택자의 사용 주의사항__ <br/>
* 명명 규칙: 클래스 이름은 의미 있고, 명확하게 작성되어야 합니다. 이는 코드의 가독성과 유지 보수성을 높이는 데 중요합니다. <br/>

* 우선순위 충돌: 여러 클래스가 같은 요소에 적용될 때, 스타일 규칙 간의 충돌이 발생할 수 있습니다. 이 경우, CSS의 우선순위 규칙(Cascading rules)에 따라 결정됩니다. 명시도(Specificity)가 높은 스타일이 우선 적용됩니다.

## 4. 전체 선택자(Universal Selector)
CSS에서 모든 요소를 선택하는 데 사용되는 선택자입니다. 전체 선택자는 별표(*) 기호로 표현되며, 문서 내의 모든 요소에 스타일을 적용할 수 있습니다. 이 선택자는 웹 페이지의 전반적인 기본 스타일을 설정하고자 할 때 유용하게 사용될 수 있습니다.<br/>

아래 CSS 규칙은 문서 내의 모든 요소에 대해 마진과 패딩을 0으로 설정하고, box-sizing 속성을 border-box로 설정합니다. 이는 웹 페이지를 구축할 때 일반적인 초기화 작업의 일부로 사용될 수 있습니다.

````css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
````
__전체 선택자의 특징__ <br/>
* 범용성: 전체 선택자는 문서 내의 모든 요소에 스타일을 적용합니다. 이는 매우 강력하지만, 때로는 불필요한 스타일 오버라이드를 초래할 수 있습니다. <br/>

* 우선순위: 전체 선택자는 다른 모든 CSS 선택자 중에서 가장 낮은 우선순위를 가집니다. 따라서, 같은 요소에 대해 다른 선택자를 통해 정의된 스타일이 있다면, 그 스타일이 전체 선택자를 통해 정의된 스타일보다 우선 적용됩니다. <br/>

* 효율성: 전체 선택자를 사용하면 코드의 양을 줄일 수 있지만, 모든 요소에 스타일을 적용하기 때문에 브라우저의 렌더링 성능에 영향을 줄 수 있습니다. 특히 대규모 문서에서는 이러한 영향이 더욱 두드러질 수 있습니다. <br/>

__전체 선택자의 활용__ <br/>
전체 선택자는 주로 글로벌 스타일을 정의하고, 웹 페이지의 기본 스타일을 초기화하는 데 사용됩니다. 예를 들어, 다양한 브라우저에서 일관된 레이아웃을 유지하기 위해 모든 요소의 마진과 패딩을 초기화하는 용도로 자주 사용됩니다. 또한, box-sizing 속성을 border-box로 설정하여 요소의 크기 계산 방식을 일관되게 만드는 데에도 활용됩니다. <br/>

__전체 선택자의 사용 주의사항__ <br/>
* 성능 고려: 전체 선택자는 간편하고 유용하지만, 모든 요소에 스타일을 적용하기 때문에 웹 페이지의 렌더링 성능에 영향을 줄 수 있습니다. 따라서, 필요한 경우에만 사용하는 것이 좋습니다. <br/>

* 우선순위 관리: 전체 선택자는 우선순위가 낮기 때문에, 다른 선택자를 통해 정의된 스타일에 의해 쉽게 오버라이드될 수 있습니다. 이 점을 고려하여 스타일을 적용하는 것이 중요합니다. <br/>

## 5. 하위 선택자(descendant selector)
CSS에서 특정 요소의 모든 하위 요소를 선택하는 데 사용됩니다. 하위 선택자는 두 개 이상의 선택자를 공백으로 구분하여 사용하며, 첫 번째 선택자에 의해 선택된 요소의 모든 자손(descendants) 중 두 번째 선택자에 해당하는 요소를 선택합니다. 이는 더 구체적인 요소를 스타일링하기 위해 사용되며, 깊이에 관계없이 모든 하위 요소를 포함합니다. 사용 시 문서의 구조를 잘 이해하고 있어야 하며, 오버라이딩이나 성능 문제를 방지하기 위해 신중하게 사용해야 합니다.<br/>

이 코드는 _article_ 태그 내부에 위치한 모든 _p_ 태그의 텍스트 색상을 파란색으로 설정합니다. _article_ 태그 내부의 깊이에 상관없이, 모든 _p_ 태그가 선택됩니다.

````css
article p {
  color: blue;
}
````
__하위 선택자의 기본 문법__ <br/>
* 상위요소: 하위 요소를 포함하는 요소를 선택합니다. <br/>

* 하위요소: 상위 요소에 포함된 특정 요소를 선택합니다. <br/>

* 사이의 공백은 하위 선택자임을 나타냅니다. <br/>

__하위 선택자의 특징__ <br/>
* 유연성: 하위 선택자는 특정 요소 내부의 다양한 요소에 스타일을 적용할 때 매우 유용합니다. 요소의 구조가 복잡하거나, 특정 요소 내부의 모든 요소에 일관된 스타일을 적용하고 싶을 때 효과적입니다. <br/>

* 범위: 하위 선택자는 선택된 상위 요소 내부의 모든 하위 요소에 스타일을 적용합니다. 이는 선택된 요소의 자식뿐만 아니라, 자손에도 영향을 미칩니다. <br/>

* 성능: 하위 선택자는 CSS 엔진이 문서의 구조를 따라가며 매칭해야 하므로, 복잡한 문서에서는 성능에 영향을 줄 수 있습니다. 따라서, 필요한 경우에만 사용하고, 가능한 한 구체적인 선택자를 사용하는 것이 좋습니다. <br/>

## 6. 자식 선택자(Child Selector)
자식 선택자(Child Selector)는 CSS에서 특정 요소의 바로 아래 한 단계에 위치한 자식 요소들을 선택하는 데 사용됩니다. 이 선택자는 '>' 기호를 사용하여 표현하며, 왼쪽에 위치한 요소의 직접적인 자식인 오른쪽 요소만을 선택합니다. 자식 선택자는 하위 선택자와 비교했을 때 더 명확한 대상 지정이 가능하며, 선택 범위가 더 제한적입니다. <br/>

아래 CSS 규칙은 _div_ 태그의 직접적인 자식으로 있는 모든 _p_ 태그의 텍스트 색상을 녹색으로 설정합니다. 만약 _p_ 태그가 더 깊은 수준의 하위 요소로 존재한다면, 이 규칙은 적용되지 않습니다.

````css
div > p {
  color: green;
}
````
__자식 선택자의 기본 문법__ <br/>
* 부모요소: 자식 요소를 포함하는 상위 요소를 선택합니다.<br/>

* 자식요소: 부모 요소의 바로 아래 한 단계에 위치한 요소를 선택합니다.<br/>

* ' _>_ ' 기호는 자식 선택자임을 나타냅니다.<br/>

__자식 선택자의 특징__ <br/>
* 정확성: 자식 선택자는 직접적인 자식 요소에만 스타일을 적용하기 때문에, 선택의 범위가 명확합니다. 이는 복잡한 페이지 레이아웃에서 특정 요소를 대상으로 스타일을 적용할 때 유용합니다.<br/>

* 제한적 범위: 자식 선택자는 바로 아래 한 단계의 자식에만 스타일을 적용하기 때문에, 하위 선택자보다 범위가 좁습니다. 이는 더 세밀한 스타일 지정을 가능하게 합니다.<br/>

* 사용 용도: 자식 선택자는 메뉴, 리스트, 폼 등 특정 구조 내에서 직접적인 자식 요소에만 스타일을 적용하고자 할 때 주로 사용됩니다.

## 7. 인접 선택자(Adjacent Sibling Selector)
인접 선택자(Adjacent Sibling Selector)는 CSS에서 특정 요소 바로 다음에 위치한 형제 요소를 선택하는 데 사용됩니다. 인접 선택자는 '+' 기호를 사용하여 표현되며, 선택자의 왼쪽에 위치한 요소의 바로 다음 형제 요소로, 오른쪽에 위치한 요소가 있을 경우에만 해당 요소를 선택합니다. 이 선택자는 특정 요소와 바로 인접한 요소에 스타일을 적용할 때 유용하게 사용됩니다. <br/>

아래 CSS 규칙은 _h2_ 태그 바로 다음에 위치한 _p_ 태그에만 폰트 크기를 14px로 설정합니다. _h2_ 태그와 _p_ 태그 사이에 다른 요소가 있거나, _p_ 태그가 _h2_ 태그 바로 다음에 위치하지 않는 경우, 이 규칙은 적용되지 않습니다.

````css
h2 + p {
  font-size: 14px;
}
````
__인접 선택자의 특징__ <br/>
* 정확한 위치 지정: 인접 선택자는 매우 구체적인 위치에 있는 요소에만 스타일을 적용합니다. 이는 문서의 특정 부분에서 요소 간의 관계에 따라 세밀한 스타일 지정이 필요할 때 유용합니다.<br/>

* 제한된 범위: 인접 선택자는 바로 다음에 위치한 요소에만 스타일을 적용하기 때문에, 선택 범위가 매우 제한적입니다. 이는 스타일 적용의 정밀도를 높여줍니다.<br/>

* 사용 용도: 인접 선택자는 특정 요소 다음에 오는 요소에 마진, 패딩, 폰트 사이즈 등을 다르게 적용하고자 할 때, 또는 특정 요소의 바로 다음 요소에만 특별한 스타일을 적용하고자 할 때 사용됩니다.

## 8. 형제 선택자(General Sibling Selector)
형제 선택자(General Sibling Selector)는 CSS에서 특정 요소와 같은 부모를 공유하는 모든 형제 요소 중, 특정 요소 이후에 위치한 모든 요소를 선택하는 데 사용됩니다. 형제 선택자는 '~' 기호를 사용하여 표현되며, 이 선택자를 사용함으로써 특정 요소의 다음에 오는 모든 형제 요소에 스타일을 적용할 수 있습니다. 이는 특정 요소와 동일한 레벨에 있는 여러 요소들에 일관된 스타일을 적용하고자 할 때 매우 유용합니다. <br/>

아래 CSS 규칙은 _h2_ 태그와 같은 부모를 공유하며, _h2_ 태그 이후에 위치한 모든 _p_ 태그의 텍스트 색상을 빨간색으로 설정합니다. 이 규칙은 _h2_ 태그 바로 다음에 오는 _p_ 태그뿐만 아니라, _h2_ 이후에 위치한 모든 _p_ 태그에 적용됩니다.

````css
h2 ~ p {
  color: red;
}
````
__형제 선택자의 기본 문법__ <br/>
* 요소1: 요소2의 형제 요소 중 하나로, 요소2가 요소1 이후에 위치할 때 요소2를 선택합니다.<br/>

* 요소2: 요소1과 같은 부모를 공유하며 요소1 이후에 위치한 모든 요소를 선택합니다.<br/>

* ' _~_ ' 기호는 형제 선택자임을 나타냅니다.<br/>

__형제 선택자의 특징__ <br/>
* 유연성: 형제 선택자는 특정 요소 이후에 오는 모든 형제 요소에 스타일을 적용할 수 있어, 다양한 디자인 요구사항을 충족시킬 수 있습니다.<br/>

* 범위: 형제 선택자는 특정 요소의 바로 다음에 오는 요소뿐만 아니라, 그 이후에 위치한 모든 형제 요소를 대상으로 합니다. 이로 인해 더 넓은 범위의 요소에 스타일을 적용할 수 있습니다.<br/>

* 사용 용도: 형제 선택자는 폼 요소, 리스트, 기사의 본문 등과 같이 동일한 부모 요소를 공유하는 여러 요소들 사이에 스타일을 일관되게 적용하고자 할 때 주로 사용됩니다.

## 9. 그룹 선택자(Group Selector)
그룹 선택자(Group Selector)는 CSS에서 여러 요소를 한 번에 선택하여 스타일을 적용할 수 있게 해주는 기능입니다. 이를 통해 코드의 반복을 줄이고, 유지 보수를 보다 쉽게 할 수 있습니다. 그룹 선택자를 사용하면, 동일한 스타일 규칙을 여러 선택자에 적용하고자 할 때 각 선택자를 개별적으로 나열하는 대신 쉼표(,)로 구분하여 한 번에 지정할 수 있습니다. <br/>

아래 예시에서는 _h1_ ,  _h2_ 태그와 _class="important-text"_ 를 가진 모든 요소에 빨간색 글자와 굵은 글씨체를 적용합니다. 이렇게 함으로써, 각 선택자에 대해 개별적으로 동일한 스타일을 반복해서 적용하는 것을 피할 수 있습니다.

````css
h1, h2, .important-text {
  color: red;
  font-weight: bold;
}
````
__그룹 선택자의 기본 문법__ <br/>
* 선택자1, 선택자2, 선택자3: 스타일을 적용하고자 하는 각각의 선택자입니다. 이들 선택자는 쉼표로 구분되며, 지정된 스타일 규칙이 모두에게 적용됩니다.<br/>

* 스타일 선언: 모든 선택된 요소에 공통적으로 적용될 CSS 속성 및 값입니다.<br/>

__그룹 선택자의 장점__ <br/>
* 코드의 간결성: 여러 요소에 동일한 스타일을 적용할 때, 각 요소에 대해 스타일을 복사하고 붙여넣는 대신 한 번에 선언할 수 있어 코드가 더 간결해집니다.<br/>

* 유지 보수의 용이성: 스타일 변경이 필요할 때, 여러 곳을 수정하는 대신 한 곳에서만 변경하면 되므로 유지 보수가 용이해집니다.<br/>

* 효율성: 스타일 시트의 크기를 줄일 수 있으며, 웹 페이지의 로딩 시간을 단축시키는 데 도움이 됩니다.<

## 10. 속성 선택자(Attribute Selector)
속성 선택자(Attribute Selector)는 HTML 요소의 특정 속성이나 속성 값에 따라 요소를 선택할 수 있는 CSS 선택자입니다. 이를 통해 단순히 요소의 타입, 클래스, ID뿐만 아니라, 요소가 갖고 있는 속성에 기반하여 스타일을 적용할 수 있습니다. 속성 선택자는 여러 종류가 있으며, 각각 다른 조건에 따라 요소를 선택합니다.   


|속성 = 값|설명|
|---|---|
|[title]|특정 속성을 가지고 있는 요소를 모두 선택|
|[title="first h2"]|특정 속성을 가지고 있으며, 해당 속성의 속성값까지 일치하는 요소를 모두 선택|
|[title~="first"]|특정 속성의 속성값에 특정 문자열로 이루어진 하나의 단어를 포함하는 요소를 모두 선택|
|[title _ㅣ_ ="first"]|특정 속성의 속성값이 특정 문자열로 이루어진 하나의 단어로 시작하는 요소를 모두 선택|
|[title^="first"]|특정 속성의 속성값이 특정 문자열로 시작하는 요소를 모두 선택|
|[title$="first"]|특정 속성의 속성값이 특정 문자열로 끝나는 요소를 모두 선택|
|[title*="first"]|특정 속성의 속성값에 특정 문자열를 포함하는 요소를 모두 선택|


__문자열 속성 선택자__<br/>
CSS에서는 기본 속성 선택자 이외에도 문자열 속성 선택자를 제공합니다.
문자열 속성 선택자는 HTML 요소가 가지고 있는 특정 속성의 속성값 내에 특정 문자열을 확인하여 선택해 줍니다. <br/>

1. [title~="first"] :위의 예제에서는 title 속성값이 "first h2"인 요소와 "first p"인 요소만 선택됩니다. title 속성값이 "first-p"인 요소는 선택되지 않습니다.이처럼 [속성이름~="속성값"] 선택자는 title 속성값이 정확히 "first"인 요소나 띄어쓰기(whitespace)를 기준으로 인식되는 단어에 "first"를 포함한 요소만을 선택합니다. <br/>

2. [title|="first"] : 위의 예제에서는 title 속성값이 "first-p"인 요소만 선택됩니다.title 속성값이 "first h2"나 "first p"인 요소들은 선택되지 않습니다.이처럼 [속성이름 _|_ ="속성값"] 선택자는 title 속성값이 정확히 "first"인 요소나 "first" 바로 다음에 하이픈(-)으로 시작하는 요소만을 선택합니다. <br/>

3. [title^="first"] : 이 선택자는 [속성이름 _|_ ="속성값"] 선택자와는 달리 속성값이 특정 문자열로 시작하면 모두 선택해 줍니다.따라서 위의 예제에서는 title 속성값이 "first"로 시작되는 요소가 모두 선택됩니다 <br/>

4. [title$="first"] : 이 선택자는 특정 속성의 속성값이 특정 문자열로 끝나기만 하면 모두 선택해 줍니다. 따라서 위의 예제에서는 title 속성값이 "first"로 끝나는 요소가 모두 선택됩니다. <br/>

5. [title*="first"] : 이 선택자는 특정 속성의 속성값이 특정 문자열를 포함하기만 하면 모두 선택해 줍니다. 따라서 위의 예제에서는 title 속성값에 "first"를 포함하는 요소가 모두 선택됩니다. <br/>   

## 11. 가상 클래스 + 가상 요소 선택자(Pseudo Selector)
__가상 클래스 (:)__<br/>
가상 클래스는 요소가 특정 상태에 있을 때 스타일을 적용합니다. 예를 들어, 사용자가 마우스로 요소 위에 호버할 때, 특정 링크를 클릭했을 때의 상태 등을 가리킵니다. 가상 클래스는 웹 페이지의 동적인 상호작용을 디자인하는 데 유용합니다. <br/> 

__가상 요소 (::)__<br/>
가상 요소는 문서의 특정 부분에 스타일을 적용합니다. 이는 실제 문서 트리에 존재하지 않는 요소를 CSS에서 생성하여 스타일링할 수 있게 해줍니다. 주로 문서의 특정 내용 앞이나 뒤에 콘텐츠를 추가하거나, 첫 글자나 첫 줄에 특별한 스타일을 적용할 때 사용됩니다.


|코드|역활|
|---|---|
|:active|마우스 커서를 클릭한 순간부터 놓기 직전까지의 요소 상태를 선택합니다.|
|:checked|체크박스, 라디오 버튼 등 체크 가능한 요소가 체크된 상태일 때 선택합니다|
|:focus|입력 폼에서 키보드의 입력을 기다리는 상태의 요소를 선택합니다|
|:hover|마우스 커서가 요소 위에 있을 때의 상태를 선택합니다.|
|:first-child|부모 요소의 첫 번째 자식 요소를 선택합니다.|
|:last-child|부모 요소의 마지막 자식 요소를 선택합니다.|
|:nth-child(n)|부모 요소의 n번째 자식 요소를 선택합니다. n은 정수이거나 공식일 수 있습니다.|
|:link|아직 클릭하지 않은 링크 상태를 선택합니다.|
|:lang|요소의 언어 속성에 따라 스타일을 적용합니다.|
|:visited|이미 방문한 링크의 상태를 선택합니다|
|::after|요소의 내용 끝난 다음에 콘텐츠를 삽입할 때 사용됩니다.|
|::before|요소의 내용이 시작되기 전에 콘텐츠를 삽입할 때 사용됩니다.|
|::selection|사용자에 의해 선택된 텍스트 영역에 스타일을 적용할 때 사용됩니다.|
|::first-line| 요소의 첫 번째 줄에만 스타일을 적용할 때 사용됩니다.|
|::first-letter|요소의 첫 글자에만 스타일을 적용할 때 사용됩니다.|


__:와 ::의 주된 차이점__<br/>
가상 클래스와 가상 요소를 구분하는 데 있습니다. 가상 클래스(:)는 요소의 상태를 기반으로 스타일을 적용하는 반면, 가상 요소(::)는 문서의 특정 부분을 선택하여 스타일을 적용합니다.

## 12. 종속 선택자
CSS에서 선택자에 종속된 선택자, 또는 다른 말로 자식 선택자(child selector)와 후손 선택자(descendant selector)는 특정 요소들의 계층적 관계를 기반으로 스타일을 적용하는 방법입니다. 이러한 선택자를 사용하면, 보다 구체적인 범위 내에서 스타일을 정의할 수 있어 웹페이지의 다양한 요소들을 효과적으로 제어할 수 있습니다.

__1. 후손 선택자 (Descendant Selector)__<br/>
이 규칙은 _div_ 요소 내의 모든 _p_ 요소에 적용됩니다. _div_ 바로 아래 있지 않은, 더 깊이 있는 _p_ 요소에도 스타일이 적용됩니다.
````css
div p {
  color: red;
}
````

__2. 자식 선택자 (Child Selector)__  <br/>
자식 선택자는 >로 표현되며, 특정 요소의 직접적인 자식에만 스타일을 적용합니다.
이 규칙은 _div_ 요소의 바로 아래 있는 _p_ 요소에만 적용됩니다. _div_ 안에 더 깊이 있는 _p_ 요소에는 적용되지 않습니다.
````css
div p {
  color: red;
}
````

__3. 인접 형제 선택자 (Adjacent Sibling Selector)__<br/>
인접 형제 선택자는 +로 표현되며, 특정 요소 바로 다음에 오는 형제 요소 하나에만 스타일을 적용합니다. 이 규칙은 _h1_ 태그 바로 다음에 오는 _p_ 태그에만 적용됩니다.
````css
h1 + p {
  font-weight: bold;
}
````

__4. 일반 형제 선택자 (General Sibling Selector)__<br/>
일반 형제 선택자는 ~로 표현되며, 특정 요소 이후에 오는 모든 형제 요소에 스타일을 적용합니다. 이 규칙은 _h1_ 태그 이후에 오는 모든 _p_ 태그에 적용됩니다.
````css
h1 ~ p {
  font-style: italic;
}
````

## 13. 선택자의 우선순위
CSS에서 선택자의 우선순위는 스타일이 적용되는 순서를 결정합니다. 복잡한 웹 페이지에서는 여러 CSS 규칙이 동일한 요소에 적용될 수 있으며, 이러한 경우 선택자의 우선순위가 중요해집니다. 선택자의 우선순위는 가중치(specificity)를 기반으로 결정되며, 다음과 같은 순서로 평가됩니다.<br/>

위의 코드에서, 만약 여러 규칙이 동일한 요소에 적용된다면 #navbar가 가장 높은 가중치를 가지므로 그 스타일이 적용됩니다.

````css
#navbar { background-color: blue; } /* 가중치: 0,1,0,0 */
div.navbar { background-color: green; } /* 가중치: 0,0,1,1 */
.nav { background-color: red; } /* 가중치: 0,0,1,0 */
div { background-color: yellow; } /* 가중치: 0,0,0,1 */
* { background-color: black; } /* 가중치: 0,0,0,0 */
````
__우선순위 순서__<br/>
* 중요도(Importance)<br/> 
    !important가 적용된 스타일이 가장 높은 우선순위를 가집니다.

* 소스순서(Source Order)<br/>
    CSS 코드 내에서 나중에 선언된 스타일이 이전에 선언된 스타일을 덮어씁니다. 이는 우선순위를 가진 경우에만 적용됩니다.<br/>
    
* 가중치(Specificity)<br/>
    가중치가 높은 선택자가 낮은 선택자보다 우선합니다. 가중치는 다음과 같이 계산됩니다.<br/>


__가중치 계산__<br/>

가중치를 비교할 때, 왼쪽에서 오른쪽으로 비교하며, 각 위치에서 더 높은 숫자를 가진 선택자가 우선합니다. 예를 들어, 0,1,0,0(아이디 선택자)은 0,0,10,10(10개의 클래스 선택자와 10개의 태그 선택자)보다 우선합니다.<br/>

* 인라인 스타일(HTML 내의 style 속성 사용): 1,0,0,0<br/>

* 아이디 선택자(#id): 0,1,0,0<br/>

* 클래스 선택자(.class), 속성 선택자([type="text"]), 가상 클래스(:hover): 0,0,1,0<br/>

* 태그 선택자(div), 가상 요소(::before): 0,0,0,1<br/>

* 전체 선택자(*), 관계 선택자(+, >, ~,  )는 가중치에 영향을 주지 않습니다.<br/>

__정리__<br/>

CSS 선택자의 우선순위는 복잡한 웹 페이지에서 예상치 못한 스타일 문제를 해결하는 데 중요합니다. 가중치 계산을 이해하고 올바르게 적용하면, 원하는 요소에 정확한 스타일을 적용할 수 있습니다.