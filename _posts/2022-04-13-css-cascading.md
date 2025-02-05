---
layout: post
title: "[CSS] CSS에서 Cascading이란?"
date: 2024-08-02 11:33:29 +0900
category: CSS
tag: [코드잇스프린트, 스프린트OON기, 취업까지달린다]
---

### Cascading의 의미
CSS에서 'C'는 Cascading의 줄임말입니다.
브라우저가 바라보았을 때, **웹요소에 겹치는 CSS 속성값이 있는 경우 어떤 것을 따라야할지 브라우저가 스타일을 결정할 때, '계단식'으로 적용된다는 의미** 입니다.
다시 말해, CSS는 계단식 형태로 우선순위가 있는 스타일 시트입니다. 스타일의 우선순위가 있기 때문에, 스타일이 충돌되지 않는 이점도 있습니다.

### 그렇다면, CSS 스타일에서 어떤 기준으로 우선순위를 매기는 걸까요?

#### 1. 명시도: 구체적일수록 우위를 차지
  - 스타일 적용 범위가 좁고 구체적일수록 높습니다.
  - 명시도는 일반적으로 다음과 같은 순서로 결정됩니다.<br>
  - <span><u>인라인 스타일(HTML내에 style 속성을 직접 입력한 경우) > id 선택자 > class 스타일 > 요소 선택자</u></span>
  - 😀 명시도 계산해주는 사이트! -> [https://specificity.keegan.st/](https://specificity.keegan.st/) 

#### 2. 중요도: !important 키워드가 있는 경우 우위를 차지  
  - !important를 붙이면 어떤 스타일보다 우선 적용됩니다.
  - <span style='background-color: #FFFF00'><u>!important > 인라인 스타일(HTML내에 style 속성을 직접 입력한 경우) > id 선택자 > class 스타일 > 요소 선택자</u></span>  

#### 3. 소스순서: 소스순서가 더 나중에 작성된 스타일이 우위를 차지
  - 상대적으로 아래에 있는 속성값이 우선 순위가 높아져 위에 적용한 속성값은 아래 속성값에 덮어쓰기가 됩니다.  

### CSS 소스 외에도 우선적용되는 요인들...

우리가 작성하는 CSS 소스 스타일(웹문서 제작자 스타일) 이외에도 컴퓨터 사용자가 지정한 스타일, 브라우저가 기본으로 정해놓은 스타일이 고려되어 웹브라우저에 내용이 표시가 됩니다.

그렇다면, "웹문서 제작자 스타일", "사용자 스타일", "브라우저 기본 스타일" 이 세가지 중에서는 어떤 것이 우선되는 걸까요?

가장 중요한 것은 사용자 스타일입니다. 그리고 두번째가 제작자 스타일, 마지막으로 브라우저 기본 스타일 순입니다.
<br>
<br>

**참고**
<hr>
- HTML+CSS+자바스크립트 웹표준의 정석(고경희 저)
- [https://uxkm.io/publishing/css/01-cssStart/04-css_cascading#gsc.tab=0](https://uxkm.io/publishing/css/01-cssStart/04-css_cascading#gsc.tab=0){:target="\_blank"}