---
layout: post
title: "[JavaScript] Template Literal(리터럴)이란"
date: 2023-05-03 19:31:29 +0900
category: JavaScript
---

Template literal 이란 문자열(String)을 표현하는 ES6문법입니다.

템플릿 리터럴을 사용하면 문자열 안에 JavaScript 표현식을 간편하게 포함할 수 있습니다.
템플릿 리터럴은 백틱 **( \` )** 을 사용하여 작성가능 합니다.

>

```javascript
console.log(`템플릿 리터럴 
사용하기`);
```

템플릿 리터럴에는 세 가지 기능이 있습니다.

- Multi-line strings
- Interpolation
- Tagged template literal

---

### Multi-line strings

ES6 이전에는 문자열을 줄바꿈할 필요가 있을 때, 이렇게 작성하였습니다.

>

```javascript
console.log(
  "템플릿 리터럴 \n" +
    "사용하기" +
    "\n이렇게" +
    "\n번거롭게 줄바꿈" +
    "할수도 " +
    "\n있습니다."
);
```

템플릿 리터럴
사용하기
이렇게
번거롭게 줄바꿈할수도
있습니다.

하지만 이렇게 백틱을 사용하여 템플릿 리터럴을 사용하면 소스에 삽입된 다음줄의 글자, 탭, 공백 등이 문자열의 일부가 됩니다.
가독성 측면에서, 확실히 좋아보입니다.

>

```javascript
console.log(`템플릿 리터럴
사용하기
이렇게
손쉽게 줄바꿈할수도 
있습니다.`);
```

템플릿 리터럴
사용하기
이렇게
"손쉽게" 줄바꿈할수도
있습니다.

또 다른 예시,

>

```javascript
console.log(`안녕하세요.
지난번 공유주신 1분기 실적보고서는 잘 받았습니다.`);
```

안녕하세요.
지난번 공유주신 1분기 실적보고서는 잘 받았습니다.

---

### Interpolation

한국어로 문자열 '보간'이라고 합니다.  
템플릿 리터럴(백틱 \` 으로 묶인 문자열)과 ${expression}을 함께 사용할 수 있습니다.

\*\*템플릿 리터럴의 장점은 이렇게 문자열에 변수값을 쉽게 삽입할 수 있다는 것입니다. `${expression}` 내의 표현식은 런타임 중에 평가되며 결과는 문자열에 삽입됩니다.
`${expression}` 내부의 표현식은 값으로 평가되는 모든 것이 될 수 있습니다(하지만 보통 문자열 사용).

>

```javascript
const currentYear = 2023;
const message = `지금은 ${currentYear}년 입니다.`;
console.log(message);
```

지금은 2023년 입니다.

---

### Tagged template literal

함수를 호출 할 때, argument를 템플릿 리터럴 형식으로 사용하는 방식입니다.
첫 번째 인수는 문자열 값의 배열입니다. 추가 argument는 만나는 순서대로 변수가 됩니다.

>

```javascript
let yourName = "Suzy";
let age = 4;
function welcome(arr, nameArg, ageArg) {
  console.log(arr[0]);
  console.log(arr[1]);
  console.log(arr[2]);
  console.log(nameArg);
  console.log(ageArg);
  console.log(arr[0] + nameArg + arr[1] + ageArg + arr[2]);
}
welcome`벌써, ${yourName}은(는) ${age}살이야?`;
```

```javascript
console.log(arr[0]) = 벌써,
console.log(arr[1]) = 은(는)
console.log(arr[2]) = 살이야?
console.log(nameArg) = Suzy
console.log(ageArg) = 4
벌써, Suzy은(는) 4살이야?
```

템플릿리터럴에서 함수 파라미터로 전달한 첫번째 인자(arr)에는 템플릿 리터럴에서 작성한 글자들(벌써, 은(는), 살이야?)가 배열 순서대로 출력되는 것을 확인할 수 있습니다.
그리고, 템플릿 리터럴에서 입력한 변수 ${yourName}, ${age}가 welcome 함수의 2번쨰 파라미터, 3번째파라미터로 각각 들어가서 출력됩니다.
<br />
<br />

> **맺으며..**<br />
> Tagged template literal 는 Styled Component 작성시, 유용하게 사용될 수 있습니다. 스타일 컴포넌트는 추후 작성해보며 이와 관련해 포스팅 해보도록 하겠습니다.

<br />
<br />

**참고자료**

<hr />
- [https://dmitripavlutin.com/javascript-template-strings/](https://dmitripavlutin.com/javascript-template-strings/){:target="\_blank"}
- [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#tagged_templates](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#tagged_templates){:target="\_blank"}
- [https://codeburst.io/javascript-template-literals-tag-functions-for-beginners-758a041160e1](https://codeburst.io/javascript-template-literals-tag-functions-for-beginners-758a041160e1){:target="\_blank"}
- [https://betterprogramming.pub/replace-string-concatenation-using-template-literals-in-javascript-fbdfd5e83bbe](https://betterprogramming.pub/replace-string-concatenation-using-template-literals-in-javascript-fbdfd5e83bbe){:target="\_blank"}
