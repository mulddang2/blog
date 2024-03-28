---
layout: post
title: "[CSS] Flex와 Grid에 대해서 비교 : 레이아웃"
date: 2023-05-21 19:31:29 +0900
category: CSS
---

### 1. Flex를 사용하면 적합한 레이아웃

- **공간을 할당하고 항목을 유연하게 정렬해야 하는 레이아웃**에 적합합니다.
- Flex 레이아웃은 주로 콘텐츠의 흐름에 집중하여 유연한 배치를 가능하게 합니다.
- 다양한 뷰포트 크기에서 플렉스 항목의 할당을 최적화하여 완전히 유동적인 레이아웃을 구성하고자 할 때 유용합니다.
- Flexbox를 사용하여 단일 축(가로 또는 세로)에서 항목을 정렬하고 공간 배분을 조절할 때, 유용합니다.

### 2. Grid를 사용하면 적합한 레이아웃

- **콘텐츠의 정확한 배치에 중점을 둔 레이아웃**에 적합합니다.
- CSS Grid는 그리드 셀에 가로 및 세로 축을 따라 정렬된 항목들을 배치하는 것에 초점을 둡니다.
- Grid를 사용하면 레이아웃 내에서 항목의 위치를 정확하게 제어할 수 있어 정확한 콘텐츠 배치가 가능합니다.
- `grid-template-rows` 및 `grid-template-columns`과 같은 속성을 사용하여 항목의 크기와 위치를 정확하게 계산할 수 있습니다.
- Grid는 깨진 레이아웃, 비대칭 레이아웃, 겹치는 레이아웃과 같이 비정상적인 레이아웃을 구성하는 데 특히 적합합니다.
- CSS Grid를 사용하면 미디어 쿼리를 사용하지 않고도 반응형 레이아웃을 구성할 수 있습니다.

<br />
<br />

**참고자료**

<hr />
- CSS Grid vs. Flexbox: Which Should You Use and When?<br />
  [https://webdesign.tutsplus.com/articles/flexbox-vs-css-grid-which-should-you-use—cms-30184](https://webdesign.tutsplus.com/articles/flexbox-vs-css-grid-which-should-you-use—cms-30184){:target="\_blank"}
