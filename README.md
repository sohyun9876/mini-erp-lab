# mini-erp-lab

> ERP 도메인 학습 + 직접 구현해보는 스터디 레포

ERP/SAP 이직을 목표로, 이론 학습과 실제 구현을 병행합니다.
`study/`에서 개념을 정리하고, `mini-erp/`에서 코드로 구현합니다.

---

## 배경

- 현 직무: 중견기업 개발팀 2년차 (기획·POC 개발 → 외주 인계, 기능 테스트)
- 목표: ERP/SAP 직군 이직
- 전략: SAP 직행 대신 ERP 도메인 이해를 먼저 쌓고, 이후 SAP로 전환

---

## 폴더 구조

```
mini-erp-lab/
├── study/                        # ERP 이론 & 도메인 학습 정리
│   ├── 01-erp-basics/           # ERP 개요, 역사, 핵심 개념
│   ├── 02-domain/               # 도메인별 학습 노트
│   │   ├── accounting/         # 회계 (전표, 원장, 재무제표)
│   │   ├── hr/                 # 인사/급여
│   │   ├── inventory/          # 재고/물류 (입출고, 실사)
│   │   ├── procurement/        # 구매/발주
│   │   └── sales/              # 영업/수주
│   ├── 03-process-flows/        # 업무 프로세스 흐름도 정리
│   └── 04-sap-notes/           # SAP 전환 시 활용할 학습 노트
│
└── mini-erp/                     # 실제 구현 프로젝트
    ├── docs/                     # 설계 문서
    │   ├── erd/                 # 데이터베이스 ERD
    │   ├── api/                 # API 명세
    │   └── wireframes/          # 화면 설계
    ├── backend/                  # Java Spring Boot 백엔드
    │   └── src/
    │       ├── main/java/com/minierp/
    │       │   ├── common/      # 인증, 공통 유틸, 예외 처리
    │       │   ├── master/      # 마스터 데이터 (사용자, 조직, 거래처)
    │       │   ├── accounting/  # 회계 모듈
    │       │   ├── hr/          # 인사 모듈
    │       │   ├── inventory/   # 재고 모듈
    │       │   ├── procurement/ # 구매 모듈
    │       │   └── sales/       # 영업 모듈
    │       ├── main/resources/
    │       │   └── mapper/      # MyBatis XML 매퍼
    │       └── test/            # 테스트 코드
    ├── frontend/                 # React 프론트엔드
    │   └── src/
    │       ├── components/      # 공통 컴포넌트
    │       ├── pages/           # 모듈별 페이지
    │       ├── store/           # 상태 관리
    │       └── api/             # API 클라이언트
    └── scripts/                  # DB 초기화, seed 데이터 스크립트
```

---

## Tech Stack

| 영역 | 기술 |
|------|------|
| Frontend | React, TypeScript, Tailwind CSS |
| Backend | Java, Spring Boot |
| Database | Oracle SQL |
| DB Mapper | MyBatis |
| Infra | Docker, GitHub Actions |
| Docs | Swagger |

---

## Roadmap

### Phase 1 — ERP 기초 & 마스터 데이터 (진행 중)
- [ ] ERP 개요 및 모듈 구조 학습 (`study/01-erp-basics/`)
- [ ] 핵심 비즈니스 프로세스 흐름 정리 (`study/03-process-flows/`)
- [ ] 사용자 / 조직 / 거래처 마스터 데이터 설계 및 구현
- [ ] 공통 코드 관리, 인증/권한 구조 구축

### Phase 2 — 핵심 모듈 구현
- [ ] **인사/급여**: 사원 관리, 부서 배치, 급여 정산 로직
- [ ] **재고/물류**: 입출고 처리, 재고 실사, 로케이션 관리
- [ ] **구매**: 발주 → 입고 → 매입 전표 흐름
- [ ] **영업**: 수주 → 출고 → 매출 전표 흐름
- [ ] **회계**: 전표 입력, 원장, 기본 재무제표

### Phase 3 — 고도화
- [ ] 모듈 간 연계 흐름 완성 (구매 입고 → 재고 자동 반영 → 회계 전표 생성)
- [ ] 데이터 시각화 대시보드
- [ ] 엑셀 업로드/다운로드 (대량 데이터 처리)
- [ ] SAP 학습 노트 연계 (`study/04-sap-notes/`)

---

## 학습 방향

ERP의 핵심은 **부서 간 데이터 통합**입니다.
단순히 CRUD를 구현하는 것이 아니라, 아래 흐름이 코드 레벨에서 연결되는 것을 목표로 합니다.

```
구매 발주 → 입고 처리 → 재고 증가 → 매입 전표 자동 생성 → 원장 반영
영업 수주 → 출고 처리 → 재고 감소 → 매출 전표 자동 생성 → 원장 반영
```

각 모듈을 독립적으로 구현하되, 연계 시점에서 **트랜잭션 무결성**을 보장하는 구조를 설계합니다.
