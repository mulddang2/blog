---
layout: post
title: "[Tailwind CSS] 모르는 className 공부 및 활용"
date: 2024-04-03 19:16:29 +0900
category: Tailwind CSS
---

```
<요약>
max-w-pros는 max-width: 65ch;로 적용됩니다. 
이를 사용하면, 그 요소의 최대 너비가 65개의 문자 너비를 초과하지 않도록 설정됩니다. 이것은 특히 긴 텍스트 블록의 가독성을 높이기 위해 사용됩니다. 일반적으로 65자 정도의 너비는 읽기에 적절한 줄 길이로 간주됩니다.
```

```html
<p className="max-w-prose">max-w-prose</p>
```

`max-w-prose`는 Tailwind CSS에서 사용될 수 있는 CSS 스타일 속성으로, 요소의 최대 너비를 설정하는 데 사용됩니다. <br />
이 속성은 max-width: 65ch;로 적용됩니다.

여기서 65ch는 너비 값을 나타내며, ch 단위는 CSS에서 'character'의 약자로, 기본적으로 숫자 0의 너비를 기준으로 합니다.

ch 단위는 다음과 같은 경우에 유용합니다:

- 글꼴 크기와 관련된 요소의 너비를 설정할 때
- 가독성을 위해 텍스트 블록의 최대 너비를 제한할 때



