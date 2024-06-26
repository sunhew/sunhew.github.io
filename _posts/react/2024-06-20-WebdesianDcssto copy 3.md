---
layout: post
title: 리액트의 네이티브
date: 2024-06-16 16:59 +0900
description: REACT
image: ../assets/img/react02.jpg
category: react
tags: react네이티브 네이티브 react react개념
published: true
sitemap: true
---

# REACT
해당 포스팅에서는 REACT의 네이티브를 다룹니다.  <br />


## __이번 포스팅 목차__
* REACT의 네이티브 <br/>

## __리액트 네이티브의 주요 특징__<br/>
리액트 네이티브(React Native)는 리액트(React)를 사용하여 __iOS__ 및 __안드로이드__ 모바일 애플리케이션을 개발할 수 있게 해주는 __프레임워크__ 입니다. 리액트 네이티브는 Facebook에서 개발되었으며, __한 번 작성된 코드를 여러 플랫폼에서 사용할 수 있게 해주는 특징__ 이 있습니다.

### __REACT의 특징과 장단점__
리액트는 __컴포넌트 기반 아키텍처, 가상 DOM, 단방향 데이터 흐름, JSX, 풍부한 생태계와 커뮤니티, React Hooks 등의 특징__ 을 가지고 있습니다. 이러한 특징들은 리액트를 강력하고 유연한 도구로 만들지만, 동시에 초기 학습 비용과 복잡한 설정, 의존성 관리 등의 단점도 존재합니다. 이를 잘 이해하고 활용하면, 효율적이고 유지보수하기 쉬운 애플리케이션을 개발할 수 있습니다.

#### __크로스 플랫폼 개발__

* __공통 코드베이스__: 한 번 작성된 코드를 iOS와 안드로이드에서 동시에 사용할 수 있어 __개발 효율성__ 을 높입니다.

* __플랫폼별 최적화__: 필요에 따라 iOS와 안드로이드에 특화된 코드를 작성할 수 있어, 각 플랫폼의 __네이티브 기능을 최대한 활용__ 할 수 있습니다.

#### __네이티브 컴포넌트 사용__

* __네이티브 UI__: 리액트 네이티브는 __네이티브 UI 컴포넌트__ 를 사용하여 성능이 뛰어난 모바일 애플리케이션을 만들 수 있습니다.

* __네이티브 모듈__: 필요에 따라 __네이티브 코드를 작성__ 하여 리액트 네이티브에서 사용할 수 있습니다.

#### __핫 리로딩(Hot Reloading)__

* __빠른 개발 사이클__: 코드 변경 시 전체 애플리케이션을 다시 컴파일하지 않고, __변경된 부분만 빠르게 업데이트__ 할 수 있습니다.

* __실시간 피드백__: 개발자가 __즉시 변경 사항을 확인__ 할 수 있어, __개발 속도__ 가 빨라집니다.

#### __풍부한 생태계와 커뮤니티__

* __오픈 소스 라이브러리__: 다양한 __오픈 소스 라이브러리와 도구__ 들이 리액트 네이티브와 호환되어 __개발 생산성__ 을 높입니다.

* __커뮤니티 지원__: 방대한 __커뮤니티와 자료__ 를 통해 문제 해결과 학습이 용이합니다.

### __리액트 네이티브의 주요 구성 요소__

#### __JSX__

* 리액트 네이티브에서도 __JSX__ 를 사용하여 UI를 정의합니다. __JSX__ 는 HTML과 유사한 문법을 사용하여 __가독성이 높고 직관적__ 입니다.

#### __컴포넌트__

* __View__: __HTML__ 의 `div`와 유사한 역할을 하며, __컨테이너 역할__ 을 합니다.

* __Text__: 텍스트를 표시하는 데 사용됩니다.

* __Image__: __이미지__ 를 표시하는 데 사용됩니다.

* __ScrollView__: __스크롤 가능한 영역__ 을 만들 때 사용됩니다.

* __Touchable__: 터치 가능한 요소를 만들 때 사용되는 컴포넌트입니다. `TouchableOpacity`, `TouchableHighlight`, `TouchableWithoutFeedback` 등이 있습니다.

#### __스타일링__

* 리액트 네이티브는 CSS가 아닌 __자바스크립트 객체__ 를 사용하여 스타일을 정의합니다. 이는 CSS와 유사하지만, __camelCase__ 문법을 사용합니다.

```javascript
const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#F5FCFF',
  },
  welcome: {
    fontSize: 20,
    textAlign: 'center',
    margin: 10,
  },
});
```

#### __네비게이션__

* 모바일 애플리케이션에서는 __화면 간의 전환__ 이 중요합니다. 리액트 네이티브는 이를 위해 다양한 __네비게이션 라이브러리__ 를 제공합니다. `react-navigation`이 가장 널리 사용됩니다.

#### __상태 관리__

* 리액트 네이티브에서도 상태 관리를 위해 리액트의 `useState`, `useEffect` 훅을 사용할 수 있습니다. 복잡한 상태 관리가 필요한 경우 __Redux, MobX__ 와 같은 라이브러리를 사용할 수 있습니다.

### __리액트 네이티브의 장단점__
리액트 네이티브는 __크로스 플랫폼 개발, 네이티브 컴포넌트 사용, 핫 리로딩 등의 특징을 통해 빠르고 효율적__ 으로 iOS와 안드로이드 애플리케이션을 개발할 수 있게 해주는 프레임워크입니다. 이를 사용하면 __개발 생산성__ 을 크게 향상시킬 수 있지만, __네이티브 코드 작성의 필요성, 성능 한계, 의존성 관리__ 등의 주의사항도 고려해야 합니다.

#### __장점__
* __코드 재사용성__: 한 번 작성된 코드를 iOS와 안드로이드에서 모두 사용할 수 있어 __개발 시간이 단축__ 됩니다.

* __성능__: __네이티브 컴포넌트__ 를 사용하여 성능이 뛰어난 애플리케이션을 만들 수 있습니다.

* __개발 생산성__: __핫 리로딩__ 기능을 통해 __빠른 개발 사이클__ 을 유지할 수 있습니다.

* __큰 커뮤니티__: __풍부한 라이브러리와 도구들, 방대한 커뮤니티 지원__ 을 받을 수 있습니다.

#### __단점__
* __네이티브 코드 작성 필요__: 모든 기능을 자바스크립트로만 구현할 수 없으므로, __네이티브 코드를 작성해야__ 하는 경우가 있습니다.

* __성능 한계__: __네이티브 앱__ 보다는 성능이 약간 떨어질 수 있습니다. 특히 복잡한 애니메이션이나 고성능 연산이 필요한 경우에는 __성능 저하__ 가 발생할 수 있습니다.

* __의존성 관리__: 다양한 라이브러리와 도구들을 사용하다 보면 __의존성 관리가 복잡__ 해질 수 있습니다.