# mind-palace
Miscellaneous learnings that haven’t found a place in major categories like "Today I Learned"

<br>

---
---

<br>

# 웹

## 서버 구축 시 기술 스택을 선택하는 기준

### 언어 및 개발자 친숙도
- 익숙한 언어
    - Python - Flask
    - JavaScript - Node.js / Express.js
    - Java - Spring
- 언어 특성
    - Python - 간결하고 배우기 쉬움
    - JavaScript - 프론트엔드와 동일한 언어 사용 가능
    - Java - 안정성과 확장성

### 프로젝트 규모와 복잡도
- 소규모/간단한 
    - 빠른 개발 가능
    - Python - Flask
    - JavaScript - Node.js / Express.js
- 중대형/복잡한 엔터프라이즈
    - 견고한 구조, 다양한 기능 지원
    - Java - Spring

### 성능 및 확장성
- 고성능, 비동기 처리
    - JavaScript - Node.js / Express.js
        - 이벤트 기반 비동기 처리로 I/O가 많은 서비스에 유리
- CPU 연산 많이 필요한 작업
    - Java - Spring
        - 멀티스레딩과 JVM 최적화로 안정적
- 빠른 개발 속도
    - Python - Flask

### 에코시스템과 라이브러리 지원
- 풍부한 라이브러리
    - JavaScript - Node.js / Express.js
- 데이터 과학/머신러닝 연동
    - Python - Flask

### 운영 환경 및 인프라
- 기존 인프라가 Java 중심
    - Spring 사용 권장
- 클라우드, 서버리스 환경
    - Node.js, Python(Flask) 인기
- 컨테이너 및 마이크로서비스
    - Spring Boot, Node.js, Flask 모두 가능하지만 Spring Boot가 안정적

### 커뮤니티와 지원
- Node.js와 Flask는 스타트업, 빠른 프로토타이핑에 인기
- Java(Spring)는 대기업, 공공기관, 금융권에서 안정적으로 널리 사용됨

### 개발 및 유지보수 비용
- 익숙한 스택은 유지보수 비용 감소
- 대규모 팀과 장기 프로젝트는 구조적이고 명확한 Spring이 유리



## 서버사이드렌더링(SSR) vs 클라이언트사이드렌더링(CSR)

### 서버사이드렌더링(SSR)
- 과정
    1. 사용자가 사이트에 접속
    2. 서버가 페이지에 필요한 DB 등의 데이터를 가져옴
    3. 서버가 HTML을 만들어서 브라우저에 전송
    4. 브라우저가 HTML을 받아 화면에 표시
- 장점
    1. 초기 로딩 속도 빠름: 완성된 HTML을 보여주기 때문
    2. SEO(검색엔진 최적화)에 좋음: 완성된 HTML이기 때문
- 단점
    1. 서버에서 렌더링하기 때문에 서버의 부담 증가
    2. 화면 새로고침 시간이 상대적으로 지연
- 사용 예
    - 블로그, 뉴스 등 초기 로딩이 빠르고 SEO가 중요한 경우

### 클라이언트사이드렌더링(CSR)
- 과정
    1. 사용자가 사이트에 접속
    2. 서버가 HTML 뼈대와 JS를 전송
    3. 브라우저가 JS를 실행 -> API 요청 -> 데이터 가져옴
    4. 브라우저가 가져온 데이터로 화면을 만들어 표시
- 장점
    1. 상호작용이 빨라 사용자 경험이 좋음
    2. 서버의 부담 감소
- 단점
    1. 초기 로딩 속도 느림: 브라우저가 만들어야 되기 때문
    2. SEO(검색엔진 최적화)에 불리: 검색엔진이 내용을 읽지 못할 수 있음
- 사용 예
    - 대시보드, SNS, 채팅 앱 등 상호작용이 중요한 경우

### 결론
- 브라우저가 HTML을 표시하기 전 누가 HTML을 만드는가에 따른 렌더링 전략


## URL
- Uniform Resource Locator
- 웹에서 자원의 위치를 나타내는 주소
- 인터넷에서 웹페이지나 파일 등에 접근하기 위한 인터넷 주소

### URL의 기본 구조
```
프로토콜://호스트:포트/경로?쿼리#프래그먼트
```
- 프로토콜  (Scheme)
    - 예: http, https, ftp 등
    - 웹에서 데이터를 주고받는 방식
        - https는 보안이 강화된 프로토콜
- 호스트 (Host)
    - 예: www.example.com
    - 서버의 도메인 이름 또는 IP 주소
    - 어디에 있는 서버인지 알려줌
- 포트 (Port)
    - 선택 입력
    - 예: :80, :443
    - 서버에서 네트워크 통신을 담당하는 특정 입구 번호
    - 보통 HTTP는 80, HTTPS는 443번 포트를 기본으로 사용하므로 생략 가능
- 경로 (Path)
    - 예: /folder/page.html
    - 서버 내에서 자원의 위치
    - 웹사이트 내 폴더와 파일 구조를 의미
- 쿼리 (Query String)
    - 선택 입력
    - 예: ?id=123&sort=asc
    - 서버에 전달하는 추가 정보
    - ? 뒤에 키=값 쌍으로 여러 개를 &로 구분합니다.
- 프래그먼트 (Fragment)
    - 선택 입력
    - 예: #section2
    - 웹페이지 내 특정 위치(앵커)를 가리킴
    - 서버로 전송되지 않고, 클라이언트에서 처리
- 예
    ```
    https://www.example.com:443/path/to/page.html?search=nodejs#comments
    ```
    - 프로토콜: https
    - 호스트: www.example.com
    - 포트: 443
    - 경로: /path/to/page.html
    - 쿼리: search=nodejs
    - 프래그먼트: comments


## HTTP 메서드

### GET
- 서버에서 리소스(데이터)를 조회
- 예: 웹페이지 접속

### POST
- 서버에 리소스(데이터)를 생성하거나 전송
- 예: 회원 가입, 댓글 작성

### PUT
- 리소스를 전체 수정
- 예: 사용자 정보 전체 업데이트

### PATCH
- 리소스를 부분 수정
- 예: 비밀번호만 변경

### DELETE
- 리소스를 삭제
- 예: 게시글 삭제

### HEAD
- GET과 유사하지만, 응답 본문 없이 헤더 정보만 요청
- 예: 리소스 존재 여부 확인

### OPTIONS
- 서버가 지원하는 메서드 목록을 요청
- 주로 CORS(Cross-Origin Resource Sharing) 사전 요청에서 사용
- 예: 클라이언트가 POST 요청을 하기 전, 서버에 OPTIONS로 요청해서 Access-Control-Allow-* 헤더 확인


## OAuth

### OAuth 2.0의 기본 구조
- Resource Owner (자원 소유자)
    - 보통 사용자. 자신의 데이터를 다른 애플리케이션이 접근하도록 허용
    - 예: Google 캘린더
- Client (클라이언트 애플리케이션)
    - 사용자의 데이터에 접근하려는 제3자 애플리케이션
    - 예: 일정 앱
- Authorization Server (인증 서버)
    - 사용자의 권한을 인증하고, 액세스 토큰을 발급하는 서버
    - 예: Google, Facebook의 인증 서버
- Resource Server (자원 서버)
    - 보호된 데이터를 호스팅하는 서버
    - 액세스 토큰을 이용해 데이터에 접근 가능

### OAuth 2.0의 기본 흐름
1. 사용자 인증 요청
    - 클라이언트가 사용자를 인증 서버로 리디렉션 → 사용자는 로그인 및 권한 부여
2. Authorization Code 발급
    - 사용자가 권한을 승인하면 인증 서버가 클라이언트에게 authorization code를 전달
3. Access Token 요청
    - 클라이언트는 authorization code와 함께 인증 서버에 액세스 토큰을 요청
4. Access Token 발급
    - 인증 서버가 클라이언트에게 액세스 토큰을 반환
5. 자원 접근
    - 클라이언트는 액세스 토큰을 사용해 자원 서버의 사용자 데이터를 요청

### OAuth 2.0의 특징
- 액세스 토큰을 통해 자원 접근 제어
- 사용자의 비밀번호 노출 없이 권한 위임 가능


## 보안

### 보안 취약점
- 컴퓨터 시스템, 네트워크, 애플리케이션, 또는 그 구성요소에서 악의적인 공격자가 악용할 수 있는 결함이나 약점

#### 보안 취약점의 주요 유형
- 소프트웨어 취약점
    - 프로그래밍 실수나 설계 결함으로 발생
    - 예: 버퍼 오버플로우(Buffer Overflow), 포맷 스트링 공격 등
- 웹 취약점
    - 웹 애플리케이션에 존재하는 보안상의 허점
    - 예: SQL Injection, XSS, CSRF
- 인증 및 권한 관련 취약점
    - 약한 비밀번호, 인증 우회, 세션 탈취 등이 포함
    - 예: 관리자 페이지에 인증 없이 접근 가능한 경우
- 네트워크 취약점
    - 네트워크 구성 또는 통신 프로토콜 상의 문제
    - 예: 스니핑(Sniffing), MITM(Man-In-The-Middle) 공격
- 설정 오류 (Misconfiguration)
    - 기본 비밀번호 사용, 불필요한 포트 개방, 과도한 권한 설정 등
    - 예: AWS S3 버킷 퍼블릭 설정

##### 웹 취약점

###### CSRF
- CSRF
    - Cross-Site Request Forgery
    - 공격자가 사용자가 로그인한 상태를 이용해 몰래 요청을 보내는 공격
    - 사용자가 의도하지 않은 요청이 실행되는 문제
- CSRF 토큰
    - 서버가 POST 요청 등 중요 요청을 받을 때 “이 요청이 진짜 사용자로부터 온 것인지” 검증
    - 원리
        1. 서버가 페이지 로드 시 세션과 연결된 CSRF 토큰 발급
        2. HTML 폼에 숨겨진 <input type="hidden" name="csrf_token">으로 포함
        3. 사용자가 폼을 제출하면 CSRF 토큰이 함께 서버로 전송
        4. 서버가 세션에 저장된 토큰과 비교
            - 같으면 정상 요청
            - 다르면 요청 거부
    - 결론: CSRF 토큰은 서버가 “이 요청은 정당한 사용자의 요청”이라고 확인할 수 있게 하는 안전 장치
- 정상 사용자의 요청 흐름
    ```
    [1] 클라이언트 GET 요청 → 서버
        |
        v
    [2] 서버: 새로운 세션 생성 → session_id 발급
        |
        v
    [3] 서버: CSRF 토큰 생성 → HTML에 포함
        |
        v
    [4] 클라이언트: 쿠키(session_id) + CSRF 토큰 저장
        |
        v
    [5] 클라이언트 POST 요청 → 서버
        | 포함: session_id 쿠키 + CSRF 토큰 + 데이터
        v
    [6] 서버: 세션과 토큰 검증
        | 정상 요청 → 처리
    ```
    - 이 과정에서 클라이언트는 자신의 세션 쿠키 + 토큰을 함께 보내므로 정상 요청으로 처리됨
- CSRF 공격 시도 (사용자 세션 탈취 없음)
    ```
    [1] 공격자 GET 요청 → 서버
        |
        v
    [2] 서버: 공격자의 새로운 세션 생성 → 공격자의 새로운 session_id 발급
        |
        v
    [3] 서버: 공격자의 새로운 CSRF 토큰 생성 → HTML에 포함
        |
        v
    [4] 공격자 POST 요청 → 서버
        | 포함: 공격자가 발급받은 session_id + 토큰
        v
    [5] 서버: 세션과 토큰 검증
        | 공격 대상 사용자 세션 아님 → 공격 실패
    ```
    - 공격자가 사용자의 세션 쿠키를 모르면 요청이 정상 사용자의 요청으로 처리되지 않음
    - 그러면 공격자가 사용자의 세션을 탈취하면?
        - 이것을 세션 탈취(Session Hijacking)라고 함
    - 혹은 공격자가 사용자의 세션을 특정할 수 있다면?
        - 이것을 세션 고정(Session Fixation)이라고 함

### OWASP
- Open Worldwide Application Security Project
- 웹 애플리케이션 보안을 개선하기 위한 글로벌 비영리 단체

#### OWASP Top 10 (2021)
- A01:2021 - Broken Access Control
    - 권한이 없는 사용자가 다른 사용자의 데이터나 기능에 접근할 수 있는 문제
    - 예: URL 권한 우회, IDOR (Insecure Direct Object Reference), 기능 숨기기 실패 등
- A02:2021 - Cryptographic Failures
    - 민감한 데이터가 암호화되지 않거나 암호화가 취약
    - 예: 민감 정보 평문 저장, HTTPS 미사용, 약한 암호 알고리즘 사용 (예: MD5)
- A03:2021 - Injection
    - 사용자 입력값이 서버 코드나 쿼리로 잘못 해석되어 실행됨
    - 예: SQL Injection, XSS (Cross-Site Scripting), Command Injection, LDAP Injection, XML Injection
- A04:2021 - Insecure Design
    - 설계부터 보안이 충분히 고려되지 않아 구조적 결함 발생
    - 예: 인증 로직 우회 가능, 비즈니스 논리상 보안 결함, 비정상적 접근 흐름 미제어
- A05:2021 - Security Misconfiguration
    - 서버, 프레임워크, 보안 설정의 오류
    - 예: 디버그 모드 ON, 기본 비밀번호 미변경, 민감 정보가 노출된 에러 메시지
- A06:2021 - Vulnerable and Outdated Components
    - 보안 취약점이 있는 외부 라이브러리나 패키지 사용
    - 예: 오래된 jQuery 사용, 취약한 라이브러리 미패치, 종속성 보안 패치 누락
- A07:2021 - Identification and Authentication Failures
    - 인증 및 세션 관리 시스템이 안전하지 않음
    - 예: 세션 고정 (Session Fixation), 약한 비밀번호 정책, 다중 인증 누락
- A08:2021 - Software and Data Integrity Failures
    - 코드나 데이터의 무결성 검증 실패
    - 예: 코드 서명 없이 업데이트, 취약한 CI/CD 파이프라인, 신뢰되지 않은 패키지 사용
- A09:2021 - Security Logging and Monitoring Failures
    - 공격 탐지 및 사고 대응이 불가능한 상태
    - 예: 로그인 실패 로그 누락, 경고/알림 시스템 없음, 의심스러운 활동 미탐지
- A10:2021 - Server-Side Request Forgery (SSRF)
    - 서버가 외부 또는 내부 시스템에 악성 요청을 하도록 유도됨
    - 예: 서버가 외부 URL을 그대로 요청, 내부 IP에 요청 가능 `(http://127.0.0.1:8080)`

<br>

---

<br>

# SQL

## DDL
- 데이터베이스 구조(테이블, 인덱스 등)를 정의하거나 변경하는 명령어
- CREATE, ALTER, DROP, TRUNCATE

### in MYSQL
- AUTO_INCREMENT: 테이블의 특정 컬럼(주로 기본키)에 자동으로 1씩 증가하는 값을 부여할 때 사용
    - CREATE할 때 선언 가능
    - ALTER할 때 선언 혹은 값을 주어 시작 값으로 설정 가능
    - 'SET @@auto_increment_increment = 값'을 통해 컬럼이 증가할 때 몇씩 증가할 지 설정 가능
        - 기본값은 1이며, 설정 직후의 값이 아닌 다음 값부터 적용

## DML
- 데이터(행)를 조회하거나 조작하는 명령어
- SELECT, INSERT, UPDATE, DELETE

### in MYSQL
- LIMIT: SELECT 문에서 결과 행(row)의 개수를 제한할 때 사용

## DCL
- 데이터베이스 접근 권한을 제어하는 명령어
- GRANT, REVOKE

## 그 밖에 MYSQL syntax

### 명령어
- 'DESC 테이블명': 테이블의 구조(스키마)를 확인
    - 'DESCRIBE 테이블명' 동일
    - 'VIEW'에도 사용 가능
        - 'DESC 뷰명'
- 'SHOW': 데이터베이스나 서버에 대한 정보(메타데이터)를 조회
    - 구조, 설정, 상태 같은 시스템 정보를 조회

<br>

---

<br>

# CI/CD

## CI
- Continuous Integration
- 지속적인 통합
- 개발자들이 작성한 코드를 자주(수시로) 통합하고 자동으로 테스트하는 과정

## CD
- Continuous Delivery/Deployment
- 지속적인 배포
- CI 이후 과정을 통해 코드를 자동으로 배포하는 것

<br>

---

<br>

# 로그인 기능 구현
- 로그인 기능은 본질적으로 "사용자 인증(Authentication)"을 구현하는 과정
- 서버가 사용자의 신원을 확인하고, 인증된 상태를 유지하는 것이 핵심

## 세션 기반 인증 (Session-Based Authentication)
- 작동 방식
    1. 사용자가 ID/비밀번호로 로그인
    2. 서버가 자격 증명을 검증하고 세션 ID를 생성
    3. 세션 ID를 쿠키에 저장하여 브라우저로 전송
    4. 이후 요청마다 쿠키를 통해 로그인 상태 유지
- 주로 사용되는 곳
    - Flask, Django, Express.js, Rails 등 대부분의 전통적인 서버 프레임워크
- 장점
    - 간단하고 직관적
    - 서버 측에서 로그인 상태를 완전히 관리
- 단점
    - 서버가 세션 정보를 계속 유지해야 하므로 확장성이 떨어짐 (대규모 서비스에 불리)

## 토큰 기반 인증 (Token-Based Authentication)
- 작동 방식
    1. 사용자 로그인 → 서버가 JWT(토큰)을 생성
    2. 토큰을 브라우저에 저장 (보통 localStorage, sessionStorage, 혹은 HttpOnly 쿠키)
    3. 이후 모든 요청에 토큰을 Authorization 헤더에 포함
    4. 서버는 토큰을 검증해 사용자를 식별
- 주로 사용되는 곳
    - REST API, 모바일 앱, React/Vue 등의 SPA와 백엔드 분리 구조
    - Express.js, Flask, FastAPI 등에서 많이 사용됨
- 장점
    - 서버 상태를 유지하지 않아도 됨 (stateless)
    - 마이크로서비스나 프론트-백 분리 환경에 적합
- 단점
    - 보안에 더 민감해야 함 (토큰 탈취 시 문제 발생)
    - 토큰을 무효화하는 방식은 별도 구현이 필요함

## OAuth 2.0 / OpenID Connect (소셜 로그인 등)
- 작동방식
    - Google, Facebook, GitHub 등의 외부 서비스로 인증을 위임
    - 사용자 로그인 → 서비스에서 인증 → 서버가 사용자 정보를 받아 로그인 처리
- 주로 사용되는 곳
    - 사용자 수가 많은 서비스
    - 소셜 로그인이 필요한 경우
- 장점
    - 사용자 등록 부담 없음
    - 보안 및 인증 처리를 신뢰성 높은 외부 서비스에 맡김
- 단점
    - 구현 복잡도 높음 (redirect, callback 등 필요)
    - API 키/비밀키 관리 필요

## 패스워드리스 로그인 (Passwordless Login)
- 작동방식
    - 이메일 링크 로그인, OTP 인증 등
    - 사용자에게 비밀번호 없이 일회용 링크나 코드를 전송하여 로그인
- 주로 사용되는 곳
    - 보안 중심의 서비스
    - UX 개선이 중요한 서비스
- 장점
    - 비밀번호 관리 필요 없음
    - 피싱 위험 감소
- 단점
    - 이메일/SMS 전송 인프라 필요
    - 구현 난이도 있음

## JWT 기반 토큰 인증 vs OAuth 2.0 / OpenID Connect

| 항목 | JWT 기반 인증 | OAuth 2.0 / OpenID Connect |
|------|------|------|
| 목적 | 자체 로그인: 사용자가 직접 회원가입하고 로그인함 | 외부 계정 로그인: Google, GitHub, Facebook 등의 계정 사용 |
| 사용자 관리 | 직접 DB에 사용자 저장 (ID/비밀번호) | 외부 서비스가 사용자 인증, 우리는 결과만 받아옴 |
| 토큰 종류 | Access Token (보통 JWT) | Access Token + ID Token (OpenID일 때) |
| 로그인 과정 | 사용자가 우리 서비스에 로그인 → 서버가 JWT 발급 | 사용자가 외부 서비스에 로그인 → 콜백으로 사용자 정보 수신 |
| 보안 책임 | 우리가 직접 비밀번호를 검증하고 보안 처리 | 외부 서비스(Google 등)가 로그인 처리 |
| 구현 복잡도 | 비교적 단순 | 상대적으로 복잡 (redirect, callback, 인증 흐름) |
| 적합한 상황 | API 기반 서비스, SPA(React, Vue 등) | 사용자 등록 허들이 낮아야 할 때, 신뢰성 있는 인증 필요 시 |

<br>

---

<br>

# 소프트웨어 시스템 / 응용 프로그램
- 계층 구조
    ```
    [시스템 수준]
    ├── 소프트웨어 시스템 / 응용 프로그램
        └── 소프트웨어 아키텍처 (또는 소프트웨어 구조)
            └── 아키텍처 스타일 / 아키텍처 패턴 (MVC, Layered, Microservices 등)
                └── 컴포넌트 (Component)
                    └── 모듈 (Module)
                        └── 클래스 (Class)
                            └── 함수/메서드 (Function/Method)
    ```
    - 소프트웨어 아키텍처: 시스템의 상위 구조. 구성요소, 관계, 상호작용을 정의
    - 아키텍처 스타일 / 아키텍처 패턴: 아키텍처를 설계할 때 따르는 설계 방식의 유형
        - 예: MVC, Layered, Microservices
    - 컴포넌트: 특정 기능을 독립적으로 담당하는 재사용 가능한 단위
    - 모듈: 보통 파일 단위로 나뉜 코드 묶음, 컴포넌트 안에 있을 수 있음
    - 클래스 / 함수: 모듈 안에서 실제 동작을 정의하는 코드

- 설계 구조(예: Flask 기준)
    - 프레임워크마다 다름
    ```
    [소프트웨어 시스템 / 애플리케이션]
    └── 프레임워크 (Framework)
        └── 라이브러리 (Library)
            └── 패키지 (Package)
                └── 모듈 (Module, .py 파일)
                    └── 클래스 (Class)
                        └── 함수 / 메서드 (Function / Method)
    ```
    - 전체 앱 흐름 제어
        - 프레임워크: 전체 앱의 구조와 흐름을 정의하는 틀, 제어 흐름을 소유
            - 개발에 대한 전체 구조나 규칙을 제공
            - 프레임워크는 여러 라이브러리를 포함하고 있을 수 있음
            - 예: Flask, Django
    - 특정 기능 제공
        - 라이브러리: 특정 기능을 수행하는 도구 모음, 개발자가 호출해서 사용
            - 여러 모듈과 패키지를 묶은 단위
            - 예: Jinja2, SQLAlchemy, requests
    - 코드 파일/폴더 구조화
        - 패키지: 파이썬의 디렉터리 단위 코드 묶음 (`__init__.py` 포함)
            - 여러 개의 모듈(파이썬 파일)을 담고 있는 디렉터리(폴더) 단위
            - 파이썬에서는 `__init__.py` 파일이 있어야 패키지로 인식
            - 패키지를 통해 관련된 모듈들을 계층적으로 묶어서 관리
            - 예: flaskr, flaskr.auth, flaskr.blog
            - 서브패키지(Subpackage): 패키지 안에 또 다른 패키지가 존재 가능
                - 패키지 내부의 하위 폴더가 또 `__init__.py` 파일을 가지면 서브패키지라고 함
            - 네임스페이스 패키지(namespace package): Python 3.3 이후부터 `__init__.py` 없이도 패키지처럼 동작하는 패키지
                - 하지만 보통 Flask 프로젝트 등에서는 전통적인 `__init__.py`가 있는 패키지를 주로 사용
        - 모듈: 하나의 파이썬 파일로 기능 단위 구현
            - Python에서 가장 기본적인 단위
            - `.py` 파일 하나가 모듈
            - 예: routes.py, models.py
    - 실제 로직 구현
        - 클래스: 상태와 동작을 캡슐화한 객체 설계 단위
            - 예: User, Post
        - 함수/메서드: 구체적인 작업을 수행하는 코드 조각
            - 예: create_user(), get_post_by_id()

<br>

---

<br>

# B2X

## 📌 B2X 용어 한눈에 정리

| 약자       | 풀네임(의미)                                         | 정의                                 | 대표 예시                          |
| --------- | -------------------------------------------------- | ------------------------------------ | -------------------------------- |
| **B2B**   | *Business to Business*<br>(기업 → 기업)              | 기업이 다른 기업에게 제품·서비스 제공    | SaaS(슬랙, 노션), 기업용 보안 솔루션, 도매유통 |
| **B2C**   | *Business to Consumer*<br>(기업 → 소비자)            | 기업이 일반 소비자에게 직접 서비스 제공   | 쇼핑몰(쿠팡), OTT(넷플릭스), 배달앱(배달의민족), 게임 |
| **B2G**   | *Business to Government*<br>(기업 → 정부)            | 기업이 정부·공공기관에 시스템/서비스 제공 | 공공 SI 프로젝트, 국가용 보안 시스템, 공공조달, 관공서 시스템 구축, 정부 프로젝트 |
| **C2C**   | *Consumer to Consumer*<br>(소비자 → 소비자)           | 개인 간 상품·서비스 거래               | 중고거래(당근마켓, 번개장터), 개인 간 렌탈(Airbnb(개인 호스트 기준)) |
| **C2B**   | *Consumer to Business*<br>(소비자 → 기업)             | 개인이 기업에 가치·콘텐츠 제공         | 인플루언서 협찬, 리뷰 제공, 프리랜서 플랫폼(크몽) |
| **G2B**   | *Government to Business*<br>(정부 → 기업)            | 정부가 기업을 위한 서비스 제공          | 기업용 전자민원 서비스(전자세금계산서), 공공데이터 API, 국가 데이터 API |
| **G2C**   | *Government to Citizen*<br>(정부 → 시민)             | 정부가 일반 시민에게 서비스 제공        | 정부24, 세금조회, 주민등록 등본 발급, 건강보험 자격 조회 |
| **B2E**   | *Business to Employee*<br>(기업 → 직원)              | 기업이 사내 구성원에게 서비스/복지 제공  | 사내 복지몰, 사내 교육 시스템(LMS) |
| **D2C**   | *Direct to Consumer*<br>(제조사 → 소비자 직접 판매)    | 브랜드가 유통사 없이 소비자에게 직판     | 애플 공식스토어, 무신사 스토어 자체 브랜드, 아임웹 브랜드몰, 패션 D2C 브랜드 |
| **B2B2C** | *Business to Business to Consumer*<br>(기업 → 기업 → 소비자) | 기업이 다른 기업을 통해 소비자에게 서비스 제공 | 네이버 스마트스토어(입점사→네이버→소비자), 배달 플랫폼 구조 |
| **O2O**   | *Online to Offline*<br>(온라인 → 오프라인 연결)                | 온라인 플랫폼이 오프라인 서비스 소비로 연결   | 카카오T, 배달앱(쿠팡이츠, 배달의민족), 미용실/병원 예약앱 |