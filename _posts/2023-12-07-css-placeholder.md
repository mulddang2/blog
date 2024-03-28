---
layout: post
title: "[CSS] placeholder가 보이지 않을 때, CSS로 해결하기"
date: 2023-12-07 19:31:29 +0900
category: CSS
---

굳이 js를 사용하지 않고, css 차원에서 미리 해결할 수 있는 것은 css로 해결하자!

<code>placeholder-shown</code> : `<input>` 또는 `<text-area>` 요소에서 placeholder가 보여질 때를 의미한다.

여기에 :not을 붙였으니, 이렇게 하면,
보이지 않을 때의 스타일을 js를 사용하지 않고도 스타일 적용할 수 있게 된다.
![](https://velog.velcdn.com/images/js4072751/post/8c20db8e-cc3f-4b82-9252-9f4a6ced9884/image.png)
