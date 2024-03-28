---
layout: post
title: "[CSS] CSS 관련 개념들 공부"
date: 2023-03-15 19:31:29 +0900
category: CSS
---

# css는 무엇인가?

Cascading Style Sheets의 약자

- Inline Style Sheet : 우선순위가 2번째
- Internal Style Sheet : 스타일 태그 안에 사용
- Linking Style Sheet : css 파일을 외부에서 불러옴

## 📕 개념 및 문법

```css
a {
  background-color: yellow;
  font-size: 16px;
}
```

- a : 선택자
- background-color, font-size : 속성명
- yellow, 16px : 속성값
- (;세미콜론) : 선언 구분자, 선언 끝

## 📗 class, id 개념

id: 우선 순위가 3번째,
class: 우선 순위가 4번째

## 📕 properties

속성을 html에서는 attribute, css에서는 property 라고 함.

### 💡 property value 단위

- 크기의 단위:

1. px
2. %
3. vw(뷰포트 너비), vh(뷰포트 높이)
   height: 100vh를 쓰면 안되는 경우, 모바일일 때, 주소창을 포함한 크기가 vh로 잡힘
4. em & rem
   > em: 부모 크기 기준
   > rem: 최상단 크기 기준

- 색상의 단위
  rgb, HEX

## 📗 안보이도록 하는 속성들 3가지 차이

- display: none;

  > 공간 차지 X
  > 이벤트 적용 X
  > 탭 눌렀을 때 focus X

- visibility: hidden;

  > 공간 차지 O
  > 이벤트 적용 X
  > 탭 눌렀을 때 focus X

- opacity: 0;

  > 공간 차지 O
  > 이벤트 적용 X
  > 탭 눌렀을 때 O

## 📕 display 속성들 차이

- display: block

  > 한줄 공간을 모두 차지한다, 너비 높이 가질 수 있다.
  > 줄바꿈 처리가 자동으로 된다.

- display: inline

  > 한줄 배치되고, 너비 높이값을 가질 수 없다.
  > 글자나 문장에서 특정 단어만 효과를 준다.

- display: inline-block

  > 한줄 배치되면서(inline 속성), 너비 높이값 가질 수 있다(block 속성).

## 📗 position 속성

- position: absolute

  > 부모 중에서 position: static이 아닌 부모를 찾아 그 부모를 기준으로 움직임. 아무도 없으면, 뷰포트 기준으로 움직임.

- position: relative

  > 본인이 움직임

- position: fixed

  > 항상 페이지의 같은 위치에 있어야 할 때 사용함, 스크롤 위치와 상관없이 꼭 그자리에 있어야할 경우에 사용

- position: sticky

  > 구체적으로 보기에 스크롤하고 특정 지점에 도달하면 중지하려는 항목이 있을 때 사용함
