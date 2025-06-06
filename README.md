# mind-palace
Miscellaneous learnings that haven’t found a place in major categories like "Today I Learned"

<br>

---
---

<br>

# 웹

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
