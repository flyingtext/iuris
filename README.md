# Iuris

**Open Source Risk Management for Data Rights**  
라틴어 *iuris* = 법, 권리.  
전 세계 성문헌법·민법·형법·특별법 조문을 통합 DB로 구축하는 프로젝트.

---

## 목표
- 193개국 성문헌법·민법·형법·특별법 조문 통합 DB
- 권리–의무–구제 구조 데이터화
- 검색 및 리스크 매니지먼트 지원

---

## 기능
1. 국가별 법령 크롤링 및 원문 저장
2. 검색/색인 (FTS5, ElasticSearch)
3. 행위자별 권리–의무 매핑
4. 권리 침해 리스크 분석 및 예상 손해액 산정
5. 최적화 전략 추천 (Expected Damage Minimization)

---

## 아키텍처
```text
사용자 브라우저
     │
     ▼
Web Frontend (Django/FastAPI)
     │
     ▼
Application Layer
  - 국가 리스트 관리
  - 조문 검색 컨트롤러
  - 리스크 매니지먼트 모듈
     │
     ▼
Data Processing Backend
  - 크롤링 모듈 (law.go.kr, EUR-Lex, govinfo 등)
  - 정규화/파싱
  - 메타데이터 추출
     │
     ▼
Search Engine
  - SQLite FTS5 (소규모)
  - ElasticSearch (대규모)
     │
     ▼
Storage Layer
  - PostgreSQL/DuckDB
  - Parquet/JSON 아카이브
````

---

## 개발 원칙

* 언어: Python 단일 스택
* 라이선스: BSD 2-Clause 또는 ISC
* 출처 강제: 모든 데이터/보고서에 법령 원문 시테이션 포함
* 모듈화: 국가별 크롤러 플러그인 구조
* 확장성: 1TB급 텍스트 DB 처리 가능

---

## 로드맵

* **MVP (0.1)**: 10개국 법령 크롤링 + 검색 인터페이스
* **v0.5**: 50개국 확장 + 리스크 매니지먼트 모듈 1차 완성
* **v1.0**: 193개국 DB 1TB 구축 + 권리/의무 매핑 전수 + 리스크 보고서 자동화

---

## 인용

> *“Remedium iuris” — 로마법에서 이미 권리와 구제는 불가분이었다.*
> — William Blackstone, *Commentaries on the Laws of England* (1765–1769)

---

## 저장소 구조

```text
iuris/
 ├─ crawler/        # 국가별 법령 크롤링 모듈
 ├─ parser/         # 법령 파싱/정규화
 ├─ risk/           # 권리/의무/리스크 매핑
 ├─ web/            # Django/FastAPI 프론트엔드
 ├─ db/             # DB 스키마 및 마이그레이션
 ├─ reports/        # JSON/Markdown 리포트
 └─ LICENSE
```

---

## 도메인

[iuris.info](https://iuris.info)

```
