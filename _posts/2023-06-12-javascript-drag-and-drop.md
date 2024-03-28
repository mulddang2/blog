---
layout: post
title: "[JavaScript] 드래그 앤 드롭 기능 구현하기"
date: 2023-06-12 19:31:29 +0900
category: JavaScript
---

![drag and drop image](https://velog.velcdn.com/images/js4072751/post/4bbf6c36-8f35-49a6-ad5a-623b20b3d0e5/image.png) <br />

드래그(Drag)와 드롭(Drop) 기능을 구현하기 위해서는 다음과 같은 기능이 필요합니다.

1. `Drag 이벤트` : 객체를 드래그할 때 발생하는 이벤트입니다. 객체를 선택하고 드래그하는 동안 마우스 커서의 위치를 계속 추적해야 합니다. 이를 위해 dragstart, drag, dragend와 같은 이벤트를 사용할 수 있습니다.

2. `데이터 전달` : 드래그된 객체를 드롭 영역으로 전달하기 위해 데이터를 설정해야 합니다. 이를 위해 setData 메서드를 사용하여 드래그 시작 시 데이터를 설정하고, 드롭 시 getData 메서드를 사용하여 해당 데이터를 가져옵니다. 일반적으로는 객체의 ID나 다른 식별자를 데이터로 설정합니다.

3. `Dragover 이벤트` : 드롭 영역 위에서 드래그 중인 객체가 지원되는 드롭을 허용하기 위해 발생하는 이벤트입니다. 드롭 영역 위에서 드래그 중인 객체를 허용하려면 이 이벤트를 처리하여 기본 동작을 취소해야 합니다.

4. `Drop 이벤트` : 드롭 영역에 객체를 드롭할 때 발생하는 이벤트입니다. 드롭 영역에 객체를 추가하고 이동시키는 등의 작업을 수행해야 합니다. 이때 드롭 이벤트를 처리하여 필요한 작업을 수행할 수 있습니다.

이 외에도 객체의 위치 업데이트, 드래그 중인 객체의 스타일 변경, 다중 객체 선택 및 드롭 처리, 드롭 영역의 영역 체크 등 추가적인 기능을 구현할 수 있습니다.

구현한 코드는 다음과 같습니다.

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>drag & drop</title>
    <style>
      #draggable {
        width: 100px;
        height: 100px;
        background-color: #f44336;
        color: #fff;
        text-align: center;
        line-height: 100px;
        cursor: move;
      }

      #dropzone {
        width: 200px;
        height: 200px;
        background-color: #e0e0e0;
        margin-top: 20px;
      }
    </style>
  </head>

  <body>
    <div id="draggable" draggable="true" ondragstart="dragStart(event)">
      이동할 객체
    </div>
    <div id="dropzone" ondragover="dragOver(event)" ondrop="drop(event)">
      드롭 영역
    </div>

    <script>
      // 드래그 시작 시 이벤트 핸들러
      function dragStart(event) {
        event.dataTransfer.setData("text/plain", event.target.id);
      }

      // 드래그 영역에 드롭을 허용하기 위한 이벤트 핸들러
      function dragOver(event) {
        event.preventDefault();
      }

      // 드롭 시 이벤트 핸들러
      function drop(event) {
        event.preventDefault();
        const data = event.dataTransfer.getData("text/plain");
        const draggableElement = document.getElementById(data);
        event.target.appendChild(draggableElement);
      }
    </script>
  </body>
</html>
```
