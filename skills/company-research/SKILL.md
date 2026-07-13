---
name: company-research
description: Perform a staged, source-backed analysis of a target company, product, market, organization, and role, then write the fixed-format research report required by later application and interview stages. Use for company, product, design organization, hiring role, culture, market, competitor, interview context, or job-posting analysis under a company-specific output folder.
---

# Company Research

## Required Reference

작업 전에 `references/report-contract.md`를 읽고 고정 목차와 깊이별 기준을 적용한다.

## Inputs

- 정확한 활성 주문, 회사 식별 정보, 채용공고
- 승인된 프로필 버전. 후보자 적합성 분석에만 사용하고 회사 사실의 출처로 사용하지 않는다.
- `intake/preflight.md`, `material-inventory.md`
- 기존 회사 자료가 supplemental로 제공되었다면 해당 source ID

`outputs/{output_slug}/research/`와 공용 `source-ledger.md`, `worklog.md`만 갱신한다.

## Staged Workflow

1. **Target lock**: 동명 회사, 제품, 법인, 국가, 직무, 채용 단계와 공고 원문을 확정한다. 공고는 `research/job-posting.md`에 보존한다.
2. **Research plan**: 보고서의 필수 섹션별 질문, 우선 출처, 검색 범위, 완료 기준을 `research/research-plan.md`에 작성한다.
3. **Company and product**: 기업 개요, 사업 모델, 고객, 주요 제품, 수익 또는 운영 구조, 최근 변화를 조사한다.
4. **Role microanalysis**: 책임, 필수·우대 요건, 산출물, 협업 대상, 평가 신호, 암시 요건을 공고 문구와 분리해 해석한다.
5. **Organization and work context**: 공식 근거가 있을 때 문화, 가치, 제품·디자인 조직, 프로세스와 도구를 조사한다. 찾지 못한 정보는 확인되지 않았다고 쓴다.
6. **Market and recent context**: 표준 조사는 직무 판단에 필요한 시장·경쟁·최근 변화만, 심화 조사는 경쟁 구도·재무/투자·후기 신호까지 확장한다.
7. **Candidate strategy**: 요구사항과 승인된 근거를 연결해 기회, 간격, 위험, 검증 질문과 지원 전략을 도출한다.
8. **Report gate**: `references/report-contract.md`의 모든 섹션, 표와 source ID를 확인한 뒤 Gate 2를 통과시킨다.

단계를 건너뛰었다면 `research-plan.md`와 보고서에 이유를 남긴다. 자료가 없다는 이유로 고정 섹션 자체를 삭제하지 않는다.

## Sources And Evidence

공식 채용공고, 회사·제품 사이트, 공시·투자자 자료, 공식 블로그와 발표를 우선한다. 보도자료와 신뢰할 수 있는 기사로 교차 확인한다. 후기와 익명 커뮤니티는 조직 내부의 확정 사실이 아니라 관찰 신호로만 사용한다.

- 외부 출처마다 `SRC-####`를 부여한다.
- `source-ledger.md`에 제목, 발행 주체, URL 또는 파일 경로, 발행일, 접속일, 사용 섹션, 신뢰도와 한계를 기록한다.
- 조사 보고서의 외부 사실에는 가까운 위치에 source ID를 둔다.
- `확인된 사실`, `합리적 해석`, `확인되지 않음`을 문장 수준에서 구분한다.
- 출처가 없는 점수, 직원 수, 매출, 팀 규모, 프로세스, 연봉, 시장점유율을 채우지 않는다.

웹 조사 기능이 없으면 설치나 설정을 요구하지 않는다. 제공된 공고와 회사 자료만 사용하고 조사 범위 제한을 기록한다. 핵심 판단에 꼭 필요한 경우에만 공식 페이지 내용이나 링크 제공을 요청한다.

## Gate 2 Completion

- `research-plan.md`, `job-posting.md`, `company-job-analysis.md`, `source-ledger.md`가 존재한다.
- 보고서의 필수 목차와 요구사항 매트릭스가 완성됐다.
- 주요 회사·직무 주장에 source ID가 있다.
- 사실, 해석, 미확인이 분리됐다.
- 후속 application과 interview 단계가 바로 사용할 수 있는 전략과 검증 질문이 있다.
