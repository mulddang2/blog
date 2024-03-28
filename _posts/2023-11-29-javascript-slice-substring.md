---
layout: post
title: "[JavaScript] String의 slice vs substring"
date: 2023-11-29 19:31:29 +0900
category: JavaScript
---

[](https://velog.velcdn.com/images/js4072751/post/2c42ee19-1520-49b4-8fd8-53cbfd8a51e5/image.jpg)

문자열 문제를 풀 때, 햇갈리는 메서드 두개가 있어 정리해보고자 합니다.

### 사용법

```
str.substring(indexStart[, indexEnd 앞])
str.slice(beginIndex[, endIndex 앞])
```

### 공통점

- 문자열 원본은 그대로 보존
- 리턴값은 잘라진 문자열
- end 값 생략 가능
- start와 end에 같은 수를 넣을 경우, 빈문자열 리턴

### 차이점

1. start 값이 End 값 보다 클 때, 다른 결과값 (<span style="color: gray">**slice**</span>: "", <span style="color: hotpink">**substring**: "110W0"</span>)

```javascript
const str = "He110W0r1d";
console.log(str.substring(7, 2)); // output: "110W0"
console.log(str.slice(7, 2)); // output: ""
```

- substring: , start값이 End값보다 크다면 작은 숫자가 시작위치, 큰숫자가 종료위치로 셋팅된다.
  ex. str.substring(7,2) --> str.substring(2,7) 로 자동변경 된다는 의미

2. start, end에 음수인 값을 전달할 경우: (<span style="color: gray">**slice**</span>: "", <span style="color: hotpink">**substring**: "He"</span>)

```javascript
const str = "He110W0r1d";
console.log(str.substring(-7, 2)); //  output: "He"
console.log(str.substring(2, -5)); // output: "He"
console.log(str.slice(-7, 2)); // output: ""
console.log(str.slice(2, -5)); // output: "110"
```

- substring: start, end 상관없이 한개라도 음수면, 시작위치가 0으로 설정된다.
- slice: end 값이 음수일 때, 뒤에서 부터 세서 그 앞까지 센다.
- slice: start 값이 음수일 때, ""

### 효율성

- string.slice()의 시간 복잡도: O(1)
- string.substring()의 시간 복잡도: O(1)

### 결론

- 효율성에 차이가 없고, substring의 경우, 자동변경되는 경우(시작인덱스가 음수일 때, 0번 인덱스부터 셋팅됨 등)가 있어 햇갈릴 수 있어 **slice 사용하는 것이 더 좋을 듯합니다.**

### 활용

문자열 my_string과 정수 n이 매개변수로 주어질 때, my_string의 뒤의 n글자로 이루어진 문자열을 return 하는 solution 함수를 작성해 주세요.

- 뒤에서부터 인덱스를 세는 slice 메서드 활용하여 문제 풀이
- 나의 코드

```javascript
function solution(my_string, n) {
  return my_string.slice(-n);
}
```
