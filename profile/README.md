# 네이버 클라우드 과정 개인 미니 프로젝트
- 과정명: 네이버 클라우드 캠프 데브옵스 7기
- 교육기관: 비트캠프 강남본원

## 프로젝트 배경
<p>네이버 클라우드 캠프 데브옵스 7기 과정을 수강하면서 개인 프로젝트를 진행했다. 개인 프로젝트는 유저 관리, 상품 관리, 판매 관리라는 세 가지 모듈만 있는 간단한 쇼핑몰을 Spring MVC, Spring 부트, MyBatis, React 등 프레임워크를 적용시키면서 리팩토링 하는 과정이다. 리팩토링 이외에도 자의적으로 기능을 추가시켰다.</p>
<p>리팩토링에 착수한 AS-IS 시스템은 Servlet, JSP를 투박하게 사용해 구현된 상태였다. MVC 아키텍처도 제대로 적용되지 않았을 뿐더러 Presentation Layer에서 비즈니스 로직을 수행하는 등 아키텍처가 정제되지 않았다. 이러한 낡고 투박한 시스템을 점차 모던한 MVC 시스템으로 변화시켜 나갔다.</p>

## 리팩토링 단계
각 리팩토링 단계마다 각 브랜치 페이지에 리팩토링 사항, 추가 구현한 기능, 마주친 문제들과 해결한 방식을 기술하였다.<br>
1단계, 2단계에서는 Git을 사용하지 않았다.

### [3. JSP EL/JSTL](https://github.com/ncamp-miniproject/ncamp-miniproject-backend/tree/3_jspel_jstl)
JSP가 오로지 View의 역할만 하도록 JSP 코드에 EL, JSTL을 적용시켰다.

### [4. MyBatis/Spring](https://github.com/ncamp-miniproject/ncamp-miniproject-backend/tree/4_mybatis_spring)
프로젝트에 스프링 프레임워크를 적용시켰으나 아직 스프링 MVC를 적용시키지 않았다.<br>
난잡한 JDBC 코드로 이루어진 Persistence Layer에 MyBatis를 적용시켰다.

### [5. AOP Transaction](https://github.com/ncamp-miniproject/ncamp-miniproject-backend/tree/5_aop_transaction)
AOP를 적용시켰다. AOP를 활용해 로깅과 트랜잭션을 처리했다.

### [6. Controller](https://github.com/ncamp-miniproject/ncamp-miniproject-backend/tree/6_controller)
본격적으로 스프링 MVC를 적용시키기 시작했다. Struts Framework를 모방한 1st party 프레임워크를 Deprecated 시키고 스프링 Controller를 적용시켰다.

### [7. URI Pattern](https://github.com/ncamp-miniproject/ncamp-miniproject-backend/tree/7_uri_pattern)
기존에는 고전적인 RPC (Remote Procedure Call) 방식의 API를 RESTful API로 변경했다.
동사형 URL을 명사형 URL로 변경했다.

### [8. RestController](https://github.com/ncamp-miniproject/ncamp-miniproject-backend/tree/8_rest_controller)
시스템을 좀 더 RESTful하게 변경했다. View를 반환하던 기존 Controller에서 JSON 데이터를 반환하는 RestController의 이전을 시작했다.

### [9. jQuery](https://github.com/ncamp-miniproject/ncamp-miniproject-backend/tree/9_jQuery)
jQuery를 이용해 클라이언트단 프로그래밍을 진행했다.

### [10. Ajax](https://github.com/ncamp-miniproject/ncamp-miniproject-backend/tree/10_ajax)
jQuery의 Ajax를 적용함으로써 서버와 비동기 통신을 구현했다.

### [11. CSS Bootstrap](https://github.com/ncamp-miniproject/ncamp-miniproject-backend/tree/11_css_bootstrap)
CSS Bootstrap을 적용하여 화면단을 디자인했다.

### [12. Spring Boot](https://github.com/ncamp-miniproject/ncamp-miniproject-backend/tree/12_spring_boot)
프로젝트를 Spring Boot로 이전하였다.

### To be continued
기본적인 12단계의 리팩토링이 끝난 이후에도 Spring Security Framework를 적용하고 리액트로 클라이언트단을 개발하는 등 개발을 계속 진행했다.

## 기술 스택
![Slice 2](https://github.com/ncamp-miniproject/.github/assets/60085941/c46b5d0f-face-4ce6-abd7-6f6436bdd99e)

## 추가 기능
- 장바구니
  - 기존 시스템에서는 하나의 상품에 대해서 한 번의 구매 행위만 일어날 수 있었다. (상품과 구매 사이의 1대1 관계)
  - 한 번의 구매 행위에 대해 여러 개의 상품을 구매할 수 있도록 transaction_prod 엔터티를 추가했다. (transaction 테이블과 transaction_prod 테이블 사이의 1:N 관계)
- 상품별 카테고리
- 파일 업로드

  - Multipart Form
  - Base64 인코딩 전송
- 회원가입 시 이메일 인증
- Java Reflection API를 사용한 동적 객체 바인딩
- 상품 목록 정렬
- 다중 파일 업로드
- Spring Security
  - 토큰 기반 인증
    - JSON 평문 형태의 암호화하지 않은 토큰
    - JWT
- 판매자 등록
- 리액트

## 클라우드 배포
### 클라우드 다이어그램
![Slice 1](https://github.com/ncamp-miniproject/.github/assets/60085941/79d70213-13fc-4a64-8ba4-1b804db8c00c)

### VPC
ncamp-miniproject

### Subnet
- ncamp-web-lb-public-subnet
  - IP 주소 범위: 10.0.255.0/24
  - Internet Gateway: Y (Public)
  - 용도: Load Balancer
  - NACL
    - 규칙 1
      - Inbound
      - port: 80
      - 출발지: 0.0.0.0/0
      - 차단
- ncamp-web-server-priv-subnet
  - IP 주소 범위: 10.0.1.0/24
  - Internet Gateway: N (Private)
  - 용도: 일반 (웹 서버)
- ncamp-api-priv-subnet
  - IP 주소 범위: 10.0.2.0/24
  - Internet Gateway: N (Private)
  - 용도: 일반 (API 서버)
- ncamp-cicd-public-subnet
  - IP 주소 범위: 10.0.100.0/24
  - Internet Gateway: Y (Public)
  - 용도: 일반 (CI/CD)

### 서버
- ncamp-cicd-public-kr2
  - 하이퍼바이저
    - KVM
  - OS
    - Ubuntu 22.04
  - 서브넷
    - ncamp-cicd-public-subnet
  - 서버 스펙
    - Standard
    - s2-g3 (vCPU 2EA, Memory 8GB)
  - Network Interface
    - IP: 10.0.100.101
  - Public IP 할당
  - 스토리지
    - 30GB
  - ACG
    - Inbound
      - 규칙 1
        - TCP
        - 접근 소스: My IP
        - 포트: 22
      - 규칙 2
        - ICMP
        - 접근 소스: My IP
      - 규칙 3
        - TCP
        - 접근 소스: My IP
        - 포트: 8080
    - Outbound
      - 규칙 1
        - TCP
        - 목적지: 0.0.0.0/0
        - 포트: 1-65535
      - 규칙 2
        - UDP
        - 목적지: 0.0.0.0/0
        - 포트: 1-65535
      - 규칙 3
        - ICMP
        - 목적지: 0.0.0.0/0
- ncamp-web-server-priv-kr2
  - 용도
    - HTML/JavaScript/CSS로 이루어진 클라이언트 애플리케이션을 제공하는 제공하는 웹 서버
  - 하이퍼바이저
    - KVM
  - OS
    - Ubuntu 22.04
  - 서브넷
    - ncamp-web-server-priv-subnet
  - 서버 스펙
    - Standard
    - g2-g3 (vCPU 2EA, Memory 8GB)
  - Network Interface
    - IP: 10.0.1.101
  - Public IP 미할당
  - 스토리지
    - 50GB
  - ACG
    - Inbound
      - 규칙 1
        - TCP
        - 접근 소스: 10.0.0.0/16
        - 포트: 80
      - 규칙 2
        - TCP
        - 접근 소스: 10.0.0.0/16
        - 포트: 22
    - Outbound
      - 규칙 1
        - TCP
        - 목적지: 0.0.0.0/0
        - 포트: 1-65535
      - 규칙 2
        - UDP
        - 목적지: 0.0.0.0/0
        - 포트: 1-65535
      - 규칙 3
        - ICMP
        - 목적지: 0.0.0.0/0
- ncamp-web-server-priv-kr2-2
  - 용도
    - High Availability를 위한 두 번째 웹 서버
  - 하이퍼바이저
    - KVM
  - OS
    - Ubuntu 22.04
  - 서브넷
    - ncamp-web-server-priv-subnet
  - 서버 스펙
    - Standard
    - g2-g3 (vCPU 2EA, Memory 8GB)
  - Network Interface
    - IP: 10.0.1.101
  - Public IP 미할당
  - 스토리지
    - 50GB
  - ACG
    - Inbound
      - 규칙 1
        - TCP
        - 접근 소스: 10.0.0.0/16
        - 포트: 80
      - 규칙 2
        - TCP
        - 접근 소스: 10.0.0.0/16
        - 포트: 22
    - Outbound
      - 규칙 1
        - TCP
        - 목적지: 0.0.0.0/0
        - 포트: 1-65535
      - 규칙 2
        - UDP
        - 목적지: 0.0.0.0/0
        - 포트: 1-65535
      - 규칙 3
        - ICMP
        - 목적지: 0.0.0.0/0
- ncamp-api-priv-kr2
  - 용도
    - API 서버
  - 하이퍼바이저
    - KVM
  - OS
    - Ubuntu 22.04
  - 서브넷
    - ncamp-api-priv-subnet
  - 서버 스펙
    - High-CPU
    - c4-g3 (vCPU 4EA, Memory 8GC)
  - Network Interface
    - IP: 10.0.2.101
  - Public IP 미할당
  - 스토리지
    - 50GB
  - ACG
    - Inbound
      - 규칙 1
        - TCP
        - 접근 소스: 10.0.0.0/16
        - 포트: 80
      - 규칙 2
        - TCP
        - 접근 소스: 10.0.0.0/16
        - 포트: 22
    - Outbound
      - 규칙 1
        - TCP
        - 목적지: 0.0.0.0/0
        - 포트: 1-65535
      - 규칙 2
        - UDP
        - 목적지: 0.0.0.0/0
        - 포트: 1-65535
      - 규칙 3
        - ICMP
        - 목적지: 0.0.0.0/0
- ncamp-api-priv-kr2-2
  - 용도
    - 두 번째 API 서버
  - 하이퍼바이저
    - KVM
  - OS
    - Ubuntu 22.04
  - 서브넷
    - ncamp-api-priv-subnet
  - 서버 스펙
    - High-CPU
    - c4-g3 (vCPU 4EA, Memory 8GC)
  - Network Interface
    - IP: 10.0.2.101
  - Public IP 미할당
  - 스토리지
    - 50GB
  - ACG
    - Inbound
      - 규칙 1
        - TCP
        - 접근 소스: 10.0.0.0/16
        - 포트: 80
      - 규칙 2
        - TCP
        - 접근 소스: 10.0.0.0/16
        - 포트: 22
    - Outbound
      - 규칙 1
        - TCP
        - 목적지: 0.0.0.0/0
        - 포트: 1-65535
      - 규칙 2
        - UDP
        - 목적지: 0.0.0.0/0
        - 포트: 1-65535
      - 규칙 3
        - ICMP
        - 목적지: 0.0.0.0/0

### 로드밸런서
- ncamp-web-server-pub-lb
  - 용도
    - 웹 서버용 로드밸런서
  - 타입
    - 애플리케이션 로드밸런서
  - Target group
    - ncamp-web-server-priv-kr2
    - ncamp-web-server-priv-kr2-2
- ncamp-api-pub-lb
  - 용도
    - api 서버용 로드밸런서
  - 타입
    - 애플리케이션 로드밸런서
  - Target group
    - ncamp-api-priv-kr2
    - ncamp-api-priv-kr2-2

### 기타
- NAT Gateway 설정
- Global DNS에 도메인 등록
- TLS 통신을 위한 인증서 발급
