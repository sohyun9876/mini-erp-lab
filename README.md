# 📁 mini-erp-core

> **ERP의 핵심 프로세스 학습 및 비즈니스 로직 구현 프로젝트**
>
> 단순히 기능을 개발하는 것을 넘어, 기업의 자원 관리 흐름(Flow)을 깊이 있게 이해하고 데이터 무결성을 보장하는 시스템을 설계하는 것을 목표로 합니다.

---

## 🎯 Project Goals
* **ERP 비즈니스 도메인 이해**: 회계, 인사, 물류 등 복합적인 비즈니스 로직 학습
* **DB 정규화 및 설계**: 복잡한 관계형 데이터베이스 구조 설계 역량 강화
* **확장 가능한 아키텍처**: 기능 모듈화(Modularization)를 통한 유지보수 용이성 확보

## 🛠 Tech Stack
* **Frontend**: React / TypeScript / Tailwind CSS
* **Backend**: Node.js (NestJS)
* **Database**: PostgreSQL
* **Tools**: GitHub Actions, Docker, Swagger
*(※ 본인이 사용하는 스택에 맞춰 수정하세요)*

---

## 🗓 Roadmap & Progress
학습과 개발 단계를 나누어 관리합니다.

### Phase 1: 기초 설계 및 공통 모듈 (진행 중 🏃)
- [ ] ERP 도메인 기초 이론 학습 및 정리
- [ ] 마스터 데이터(사용자, 권한, 거래처) 테이블 설계
- [ ] 공통 코드 관리 시스템 구축

### Phase 2: 핵심 모듈 개발 (대기 🗓)
- [ ] **인사/급여**: 사원 관리 및 급여 정산 로직
- [ ] **재고/물류**: 입출고 관리 및 재고 실사 프로세스
- [ ] **회계**: 전표 입력 및 기본 재무제표 생성

### Phase 3: 고도화 (대기 🗓)
- [ ] 데이터 시각화 대시보드
- [ ] 엑셀 업로드/다운로드 대량 데이터 처리

---

## 📂 Project Structure
```text
/docs            # ERP 이론 및 프로세스 분석 문서
/src             # 프로젝트 소스 코드
  ├── backend    # Server-side logic
  └── frontend   # Client-side UI
/research        # 벤치마킹 및 기술 스택 리서치