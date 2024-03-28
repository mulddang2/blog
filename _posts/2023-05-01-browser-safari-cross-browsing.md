---
layout: post
title: "[Browser] Safari 브라우저에서 크로스브라우징 하기"
date: 2023-05-01 19:31:29 +0900
category: Browser
---

오늘은 iOS Safari 환경에서 일어날 수 있는 이슈들과 사파리를 위한 meta 태그들에 대한 고민을 해보았습니다.

## 1. 모바일 서비스 중에 발생할 수 있는 다양한 호환성에 대한 이슈

참고 사이트 https://www.powermapper.com/products/sortsite/rules/bugsafari/ 에서 볼 수 있듯 스크롤을 내려보다보면 생각보다 많은 것을 알 수 있는데요..

이 중에서, 활용도가 높을 듯한데 iOS Safari에서는 주의해서 사용해야 할 몇가지를 꼽아보았습니다.

### 🔶 issue-1

#### position: sticky 모바일에서 다른 브라우저 사용 시에는 잘 동작할 수 있지만, 아이폰에서는 iOS13(2019-09-19 출시) 이전 버전에서 작동하지 않을 수 있습니다.

<figure style="display:block; text-align:center;">
  <img src="https://velog.velcdn.com/images/js4072751/post/9bbc7aad-af59-445a-b63b-94fb4577cdc5/image.png"
       style="width: 500px; margin:0px auto">
  <figcaption style="text-align:center; font-size:15px; color:#808080">
    출처: <a href="https://developer.mozilla.org/ko/docs/Web/CSS/position#%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80_%ED%98%B8%ED%99%98%EC%84%B1" style="color: blue">mdn</a>
  </figcaption>
</figure>

#### solution

position: sticky 속성 사용시, iOS13 이전 버전에서는 속성 앞의 접두사로 -webkit를 사용하여 구현하여야합니다.

>

```css
position: -webkit-sticky; /* Safari */
```

매번 스타일을 정의 할 때마다 벤더 프리픽스를 설정하면 코드가 길어질 수 있을 것 같아 우려도 되는데요. 역시 <u>프리픽스를 지원하는 –prefix-free 플러그인도 있다고 합니다.</u>

### 🔶 issue-2

#### Safari iOS 에서만 rotate x, y, z 값을 사용할 수 없습니다.

<figure style="display:block; text-align:center;">
  <img src="https://velog.velcdn.com/images/js4072751/post/8de16069-ad54-4ed0-9e52-83be9f26508d/image.png"
       style="width: 500px; margin:0px auto">
  <figcaption style="text-align:center; font-size:15px; color:#808080">
    출처: <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/rotate#browser_compatibility" style="color: blue">mdn</a>
  </figcaption>
</figure>

#### solution

rotat속성에서 값으로 x, y, z 대신, transform: rotateY() 등을 사용하면 iOS에서도 것이 호환성을 높일 것이라 생각됩니다.

<figure style="display:block; text-align:center;">
  <img src="https://velog.velcdn.com/images/js4072751/post/4de0e579-570b-4a8e-9797-22d76d8a0dbc/image.png"
       style="width: 500px; margin:0px auto">
  <figcaption style="text-align:center; font-size:15px; color:#808080">
    출처: <a href="" style="color: blue">mdn</a>
  </figcaption>
</figure>

```css
#box2:hover {
  rotate: y 180deg;
} /* 이렇게 rotate 속성으로 y값을 넣기보다는,, */
```

```css
#box2:hover {
  transform: rotateY(180deg);
} ⭕⭕⭕⭕✅🆗
/* 이렇게 transform 속성으로 rotate를 사용하는 것이 호환성 높습니다! */
```

## 2. iOS에서 Meta tag의 다른 설정 방법

### 🔶 apple-mobile-web-app-capable

```
<meta name="apple-mobile-web-app-capable" content="yes">
```

- 역할: 브라우저의 UI ( URL바) 를 숨길 수 있도록 하여, Web App이 마치 일반 Native App 처럼 화면 전체의 활용이 가능하도록 합니다.

- 사용법:
  content값이 “yes”인 경우, 전체화면 모드로 실행됩니다. “no”인 경우 일반모드로 작동합니다.
  javascript에서 window.navigator.standalone 속성을 사용하여 전체화면 모드를 예측할 수 있습니다.

### 🔶 apple-mobile-web-app-status-bar-style

```
<meta name="apple-mobile-web-app-status-bar-style" content="black">
```

- 역할: 상태바(시간, 배터리표시, 와이파이 등이 표시된 부분)의 색상을 지정하여, 앱 전체에서 화면색과 통일감을 줄 수 있습니다.

- 사용법:

  1. 이 메타 태그는 apple-apple-mobile-web-app-capable에 설명된 대로 전체 화면 모드를 먼저 지정하지 않으면 효과가 없습니다.
  2. content=“” 속성에서 지정한 default(검정색 텍스트에 흰색 배경), black(검정), black-translucent(흰색 텍스트와 웹앱 본문과 동일한 배경색)을 사용할 수 있습니다.
  <hr>

black-translucent으로 지정한 경우, 아래 이미지와 같이 본문과의 통일감 을 줄 수 있습니다.

<figure style="display:block; text-align:center;">
  <img src="https://velog.velcdn.com/images/js4072751/post/d525a741-34bf-4b1b-bcb0-9300eb2c2332/image.png"
       style="width: 500px; margin:0px auto">
  <figcaption style="text-align:center; font-size:15px; color:#808080">
    출처: <a href="https://medium.com/appscope/changing-the-ios-status-bar-of-your-progressive-web-app-9fc8fbe8e6ab" style="color: blue">https://medium.com/appscope/changing-the-ios-status-bar-of-your-progressive-web-app-9fc8fbe8e6ab</a>
  </figcaption>
</figure>
<hr>

### 🔶 format-detection

```html
<meta name="format-detection" content="telephone=no" />
```

- 역할: 전화번호와 같은 형식의 모든 문자열을 감지 유무
- 사용법: 전화번호와 같은 형식의 모든 문자열을 감지하고 전화를 걸 수 있는데, content=“telephone=no”로 설정되어 있는 경우, 이 기능이 비활성화됩니다.

### 🔶 viewport

```html
<meta
  name="viewport"
  content="width = 320,
       initial-scale = 2.3, user-scalable = no"
/>
```

- 역할: iOS에서 페이지를 표시할 때 사용하며, 창 크기를 변경할 수 있습니다.
- 사용법:

  1. 여러 개의 속성을 사용할 경우, 쉼표로 구분하여 사용하여야합니다.

  2. content : width [number | device-width], height [number | device-height], initial-scale [number],user-scalable [no | yes]
     <br />

- 설명:
  - meta name = "viewport" : 뷰포트 선언
  - content= “width=device-width” : 디바이스 크기에 맞추겠다고 선언
  - initial-scale=1 : 초기 크기(기본 가득찬 화면)
  - minimum-scale=1 : 최소 크기 설정 (기본값: 0.25, 범위: 0~10.0)
  - maximum-scale=1 : 최대 크기 설정 (최대배율 범위: 0~10.0)
  - user-scalable=no (사용자 단말의 확대가능 사용 유무선언, no 속성은 스크롤 할 때 input box에 enter가 입력되는 것을 막는 역할을 합니다.)
    <br />
    <br />

**참고사이트**

<hr />
- [https://www.powermapper.com/products/sortsite/rules/bugsafari/](https://www.powermapper.com/products/sortsite/rules/bugsafari/){:target="\_blank"}
- [https://developer.apple.com/library/archive/documentation/AppleApplications/Reference/SafariHTMLRef/Articles/MetaTags.html](https://developer.apple.com/library/archive/documentation/AppleApplications/Reference/SafariHTMLRef/Articles/MetaTags.html){:target="\_blank"}
- [https://medium.com/appscope/changing-the-ios-status-bar-of-your-progressive-web-app-9fc8fbe8e6ab](https://medium.com/appscope/changing-the-ios-status-bar-of-your-progressive-web-app-9fc8fbe8e6ab)
- [https://elad.medium.com/css-position-sticky-how-it-really-works-54cd01dc2d46](https://elad.medium.com/css-position-sticky-how-it-really-works-54cd01dc2d46){:target="\_blank"}
- [https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/rotateY#browser_compatibility](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/rotateY#browser_compatibility)
- [https://developer.mozilla.org/en-US/docs/Web/CSS/rotate#browser_compatibility](https://developer.mozilla.org/en-US/docs/Web/CSS/rotate#browser_compatibility){:target="\_blank"}
