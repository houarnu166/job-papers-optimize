# Application Artifact Contract

회사별 지원 문서를 만들기 전에 필요한 분석과 계획 산출물의 고정 목차다. 요청하지 않은 제출 문서를 억지로 만들 필요는 없지만 내부 전략 문서는 아래 계약을 따른다.

## Capability Assessment

`application/capability-assessment.md` 목차:

1. 경력 요약과 현재 포지셔닝
2. 핵심 역량 인벤토리
3. 도메인·플랫폼·사용자 경험 맵
4. 방법론·도구·협업 경험
5. 검증된 성과와 임팩트
6. 강점과 차별화 요소
7. 간격, 상충 정보와 과장 금지 영역
8. 재사용 가능한 면접 story bank

각 사실성 항목은 evidence ID와 상태를 표시한다. `candidate`와 `conflict`는 최종 문구 후보로 사용하지 않는다.

## Requirement-Evidence Matrix

`application/requirement-evidence-matrix.md` 표:

| ID | 공고 원문 | 유형 | 중요도 | 평가 행동 | 지원자 근거 | Evidence ID | 적합도 | 문서 적용 | 면접 검증 | Gap 대응 |
|---|---|---|---|---|---|---|---|---|---|---|

- 공고의 주요 업무, 필수, 우대 요건을 빠짐없이 행으로 만든다.
- 근거가 없으면 빈칸 대신 `검증된 근거 없음`이라고 쓴다.
- 공고 키워드와 실제 수행 경험을 구분한다.

## Matching Strategy

`application/matching-strategy.md` 목차:

1. 한 문장 포지셔닝
2. 채용 담당자가 기억해야 할 메시지 3개
3. 요구사항 우선순위와 근거 선택
4. 핵심·보조 키워드와 사용 경계
5. 문서별 적용 전략
6. 간격과 위험 대응
7. 자연스러움·회사명·톤 가이드
8. 제출 문서와 면접의 일관성 기준

## Resume Analysis

Resume가 요청되면 `application/resume-analysis.md`를 작성한다.

1. Source ID와 원본 형식
2. 현재 제목·섹션·경력 항목 순서
3. 원본의 강점과 약점
4. ATS와 읽기 순서 진단
5. 블록별 keep/rewrite 계획
6. 키워드 적용 위치
7. 길이와 레이아웃 위험
8. 승인 없이는 적용하지 않을 구조 변경 제안

## Cover Letter Plan

Cover letter가 요청되면 `application/cover-letter-plan.md`를 작성한다.

1. Source ID와 원본 문단 구조
2. 지원 동기 후보와 선택 근거
3. 전체 내러티브
4. 문단별 역할과 근거
5. 회사명 사용 위치
6. 톤과 글자 수 배분
7. 블록별 keep/rewrite 계획
8. 확인이 필요한 개인 동기

원본 문단 수와 순서를 유지한다. 원본이 없는 새 작성은 `operation: create`여야 한다.

## Portfolio Plan

Portfolio가 요청되면 `application/portfolio-plan.md`를 작성한다.

1. Source ID, 페이지·최상위 구조와 자산 현황
2. Cover와 introduction 진단
3. 프로젝트별 관련성·강점·위험 매트릭스
4. 프로젝트별 기존 storytelling 패턴
5. 페이지·블록별 keep/rewrite 계획
6. 이미지·캡션·순서 보존 계획
7. Closing과 개인 브랜딩 일관성
8. 승인 없이는 적용하지 않을 재배치·삭제 제안

프로젝트 우선순위를 바꾸는 것이 전략적으로 좋아도 source-locked에서는 제안만 하고 자동 적용하지 않는다.

## Final Documents

- 최종 파일은 원본의 첫 블록부터 마지막 블록까지 같은 순서로 대응시킨다.
- 내부 근거 태그는 제거한다.
- 원본의 연락처·링크·날짜를 임의로 보정하지 않고 상충 시 사용자 확인을 요청한다.
- Markdown 변환에서도 원본의 블록 경계, 표와 이미지 위치를 최대한 직접적으로 표현한다.
- 새로 만든 generic `Profile`, `Core Capabilities`, `Case 1` 구조는 원본에 같은 역할의 블록이 있거나 redesign/create가 승인된 경우에만 허용한다.

## Submission Package

`application/submission-package.md` 목차:

1. 요청 산출물과 전달 파일
2. 각 파일의 source ID와 preservation 결과
3. 주요 최적화 요약
4. 적용하지 않은 구조 변경 제안
5. 선택 export와 QA 상태
6. 제출 전 사용자 확인사항
7. 면접 준비로 넘길 핵심 메시지
