---
layout: post
title: "[JavaScript] 직접 Carousel 만들기"
date: 2023-06-18 19:31:29 +0900
category: JavaScript
---

캐러셀은 기존하는 수많은 라이브러리들이 있지만, 오늘은 작동방식을 공부해보기 위해 직접 캐러셀을 구현해보려 합니다.

아래 코드는 HTML, CSS, JavaScript를 사용하여 Carousel을 구현해본 예시입니다.

JavaScript 코드에서 carousel 함수는 Carousel을 초기화하는 역할을 합니다.
carousel 함수 내부에서는 필요한 변수들을 설정하고, 초기 위치를 설정합니다.
prev 함수는 이전 버튼을 클릭했을 때 호출되는 함수로, 현재 인덱스를 업데이트하고 Carousel을 왼쪽으로 이동시킵니다.
next 함수는 다음 버튼을 클릭했을 때 호출되는 함수로, 현재 인덱스를 업데이트하고 Carousel을 오른쪽으로 이동시킵니다.
이전 버튼과 다음 버튼에 대한 클릭 이벤트 리스너를 추가하여 해당 버튼이 클릭되면 prev 또는 next 함수가 호출되도록 합니다.
DOMContentLoaded 이벤트 리스너를 사용하여 페이지가 로드되면 carousel 함수를 호출하여 Carousel을 초기화합니다.

```javascript
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>carousel 구현하기</title>
    <style>
      .carousel {
        width: 720px;
        overflow: hidden;
        position: relative;
      }
      .carousel ul {
        list-style-type: none;
        width: 100%;
        margin: 0;
        padding: 0;
        display: flex;
        transition: transform 0.5s ease;
      }
      .carousel li {
        flex: 0 0 100%;
        width: 100%;
      }
      .carousel-buttons {
        display: flex;
        justify-content: center;
        margin-top: 10px;
      }
      .carousel-buttons button {
        background-color: #ddd;
        color: #333;
        padding: 8px 16px;
        border: none;
        cursor: pointer;
        width: 100px;
        height: 30px;
        z-index: 999;
        margin-left: 10px;
      }
    </style>
  </head>
  <body>
    <div class="carousel">
      <ul>
        <li>
          <img src="https://via.placeholder.com/728x90.png" alt="Image 1" />
        </li>
        <li>
          <img src="https://via.placeholder.com/728x90.png" alt="Image 2" />
        </li>
        <li>
          <img src="https://via.placeholder.com/728x90.png" alt="Image 3" />
        </li>
      </ul>
      <div class="carousel-buttons">
        <button class="prev-button">Prev</button>
        <button class="next-button">Next</button>
      </div>
    </div>

    <script>
      function carousel() {
        const carouselContainer = document.querySelector(".carousel");
        const carouselList = carouselContainer.querySelector("ul");
        const carouselItems = carouselList.querySelectorAll("li");
        const carouselWidth = carouselContainer.offsetWidth;
        const totalItems = carouselItems.length;
        let currentIndex = 0;

        // 초기 위치 설정
        carouselList.style.transform = `translateX(-${
          currentIndex * carouselWidth
        }px)`;

        // 이전 버튼 클릭 시
        function prev() {
          currentIndex = (currentIndex - 1 + totalItems) % totalItems;
          carouselList.style.transform = `translateX(-${
            currentIndex * carouselWidth
          }px)`;
        }

        // 다음 버튼 클릭 시
        function next() {
          currentIndex = (currentIndex + 1) % totalItems;
          carouselList.style.transform = `translateX(-${
            currentIndex * carouselWidth
          }px)`;
        }

        // 이전/다음 버튼 이벤트 리스너 추가
        const prevButton = carouselContainer.querySelector(".prev-button");
        prevButton.addEventListener("click", prev);

        const nextButton = carouselContainer.querySelector(".next-button");
        nextButton.addEventListener("click", next);
      }

      // DOM이 로드된 후에 Carousel을 초기화합니다.
      window.addEventListener("DOMContentLoaded", carousel);
    </script>
  </body>
</html>

```
