---
layout: post
title: "[React] 이벤트 핸들러.."
date: 2024-01-25 19:31:29 +0900
category: React
---

### 1. 이벤트 핸들러는 컴포넌트 내부에 선언하기

( + 상위에서 prop 받아서 prop에 접근가능 )<br />
이벤트는 Toolbar가 아니라, AlertButton 컴포넌트 안에서 사용한다.
이벤트 재료인 메세지 내용을 상위(Toolbar)에서 받아서 아래와 같이 사용하면 된다.

```javascript
function AlertButton({ message, children }) {
  return (
    <button onClick={() => alert(message)}>
      {children}
    </button>
  );
}

export default function Toolbar() {
  return (
    <div>
      <AlertButton message="Playing!">
        Play Movie
      </AlertButton>
      <AlertButton message="Uploading!">
        Upload Image
      </AlertButton>
    </div>
  );
}
```

### 2. 전파방지

부모인 div 에도 이벤트가 있고, 자식인 button 에도 각각 이벤트 핸들러가 있다면 어떻게 될까..

1. 버튼 클릭이벤트 실행 <br />
2. 부모 클릭이벤트 실행

<span style="color: #8A0829">**답은 1, 2번 순서대로 실행된다.**</span> 즉, alert 창이 2개 뜬다. <br />
!codesandbox[qqwck7?view=Editor+%2B+Preview&module=%2Fsrc%2FApp.js]

이 문제해결을 위해, 왼쪽 버튼에만 <span style="color: #8A0829">**e.stopPropagation**</span> 을 추가해주었다.
아래와 같이 play Movie 버튼에서는 alert이 1번만 뜬다. <br />
!codesandbox[6s7rct?view=Editor+%2B+Preview&module=%2Fsrc%2FApp.js]

### 3. `e.stopPropagation` vs `e.preventDefault`

e.stopPropagation ? - 부모로 이벤트 전파되는 현상을 막아준다.<br />
e.preventDefault ? - `<form>` 태그 내에서 버튼 클릭하면, 기본적으로 페이지 전체가 리로드 되는데 이런 기본 속성을 막아준다.

### 4. 이벤트 핸들러는 호출이 아니라 전달만 가능하다.

onClick={ handleClick( ) } ❌
onClick={ <span style="color: #8A0808">**handleClick**</span> } ⭕<br />
대신 이렇게는 가능하다.
onClick={ <span style="color: #8A0808">**( ) => handleClick( )**</span> } ⭕

> <span style="color: #F5A9A9 ">참고 자료: </span><a style="color: #F5A9A9 !important">
> https://ko.react.dev/learn/responding-to-events#adding-event-handlers</a>
