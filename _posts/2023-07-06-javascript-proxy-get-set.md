---
layout: post
title: "[JavaScript] Proxy를 활용한 객체의 Set과 Get"
date: 2023-07-06 19:31:29 +0900
category: JavaScript
---

Proxy는 JavaScript에서 객체에 접근하고 이를 제어하는 기능을 제공합니다.

Proxy를 사용하여 객체의 Set과 Get 동작을 수정하는 방법과 그 장점에 대해 살펴보도록 하겠습니다..!

## 1. 객체에 대해서 Proxy를 생성하여 Set, Get 하는 방법

Proxy를 사용하여 객체의 Set과 Get 동작을 수정하려면, Proxy 객체를 생성하고 그 안에 handler를 정의해야 합니다. Proxy 생성자는 두 가지 인자를 받습니다. 첫 번째 인자는 대상 객체(target)이고, 두 번째 인자는 handler 객체입니다. handler 객체에는 객체에 접근하는 동작에 대한 특정 동작들을 정의할 수 있습니다.

아래는 Proxy를 사용하여 객체의 Set과 Get 동작을 수정하는 간단한 예시입니다.

```javascript
const target = {
  name: "John",
  age: 30,
};

const handler = {
  get: function (target, property) {
    console.log("Getting " + property);
    return target[property];
  },
  set: function (target, property, value) {
    console.log("Setting " + property + " to " + value);
    target[property] = value;
  },
};

const proxy = new Proxy(target, handler);

console.log(proxy.name); // Getting name, John
proxy.age = 40; // Setting age to 40
```

## 2. 객체에 대해서 Proxy를 생성해서 객체를 Set, Get 하는 방법의 장점

Proxy를 사용하여 객체의 Set과 Get 동작을 수정하는 방법에는 몇 가지 장점이 있습니다.

a. `데이터 유효성 검사` : Proxy를 사용하면 객체에 할당되는 값에 대한 유효성을 검사할 수 있습니다. 예를 들어, 숫자형 속성에만 값을 할당하도록 제한하거나, 문자열 속성의 길이를 제한하는 등의 작업을 수행할 수 있습니다.

b. `디버깅 및 로깅` : Proxy를 통해 객체에 접근하는 동작을 가로채고 이를 기록하거나 디버깅 정보를 추가할 수 있습니다. 예를 들어, 객체에 접근하는 동작이 언제 발생하는지 기록하거나 특정 속성의 변경을 추적할 수 있습니다.

c. `은닉화` : Proxy를 사용하여 객체의 일부 속성을 외부로부터 숨길 수 있습니다. 특정 속성에 대한 접근을 제한하거나 가상 속성을 도입하여 객체의 은닉성을 강화할 수 있습니다.

d. `동작 수정` : Proxy를 사용하면 객체의 동작을 수정하고 확장할 수 있습니다. 예를 들어, 객체에 접근하는 동작을 수정하여 캐시 기능을 추가하거나 비동기적인 동
