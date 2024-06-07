---
layout: post
title: "[Algorithm] 배열 n개씩 나누기"
date: 2024-01-18 19:20:23 +0900
category: Algorithm
---

### 1. 배열을 n개씩 나눌 때, 핵심:

- for문 증감식에서 i를 n만큼 증가하는 것이다.
- temp 변수를 둬서 slice 해서 활용하면 된다.

### 2. 문제활용: 프로그래머스 문제 '5명씩'

아래 알고리즘 문제 코드는 5명씩 묶고, 첫번째 이름을 출력하는 문제의 코드이다.

```javascript
function solution(names) {
  var answer = [];

  for (let i = 0; i < names.length; i += 5) {
    let temp;
    temp = names.slice(i, i + 5);
    answer.push(temp[0]);
  }

  return answer;
}
```
