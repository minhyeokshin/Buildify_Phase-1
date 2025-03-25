# 📦 BuildiFy - WMS 시스템 (1차 프로젝트)

## 📌 프로젝트 개요
**BuildiFy**는 Java 기반 CLI 창고관리 시스템(Warehouse Management System)입니다.  
조립형 PC 부품의 입출고 및 재고 관리를 중심으로, 실무 흐름을 기반으로 설계된 CLI 기반 재고관리 프로젝트입니다.

MySQL DB 연동, 계정 승인 시스템, 입출고 처리 흐름, 예외 검증 로직 등  
다양한 기능을 팀 협업 기반으로 구현한 **1차 프로젝트 버전**입니다.

---

## 🖥 사용 기술 스택

- **Language**: Java 17
- **Database**: MySQL (Railway 기반 Cloud 사용)
- **Framework / Library**: JDBC, Lombok
- **Version Control**: Git & GitHub
- **기타 설계 요소**: DI 구조, Validator, ErrorCode Enum

---

## ✅ 주요 기능

### 👨‍💼 사용자 (입점사)
- 회원가입 신청 → **관리자 승인** 후 계정 활성화
- 로그인 / 회원 정보 조회 및 수정
- **입고 요청**, **출고 요청** 등록
- 자사 **재고 목록 조회**

### 👨‍🔧 관리자
- 회원가입 승인 및 사용자 계정 관리
- **입고/출고 요청 승인 및 처리**
- 전체 재고 관리
- 관리자 본인 정보 조회 및 수정

---

## 📂 프로젝트 폴더 구조

```
Buildify/
├── src/
│   ├── Main.java
│   ├── common/
│   ├── config/
│   ├── controller/
│   ├── domain/
│   │   ├── inbound/
│   │   ├── outbound/
│   │   ├── inventory/
│   │   └── accountManagement/
│   ├── dto/
│   ├── exception/
│   ├── MySql/
│   └── resources/
```

---

## ▶ 실행 가이드

### 실행 방법
1. `src/Main.java` 실행
2. Lombok, JDBC Connector JAR 설치 필요
3. DB 초기 세팅

---

## 📦 제품 카테고리 (1차 기준)

- CPU
- RAM
- 메모리
- 그래픽카드
- 모니터
- 마우스
- 키보드

> 💡 2차 프로젝트에서 제품 카테고리 추가 예정

---

## 📌 설계 포인트

- **DI 기반 객체 주입** → `Diconfig.java`
- **입력 유효성 검증** → `ValidCheck.java`
- **에러코드 관리** → `ErrorCode.java + CustomException`
- **SQL 기반 프로시저 분리** → `MySql/Inbound`, `Outbound` 등
- **협업 기준 1인 1모듈 개발** → 모듈별 책임 명확

---

## ⚠️ 실행 중 발생 가능한 문제

| 문제 | 원인 | 해결 방법 |
|------|------|-------------|
| DB 연결 오류 | 커넥션 정보 오타 | `DBConnection.java` 설정 확인 |
| 테이블 없음 | SQL 미실행 | `wmsdb.sql` 직접 실행 |
| 숫자 입력 오류 | 문자 입력 | `ValidCheck`로 검증 처리 필요 |

---

## 🗂️ 클래스 다이어그램
> 📌 클래스 간 관계 및 흐름을 이미지로 나타낸 공간입니다.
- 🔗 [클래스 다이어그램 보기](https://drive.google.com/file/d/1o0W2l0YttRRJY7rc2RdLTgCYaEf4euq0/view)

![Image](https://github.com/user-attachments/assets/cec7e186-38e2-4393-be67-88b96657d4d6)


---

## 🧾 ERD(Entity Relationship Diagram)
> 📌 MySQL 테이블 간 관계를 시각적으로 표현한 ERD입니다.

![Image](https://github.com/user-attachments/assets/e89a3a8c-07e6-4bca-8f5b-a03fbb143f53)

## 🔗 기타 링크
- 🔗 [Notion 포트폴리오 보기](https://scientific-monkey-6c4.notion.site/Team-WMS-1842e3ff65358188b9d3fa4ce72c1c0c?pvs=74)

---

## 🔧 개발 예정 (2차 프로젝트)

- 웹 기반 UI 및 기능 확장 (JSP or Spring)
- 카테고리 세분화
- 관리자 대시보드 및 통계 기능 추가

---

## 👥 팀원

| 이름 | 역할 |
|------|------|
| 김선민 | 입고 도메인 구현 |
| 김성준 | 출고 및 재고 처리 |
| 이동휘 | 관리자 기능 및 DB 쿼리 |
| 신민혁 | 전체 구조 설계, Validator/Controller 유틸, 흐름 설계 |

---

## 📝 Git & Commit 컨벤션

### 🔧 Git 사용 순서
```bash
git add .
git commit -m "#이슈번호 타입: 메시지"
git pull origin main
git push origin [브랜치명]
```

### 💬 Commit 메시지 규칙

| 타입 | 설명 |
|------|------|
| feat | 기능 추가 |
| fix | 버그 수정 |
| docs | 문서 수정 |
| style | 코드 포맷 변경 |
| refactor | 리팩토링 |
| test | 테스트 코드 |
| chore | 빌드 제외 잡일 |
| build | 빌드 설정 |
| ci | CI 관련 설정 |

**예시:**
```bash
git commit -m "feat: 입고 기능 추가 및 검증 로직 연결

입고 요청 등록 시 제품명 검증 로직 추가.
resolves: #12"
```

---

## 🔠 코드 컨벤션 요약

- **변수/함수명**: camelCase
- **클래스/생성자**: PascalCase
- **함수명**: 동사 + 명사 (ex: `getUserInfo`)
- **줄 깊이 제한**: tab depth 최대 4단계
- **주석 규칙**: `//` or `/** */`로 작성
- **함수 인자 제한**: 최대 3개

---

## 🗃 DB / 테이블 명명 규칙

- DB명: 소문자, 8자 이하
- 테이블: 소문자 단수형, 최대 3단어 (`user_info_tbl`)
- 컬럼: `snake_case`, 의미+접미사 (`product_id`, `user_name`)
