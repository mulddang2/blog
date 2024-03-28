---
layout: post
title: "[JavaScript] infiniteScroll 기법- Intersection Observer API 사용"
date: 2023-06-07 19:31:29 +0900
category: JavaScript
---

### 무한스크롤이란?

사용자가 스크롤을 끝까지 내리면 더 많은 콘텐츠가 자동으로 로드되는 웹 디자인 기법입니다. pagination을 제거하고 사용자가 사이트에서 보내는 시간을 늘릴 수 있습니다.

무한 스크롤의 개념은 사용자에게 "원활한" 느낌을 주지만 한 번에 너무 많은 데이터를 요청하여 서버에 과부하를 주지 않는 방식으로 서버에서 데이터를 로드하는 데 사용됩니다.

### Intersection Observer API를 이용하여 무한 스크롤링을 구현하는법

<span style="color: #333; background-color: pink;">**1. JavaScript로 목록을 생성하기**</span>
먼저 빈 목록 페이지를 생성한 다음 JavaScript의 setTimeout을 통해 데모 데이터를 로드하고 마지막으로 데이터를 페이지에 렌더링합니다.

<span style="color: #333; background-color: pink;">**2. Intersection Observer API로 더 로드하기**</span>
Intersection Observer API는 요소가 보이는지 여부를 관찰할 수 있습니다. 이를 사용하여 무한 스크롤을 완료할 때 목록 맨 아래에 요소를 추가해야 합니다. 요소가 표시되면 더 많은 콘텐츠를 로드합니다.

<span style="color: #333; background-color: pink;">**3. 최적화를 위해서, Observer가 좀 더 일찍 실행되도록 loading...과 같은 자리 표시 요소를 추가 하는 방법도 있습니다.**</span>

### 결론

스크롤 이벤트를 수신하여 무한스크롤을 할 수도 있지만 스크롤 위치를 계속 계산해야 합니다. 하지만 Intersection Observer API를 사용하는 동안 콜백 기능만 제공하면 대상 요소가 뷰포트에 진입하면 자동으로 실행되므로 간단할 뿐만 아니라 성능도 향상됩니다.
<br />
<br />

**참고자료**

<hr>
- How to Implement Infinite Scrolling With JavaScript:<br />
[https://webdesign.tutsplus.com/tutorials/how-to-implement-infinite-scrolling-with-javascript—cms-37055](https://webdesign.tutsplus.com/tutorials/how-to-implement-infinite-scrolling-with-javascript—cms-37055){:target="\_blank"}

- How to Implement Infinite Scrolling with Intersection Observer API: <br />[https://javascript.plainenglish.io/how-to-implement-infinite-scrolling-with-intersection-observer-api-9f2bc9ad8662](https://javascript.plainenglish.io/how-to-implement-infinite-scrolling-with-intersection-observer-api-9f2bc9ad8662){:target="\_blank"}
- Easy Endless Infinite Scroll With JavaScript: <br />
  [https://codingbeautydev.com/blog/infinite-scroll-javascript/](https://codingbeautydev.com/blog/infinite-scroll-javascript/){:target="\_blank"}
