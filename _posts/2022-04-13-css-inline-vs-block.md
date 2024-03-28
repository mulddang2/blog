---
layout: post
title: "[CSS] block vs inline"
date: 2022-04-13 19:31:29 +0900
category: CSS
---

# block

- 혼자 한줄 차지 = 너비가 100% 라는 것
- 대표태그 `<h1~h6>`, `<div>`, `<p>` 등

---

좀 더 자세한 내용 덧붙이자면, 'block' 요소는?

- 레이아웃 관련, 제목, 테이블 관련, 목록, sementic 태그들이 포함됨
- width, height 넣을 수 있음
- 상하좌우 margin도 넣을 수 있음

# inline

- 한줄 차지안함 = 콘텐츠만큼만 차지함
- 곧, 한줄에 여러개 붙을 수 있음
- 대표 태그 `<span>`, `<img>`, `<strong>` 등

---

좀 더 자세한 내용 덧붙이자면, 'inline' 요소는?

- '글자'를 <mark>개별적</mark>으로 꾸미는 서식 관련 태그들이 포함됨
- width, height 넣을 수 없음
- 상하좌우 margin도 넣을 수 없음

## 한줄 정리

> block은 덩치, inline은 약한 놈.
