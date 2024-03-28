---
layout: post
title: "[Setting] VS Code - 코드 스니펫 만들기"
date: 2023-12-21 19:31:29 +0900
category: Setting
---

![banner](https://velog.velcdn.com/images/js4072751/post/9e140118-5944-47bc-9326-42a5a77ba893/image.jpg)  
저처럼 반복코드를 적는게 귀찮은데, 확장까지 설치하기엔 과하다싶을 때, 유용한 듯 합니다.

## VS Code Snippet(코드조각) 만들기

코드 작성 시, 반복 코드 작업 개선을 위해 코드 스니펫(코드 조각) 셋팅을 해보고자 합니다.

### 1. 코드 조각 생성

**파일 > 기본 설정 > 사용자 코드 조각 구성** (단축키: Ctrl + Shift + P)

![](https://velog.velcdn.com/images/js4072751/post/0f428411-22ee-4162-bf0a-f4b2328867d2/image.png)

### 2. 최초 등록 시, 파일명: javascriptreact.json 로 설정

(추가 시, 기존 javascriptreact.json 파일 내 추가)

### 3. 포멧 작성하기

- prefix: 만든 코드조각을 소환할 단어
- [body 안에 포멧 작성 시, 유용한 곳 ](https://snippet-generator.app/?description=&tabtrigger=&snippet=const+Temp+%3D+%28%29+%3D%3E+%7B%0A++return+%28%0A++%3C%3E%3C%2F%3E%0A++%29%0A%7D%0A%0Aexport+default+Temp%3B&mode=vscode){:target="\_blank"}

### 4. 내가 만든 코드 스니펫

import react 부분은 최상단에서만 대부분 사용하는 것 같아 일부러 우선 적지 않음

```json
{
  "CreateReactComponents": {
    "scope": "javascript, typescript",
    "prefix": "rc",
    "body": [
      "const ${1:${TM_FILENAME_BASE}} = () => {",
      "  return (",
      "    <>",
      "      ${2:}",
      "    </>",
      "  );",
      "};",
      "",
      "export default ${1:${TM_FILENAME_BASE}};"
    ],
    "description": "CreateReactComponents"
  },

  "FunctioneReactComponents": {
    "scope": "javascript, typescript",
    "prefix": "frc",
    "body": [
      "function ${1:${TM_FILENAME_BASE}} () {",
      "  return (",
      "    <>${2:}</>",
      "  )",
      "}",
      "",
      "export default ${1:${TM_FILENAME_BASE}}"
    ],
    "description": "FunctioneReactComponents"
  }
}
```

### 5. 유용한 변수

- ${1:}은 코드 생성시 처음으로 커서 포커스가 가는 부분 --> $1을 동시에 설정했으니, 동시에 파일명 바꿀 수 있음
- TM_FILENAME_BASE: 확장자 빼고 현재 파일 문서명 따름
- ${2:} 는 탭 누르면 그다음으로 포커스가 가는 부분
  <br />
  <br />

**참고자료**

<hr />
VS Code :
[https://code.visualstudio.com/docs/editor/userdefinedsnippets#\_create-your-own-snippets](https://code.visualstudio.com/docs/editor/userdefinedsnippets#_create-your-own-snippets){:target="\_blank"} <br />
blog : [https://likejirak.tistory.com/143](https://likejirak.tistory.com/143){:target="\_blank"}
