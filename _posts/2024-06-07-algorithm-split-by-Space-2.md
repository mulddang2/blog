---
layout: post
title: "[Algorithm] 공백으로 구분하기 2"
date: 2024-06-07 14:00:23 +0900
category: Algorithm
---

### 📖 들어가며

배열 메서드 filter의 정의 "콜백 함수의 반환값이 true인 요소로만 구성된 새로운 배열을 반환한다"를 다시 새기고, 적용해보았습니다.

### 🔒 문제

단어가 공백 한 개 이상으로 구분되어 있는 문자열 my_string이 매개변수로 주어질 때, my_string에 나온 단어를 앞에서부터 순서대로 담은 문자열 배열을 return 하는 solution 함수를 작성해 주세요.

### 🔑 나의 풀이

```javascript
function solution(my_string) {
  let strArr = my_string.split(" ");
  let answer = strArr.filter((v) => v.length > 0);

  return answer;
}
```

### 🔎 다른 사람 풀이

```javascript
function solution(my_string) {
  return my_string.split(" ").filter((v) => v);
}
```

### 🤓 깨달은 점

제 코드에서 처럼 filter 메서드에 조건 v.length > 0 을 적지 않더라도, 공백제거가 가능합니다.
filter는 콜백함수의 반환값이 true인 요소로만 구성된 새로운 배열을 반환하기 때문입니다.

공백(빈문자열)은 false값으로 평가되는 Falsy값이기 때문에, 빈문자열을 제외한 나머지만 배열에 담을 수 있습니다.
