# 네이버 클라우드 과정 개인 미니 프로젝트
- 과정명: 네이버 클라우드 캠프 데브옵스 7기
- 교육기관: 비트캠프 강남본원

## 프로젝트 배경
<p>네이버 클라우드 캠프 데브옵스 7기 과정을 수강하면서 개인 프로젝트를 진행했다. 개인 프로젝트는 유저 관리, 상품 관리, 판매 관리라는 세 가지 모듈만 있는 간단한 쇼핑몰을 Spring MVC, Spring 부트, MyBatis, React 등 프레임워크를 적용시키면서 리팩토링 하는 과정이다. 리팩토링 이외에도 자의적으로 기능을 추가시켰다.</p>
<p>리팩토링에 착수한 AS-IS 시스템은 Servlet, JSP를 투박하게 사용해 구현된 상태였다. MVC 아키텍처도 제대로 적용되지 않았을 뿐더러 Presentation Layer에서 비즈니스 로직을 수행하는 등 아키텍처가 정제되지 않았다. 이러한 낡고 투박한 시스템을 점차 모던한 MVC 시스템으로 변화시켜 나갔다.</p>

## 리팩토링 단계
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

### To be continued
기본적인 11단계의 리팩토링이 끝난 이후에도 Spring Framework에 Spring Boot를 적용하고, 리액트로 클라이언트단을 개발하는 등 개발을 계속 진행했다.