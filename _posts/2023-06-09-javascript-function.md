---
layout: post
title: "[JavaScript] 함수 선언식 vs 함수 표현식"
date: 2023-06-09 19:31:29 +0900
category: JavaScript
---

모양만 다르고 취향대로 쓰는 것 아닐까..? 라고 생각했지만, 자바스크립트 강의를 듣다가 차이가 있어 정리해보았습니다.

`선언식`은 특정코드보다 나중에 선언이 되어 있더라도, 코드 실행 전에 정의가 됩니다. 자바스크립트 언어가 선언된 함수들을 모은 다음, 함수를 정의한 후에 코드를 실행하기 때문입니다.

`표현식`은 특정변수로 받는 것이기 때문에, 표현식이 정의된 시점 이후부터 해당함수에 접근이 가능합니다.<br /><br />

> 함수 선언식

```javascript
function 함수이름(매개변수) {
  //코드
}
```

<br />
> 함수 표현식

```javascript
const 함수이름 = function (매개변수) {
  //코드
};
```

아래 코드의 경우, funcA는 함수 선언식으로, funcB는 함수 표현식, funcC는 화살표함수로 사용하여 테스트 해보았습니다.
funcA의 경우, 함수 정의 이전에 호출 할 때, 잘 작동하는 것으로 나옵니다. 하지만, funcB와 funcC의 경우에는 함수정의 이전에 맨위에서 호출했을 때
`ReferenceError: funcB is not defined` 이러한 에러를 만나게 됩니다.

따라서 <span style="color: dodgerblue">**함수표현식과 화살표함수는 정의한 이후에 접근할 수 있음**</span>을 확인할 수 있습니다.

```javascript
funcA();
//funcB ();
//funcC ();

function funcA() {
  //정의
  console.log("funciton A");
}

const funcB = function () {
  console.log("function B");
};

const funcC = () => {
  console.log("function C");
};

funcB();
funcC();
```
