---
layout: post
title: "[Network] HTTP와 HTTPS의 차이점은 무엇일까요?"
date: 2023-06-01 19:31:29 +0900
category: Network
---
## HTTP와 HTTPS의 차이점
HTTP(Hypertext Transfer Protocol) 
- 개념: 클라이언트와 서버 간 통신을 위한 프로토콜
- 기본 프로토콜: HTTP/1과 HTTP/2는 TCP/IP를, HTTP/3은 QUIC를 사용함
- 포트: 80
- 보안: 추가 보안 기능 없음
 

HTTPS(Hypertext Transfer Protocol Secure)
- 개념: HTTP의 확장 버전으로 통신의 보안을 위해 고안된 프로토콜
- 프로토콜: SSL(TLS)와 HTTP/2를 사용함
- 포트: 443
- 보안: 퍼블릭 키 암호화에 SSL 인증서 사용

## 웹사이트 HTTPS 설정 방법
### 1. SSL(TLS) 인증서 구매
SSL 인증서 판매 기관에 매년 일정 금액을 지불하고 SSL 인증서를 구매해야 합니다.
SSL 인증서를 발급받으면 3개의 파일이 주어집니다. 각 파일은 기본 인증서가 포함된 `looker.pem`이라는 인증서 파일, 이름이 `looker.key`인 연결된 키 파일, 필요한 경우 `ca.pem`이라는 중간 인증 기관 (CA) 체인 파일을 제공합니다.이 파일들을 운영하는 서버 환경에 맞게 업로드하면 HTTPS 통신을 적용할 수 있습니다.
### 2. 서버측 설정
기본적으로 HTTPS는 443포트를 통해 통신을 진행합니다. 따라서 서버측에서 코드를 통해 HTTP 통신 방식인 80포트를 막고 443포트를 열어 주어야 합니다.
또는 80포트를 열여두지만 80 -> 443으로 재요청시켜 최종적으로 443포트에서 통신이 이루어지게 만들어야 합니다.
<br />
<br />

**참고자료**
<hr>
- HTTP와 HTTPS의 차이점은 무엇인가요?<br />
[https://aws.amazon.com/ko/compare/the-difference-between-https-and-http/](https://aws.amazon.com/ko/compare/the-difference-between-https-and-http/){:target="\_blank"}
- 적절한 HTTPS를 위한 SSL 인증서 구성<br />
[https://cloud.google.com/looker/docs/ssl-certificate-for-proper-https?hl=ko](https://cloud.google.com/looker/docs/ssl-certificate-for-proper-https?hl=ko){:target="\_blank"}
- HTTP, HTTPS의 차이점 및 전환의 중요성<br />
[https://seo.tbwakorea.com/blog/https-http/#part9](https://seo.tbwakorea.com/blog/https-http/#part9){:target="\_blank"}