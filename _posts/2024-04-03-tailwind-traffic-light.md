---
layout: post
title: "[Tailwind CSS] 신호등 만들기 예제"
date: 2024-04-03 19:16:29 +0900
category: TailwindCSS
---
Tailwind를 프로젝트에 도입해보고자, 만들어본 예제입니다.

``` html
<section class="bg-neutral-600 flex flex-row justify-between items-center h-[300px] group">
  <div class="flex flex-row gap-3 group-hover:bg-pink-400">
    <div class="w-4 h-[150px] bg-white"></div>
    <div class="w-4 h-[150px] bg-white"></div>
    <div class="w-4 h-[150px] bg-white"></div>
    <div class="w-4 h-[150px] bg-white"></div>
    <div class="w-4 h-[150px] bg-white"></div>

  </div>
  <div class="flex flex-row justify-center items-center gap-4">
    <div class="w-[200px] h-[200px] bg-red-500 rounded-full border-4 border-black hover:bg-red-300 transition"></div>
    <div class="w-[200px] h-[200px] bg-yellow-500 rounded-full border-4 border-black hover:bg-yellow-300 transition"></div>
    <div class="w-[200px] h-[200px] bg-green-500 rounded-full border-4 border-black hover:bg-green-300 transition"></div>
  </div>
  <div class="flex flex-row gap-3 group-hover:bg-purple-400">
    <div class="w-4 h-[150px] bg-white"></div>
    <div class="w-4 h-[150px] bg-white"></div>
    <div class="w-4 h-[150px] bg-white"></div>
    <div class="w-4 h-[150px] bg-white"></div>
    <div class="w-4 h-[150px] bg-white"></div>
  </div>
</section>
```

결과 UI는 다음과 같습니다.
![신호등 예제 이미지](https://cdn.jsdelivr.net/gh/mulddang2/blog@main/public/img/traffic-light.png)





