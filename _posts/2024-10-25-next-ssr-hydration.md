---
layout: post
title: "[Next.js] 왜? Next.js사용하고 hydration은 무엇?"
date: 2024-10-25 19:09:29 +0900
category: Next.js
tag: [코드잇스프린트, 스프린트OON기, 취업까지달린다]
---

### ❗❔ 리액트만 사용할 때와 비교해 Next.js를 사용하는 이유
React는 사용자와 상호작용 가능한 대화형 UI(ex. 버튼 클릭 시, 모션 동작 등) 구축을 위한 JavaScript 라이브러리 입니다.

라이브러리란 React가 UI를 구축하는 데 유용한 함수(API)를 제공하지만, 해당 함수를 애플리케이션에서 어디에서 사용할지는 개발자에게 맡긴다는 것을 의미합니다. 그래서 React에서는 웹을 개발하는 과정에서 렌더링 할 때는 어떤 도구를 쓰고, 데이터를 가져올 때는 어떤 도구를 쓰는 등에 대해 표준화 하지 않고 자유롭게 개발자들이 원하는대로 사용할 수 있게 했습니다.

그렇기 때문에 어떤 도구를 선택할지 고민해야합니다. 일반적으로 필요한 것들을 알아서 셋팅 해주고 알아서 최적화 해주면 좋겠는데 말입니다.

<br>

그래서 Next.js와 같은 타사 툴들의 생태계가 형성된 것이라 합니다.

`Next.js`는 **빠르고 풀스택 웹 애플리케이션을 만드는 데 필요한 기본 요소를 제공하는 유연한 React 프레임워크**입니다.

<br>

Next.js를 사용하여 개발할 때의 이점은 다음과 같이 정리해볼 수 있었습니다.

<br>

**1. Next.js에서 일반적인 애플리케이션 요구 사항(라우팅, 데이터 페치, 캐싱)을 제공해줍니다.**

> 그래서 이것저것 다른 라이브러리 설치할 필요 없이 쉽게 해결할 수 있습니다. 동시에 개발자와 최종 사용자 경험도 개선할 수 있습니다.

**2. 서버 측 렌더링(SSR)을 통한 향상된 애플리케이션 성능향상**

> 서버에서 초기 HTML을 렌더링하여 첫 번째 페이지 로드 시간을 줄입니다. 그래서 초기로딩에 있어 빠른 로딩 경험을 사용자에게 제공할 수 있습니다.

**3. 최적화된 이미지 로딩 (`<Image />` 컴포넌트 제공)**
<br>

**4. 자동 코드 분할로 초기 로드 시간 단축**
<br>
> 자동 코드 분할은 해당 특정 페이지에 필요한 코드만 로드하여 초기 로드 시간을 향상시킵니다.

**5. 캐싱을 통한 애플리케이션 성능 개선**
<br>
> - Data Cache: Next.js는 특정 요청이든 전체 경로 세그먼트이든 데이터 캐싱을 위한 기본 제공 지원을 제공합니다. Next.js는 자동으로 캐시하고 중복을 제거합니다.
> - Router Cache: React Server Component가 로드되면 Router Cache라고 알려진 캐시 내의 메모리에 데이터를 보관합니다. 이 캐시는 개별 경로 세그먼트로 나뉘며 이전에 방문한 경로를 추적하고 향후 경로를 미리 페치하여 탐색 경험을 향상시키는 데 사용됩니다.
> - Full Route Cache: Next.js는 탐색 시 서버 요청을 줄이고 성능을 향상시키기 위해 HTML과 React Server Component(RSC) 페이로드를 서버에 저장하는 캐싱 메커니즘인 Full Route Cache를 구현합니다.

**6. 전체 사이트를 다시 생성하지 않고도 구축 프로세스 중에 동적 콘텐츠를 수정할 수 있도록 하여 정적사이트 생성(SSG)를 향상**
  
> 이를 ISG(Incremental Static Generation)라고 하는데, SSG(정적 사이트 생성)와 SSR(서버에서 렌더링)기능을 결합한 하이브리드 시스템입니다.

**7. Next.js는 개발, 서버 측, 클라이언트 측 오류를 처리할 수 있는 포괄적인 오류 처리 메커니즘을 제공합니다.**

**8. 개발 환경에서, 빠른 새로 고침으로 즉각적으로 개발자 피드백 제공**

**9. 내장된 SEO 지원**

**10. Next.js Speed ​​Insights: 사전 구축된 분석 기능으로 웹페이지 성능 측정 기능 제공**
> Next.js Speed ​​Insights라는 사전 구축된 분석 기능이 포함되어 있어 다양한 메트릭을 통해 웹 페이지의 성능을 평가하고 측정할 수 있습니다.
Vercel 배포에서 추가 설정 없이 Real Experience Score를 수집할 수 있습니다.

---
### ❗❔ Next.js에서 SSR을 실행하는 과정, hydration
1. 페이지에서 서버 측 렌더링을 사용하면 각 요청마다 페이지 HTML이 생성됩니다.
2. 페이지에 서버 측 렌더링을 사용하려면 `getServerSideProps`라는 비동기 함수를 내보내야 합니다. 이 함수는 모든 요청에서 서버에서 호출됩니다.

      > getServerSideProps는 getStaticProps와 비슷하지만, 차이점은 `getServerSideProps`는 빌드 시점이 아니라 모든 요청에서 실행되며, 필요한 데이터를 패칭해서 페이지의 prop으로 전달합니다.

3. 클라이언트에서 React 하이드레이션: 클라이언트 측 JavaScript가 이 정적 콘텐츠를 "hydration"하여 상호 작용성을 부여하여 완벽하게 기능하는 React 애플리케이션을 형성합니다.

#### hydration 이란?

프리렌더링된 서버 측 콘텐츠를 클라이언트 측의 인터렉티브 UI로 변환하는 프로세스입니다.

- 사용자가 사전 렌더링된 페이지에 액세스하면 Next.js는 완전히 렌더링된 HTML 콘텐츠를 서버의 초기 데이터와 UI와 함께 클라이언트의 브라우저로 즉시 전송합니다.

- 클라이언트 측 JavaScript가 이 정적 콘텐츠를 "hydration"하여 대화형 기능을 부여하여 완전히 기능적인 React 애플리케이션을 형성합니다.

#### 기존 React의 CSR방식과 비교:
  브라우저가 빈 HTML 페이지를 검색한 다음 렌더링 및 데이터 수집을 위해 JavaScript 번들을 가져오는 기존의 클라이언트 측 렌더링(CSR) React 앱과 달리 
  **Next.js의 hydration 프로세스는 초기 로딩 지연을 크게 완화합니다**
  


<br>
<br>

**참고**
<hr>
- Next.js 공식문서: [https://nextjs.org/learn/react-foundations/what-is-react-and-nextjs](https://nextjs.org/learn/react-foundations/what-is-react-and-nextjs){:target="\_blank"}
- [https://cult.honeypot.io/reads/top-nextjs-performance-benefits/](https://cult.honeypot.io/reads/top-nextjs-performance-benefits/){:target="\_blank"}