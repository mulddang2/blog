---
layout: post
title: "[SCSS] @at-root?"
date: 2022-12-21 19:31:29 +0900
category: SCSS
---

중첩을 사용하고 있다가 중첩을 벗어나고 싶을 때 <u>@at-root 를 사용한다.</u>

```css
.frame {
  padding: 20px;
  border: 1px solid #000;
  text-align: center;

  @at-root .heading {
    color: palevioletred;
    font-size: 36px;
    font-weight: normal;
  }
}
```

컴파일 결과----------------------------------------------------

```css
.frame {
  padding: 20px;
  border: 1px solid #000;
  text-align: center;
}
.heading {
  color: palevioletred;
  font-size: 36px;
  font-weight: normal;
}
```
