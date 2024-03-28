---
layout: post
title: "[COTE] 더 크게 합치기"
date: 2023-05-13 19:20:23 +0900
category: COTE
---

### 📖 들어가며

이제 자바스크립트 기초문법을 강의와 함께 `프로그래머스`에서 제공하는 `"코딩기초트레이닝"`을 3일전부터 꾸준히 해보고 있습니다. 앞으로도 코딩기초트레이닝 문제를 매일 풀어서, 배운문법들을 잘 활용하여 제 것으로 얼른 만들고싶어요..! 기초문제 다 풀고 높은 단계 레벨들도 술술 해결해나가는날을 오리라 기대합니다.

풀고나서, 다른 사람들의 풀이 참고해보는데 오늘 푼 문제 중 이 문제에서 유독 제 코드가 가장 긴 것 같아서, 이 문제를 남겨보려고 합니다.

![](https://velog.velcdn.com/images/js4072751/post/f4fc50bc-c8d0-49a5-b6f2-6197a3a22e6c/image.png)

### 🔒 문제

**문제 설명**

> 연산 ⊕는 두 정수에 대한 연산으로 두 정수를 붙여서 쓴 값을 반환합니다. 예를 들면 다음과 같습니다.<br>

- 12 ⊕ 3 = 123
- 3 ⊕ 12 = 312
  <br>양의 정수 a와 b가 주어졌을 때, a ⊕ b와 b ⊕ a 중 더 큰 값을 return 하는 solution 함수를 완성해 주세요.<br>
  단, a ⊕ b와 b ⊕ a가 같다면 a ⊕ b를 return 합니다.

**제한사항**

- 1 ≤ a, b < 10,000
  **입출력 예**
  ![](https://velog.velcdn.com/images/js4072751/post/1d441812-daee-4971-b5a8-3d963695149c/image.png)

**입출력 예 설명**<br />
입출력 예 #1

- a ⊕ b = 991 이고, b ⊕ a = 919 입니다. 둘 중 더 큰 값은 991 이므로 991을 return 합니다.

입출력 예 #2

- a ⊕ b = 898 이고, b ⊕ a = 889 입니다. 둘 중 더 큰 값은 898 이므로 898을 return 합니다.

### 🔑 나의 풀이

>

```javascript
function solution(a, b) {
  let result = 0;
  let abString = String(a) + String(b);
  let baString = String(b) + String(a);
  let abNum = Number(abString);
  let baNum = Number(baString);
  if (abNum >= baNum) {
    result = abNum;
  } else result = baNum;
  return result;
}
```

### 🔎 다른 사람 풀이

>

```javascript
function solution(a, b) {
  return Math.max(Number(`${a}${b}`), Number(`${b}${a}`));
}
```

### 🤓 깨달은 점

매개변수 a,b가 문자열로 더한 후, 숫자의 값으로써 비교하는 문제입니다.

String으로 우선 만들어야겠다.. 는 생각으로 저렇게 사용했는데,
다른 사람의 풀이를 보니, **백틱을 사용해서 문자열로 만들어** 불필요한 String 매서드의 반복을 피할 수 있구나.. 라는 것을 알 수 있었습니다.

또한,** Math.max 매서드를 사용**하면, if else 문을 사용하지 않고 간단하게 크기 비교 할 수 있다는 것도 알게 되었습니다.
