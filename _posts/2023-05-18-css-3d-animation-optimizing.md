---
layout: post
title: "[CSS] CSS에서 3D 애니메이션과 최적화 방법"
date: 2023-05-18 19:31:29 +0900
category: CSS
---

CSS에서 3D를 활용한 애니메이션은 왜 사용해야 할까요? 이번 포스팅에서는 CSS에서 3D를 사용하는 이유와 애니메이션 최적화 방법에 대해 알아보겠습니다.

### 1. CSS에서 3D를 사용하는 이유

CSS에서 3D를 사용하는 이유는 여러 가지가 있습니다.

- 외부 라이브러리를 사용하지 않아 편리합니다.
- 하드웨어 가속을 사용하면 성능이 향상됩니다.
- 가상 클래스를 사용하여 특별한 효과를 만들어낼 수 있습니다.
- 자바스크립트를 통해 애니메이션 종료 시점을 감지할 수 있습니다.
- 전처리기와 함께 사용하여 일관성을 유지하고 변수를 활용할 수 있습니다.
- Media Query를 사용하여 애니메이션을 수정할 수 있어 개발 속도를 향상시킬 수 있습니다.

### 2. 애니메이션 최적화 방법

CSS 애니메이션을 최적화하는 방법은 다음과 같습니다.

- will-change 속성을 사용하여 브라우저에 애니메이션 요소의 변경 사항을 알립니다.
- will-change: transform; 속성을 사용하여 애니메이션을 적용할 요소 앞에 추가합니다.
- 필요한 경우 will-change 속성에 다른 속성(ex: will-change: opacity;)을 명시하여 변경될 속성을 미리 알려줄 수도 있습니다.

### 3. 애니메이션 최적화에 대한 주의 사항

애니메이션 최적화를 위해 다음과 같은 주의 사항을 염두에 두어야 합니다.

- will-change 속성을 직접 CSS에 추가하기보다는 JavaScript를 사용하여 속성을 제어하는 것이 좋습니다.
- 성능 향상을 위해 모든 애니메이션에 최적화를 적용하는 것은 필요하지 않을 수 있으므로 신중하게 판단해야 합니다.
- will-change 속성을 과도하게 사용하지 않도록 주의해야 합니다. 이는 리소스 낭비나 성능 저하를 초래할 수 있습니다.
- 애니메이션을 최적화할 때는 변경이 발생하기 전에 will-change 속성을 적용하여 브라우저에 최적화 타이밍을 알려주는 것이 좋습니다.
- will-change 속성의 브라우저 지원 범위는 caniuse.com을 참고하여 사용할 수 있습니다.

이렇게 CSS에서 3D 애니메이션을 활용하고 최적화하는 방법에 대해 알아보았습니다.
<br />
<br />

**참고자료**

<hr />
- mdn web docs (will-change)<br />
[https://developer.mozilla.org/ko/docs/Web/CSS/will-change](https://developer.mozilla.org/ko/docs/Web/CSS/will-change){:target="\_blank"}
- will-change 속성으로 CSS 애니메이션을 최적화하는 방법<br />
[https://www.developerdrive.com/how-to-optimize-css-animation-with-the-will-change-property/](https://www.developerdrive.com/how-to-optimize-css-animation-with-the-will-change-property/){:target="\_blank"}
- 다양한 애니메이션 기술의 장단점<br />
[https://viscircle.de/the-advantages-and-disadvantages-of-different-animation-technologies/?lang=en](https://viscircle.de/the-advantages-and-disadvantages-of-different-animation-technologies/?lang=en){:target="\_blank"}
