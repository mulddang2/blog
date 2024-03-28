---
layout: post
title: "[Optimizing] Font를 Preload 방법, Web Font 최적화 방법"
date: 2023-05-07 19:31:29 +0900
category: Optimizing
---

로컬 폰트가 있을 때, 로딩법은 사용자의 기기에 이미 설치되어 있는 폰트 파일을 사용하여 로딩합니다. 그렇기 때문에, 웹폰트보다 로컬폰트가 로딩속도 측면에서 빠른 장점이 있습니다.
하지만, 내 컴퓨터에 해당 웹페이지에서 필요한 폰트가 없다면 대체 폰트를 사용하게 되어, 페이지의 디자인이 깨질 수 있다는 단점이 있습니다.
웹폰트는 서버에서 제공되는 폰트 파일을 사용하여 렌더링 하기 때문에 로딩시간이 더 길어질 수 있습니다.
따라서 웹 폰트 최적화를 위한 방법들을 살펴보도록 하겠습니다.

### 웹 폰트 최적화하는 방법은?

#### 1. (HTML) link rel=“preload” 사용하기

```
<link rel="preload" href="url" as="font" type="font/woff2" crossorigin />
```

head 태그 안에 사용하는 링크이며, preload 를 입력하게 되면 폰트를 초기에 요청하게 됩니다.
폰트파일을 미리 다운로드한다면 사이트에 방문할 때마다 폰트를 새로 렌더링 하지 않아도 되기 때문에 로딩속도가 향상되어 최적화 될 수 있다는 장점이 있습니다.
하지만, 주의점으로는 해당페이지에서 꼭 필요한 폰트만 preload 해야한다는 것이다.
해당 페이지에서 사용하지 않는데 preload를 사용할 경우 해당폰트를 우선시하고,  
너무 많은 폰트를 proload 하게 될 경우 로딩시간이 길어지는 문제가 발생하게 되기 때문입니다.

#### 2. CSS에서 font-face를 사용할 때, font-display: swap 사용

font-display는 글꼴 다운로드 기간(block-swap-failure)마다 글자를 어떻게 보여줄지 결정하는 CSS 속성입니다.
`font-display: swap` 을 사용하게 되면, 글꼴이 다운되기 전까지, 시스템 글꼴을 사용하다가 다운로드가 완료되면 웹폰트를 적용하는 방법입니다.
사용자에게 처음부터 아예 글 자체가 보이지 않는다면 사용자 경험 측면에서 좋지 못할 것이기 때문에 이 속성을 사용함으로써 웹폰트 최적화가 가능합니다.

#### 3. 저용량 순으로 Font format을 사용하여 폰트를 적용하기

모든 브라우저에서 지원하는 Font format은 TTE, WOFF, WOFF2가 있습니다.
이 때 용량이 큰 순서는 WOFF2 < WOFF < EOT < TTF 순입니다. 따라서 우리는 용량이 적은 순서대로 폰트를 적용하도록 하면 웹 폰트 최적화가 가능합니다. 하지만, 브라우저마다 지원 format이 다르기 때문에 미리 확인은 필수입니다!!

<figure style="display:block; text-align:center;">
  <img src="https://velog.velcdn.com/images/js4072751/post/391a8c79-b9f6-4ee4-b1ff-b0b943ec98e5/image.png"
       style="width: 500px; margin:0px auto">
  <figcaption style="text-align:center; font-size:15px; color:#808080">
    출처: <a href="" style="color: blue"> https://www.w3schools.com/Css/css3_fonts.asp</a>
  </figcaption>
</figure>

<br />
<br />

**참고사이트**

<hr />
- Font Preload란?<br />
[https://qorguswp.com/entry/Font-Preload-font-preload-%EB%B0%A9%EB%B2%95-%EB%B0%8F-%EC%A0%95%EB%A6%AC](https://qorguswp.com/entry/Font-Preload-font-preload-%EB%B0%A9%EB%B2%95-%EB%B0%8F-%EC%A0%95%EB%A6%AC){:target="\_blank"}
- [HTML/CSS] Font를 Preload하는 방법과 이유<br />
[https://velog.io/@xnelb013/HTMLCSS-Font%EB%A5%BC-Preload%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95%EA%B3%BC-%EC%9D%B4%EC%9C%A0](https://velog.io/@xnelb013/HTMLCSS-Font%EB%A5%BC-Preload%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95%EA%B3%BC-%EC%9D%B4%EC%9C%A0){:target="\_blank"}
- [CSS] font-display, 글꼴 렌더링 방식을 변경하는 방법<br />
[https://mong-blog.tistory.com/entry/CSS-font-display-%EA%B8%80%EA%BC%B4-%EB%A0%8C%EB%8D%94%EB%A7%81-%EB%B0%A9%EC%8B%9D%EC%9D%84-%EB%B3%80%EA%B2%BD%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95](https://mong-blog.tistory.com/entry/CSS-font-display-%EA%B8%80%EA%BC%B4-%EB%A0%8C%EB%8D%94%EB%A7%81-%EB%B0%A9%EC%8B%9D%EC%9D%84-%EB%B3%80%EA%B2%BD%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95){:target="\_blank"}
- 글꼴 형식 이해: TTF, OTF, WOFF, EOT & SVG<br />
[https://medium.com/@aitareydesign/understanding-of-font-formats-ttf-otf-woff-eot-svg-e55e00a1ef2](https://medium.com/@aitareydesign/understanding-of-font-formats-ttf-otf-woff-eot-svg-e55e00a1ef2){:target="\_blank"}
