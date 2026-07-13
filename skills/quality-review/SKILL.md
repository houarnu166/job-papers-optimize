---
name: quality-review
description: Independently review company-specific research, application, interview, Markdown, DOCX, and HTML outputs against their fixed artifact contracts and actual source documents. Use as the final gate and after remediation to verify profile integrity, evidence, truthfulness, source fidelity, format completeness, ATS readability, assets, and submission readiness.
---

# Quality Review

## Required Reference

작업 전에 `references/review-contract.md`를 읽는다. 이전 단계의 PASS 선언이나 worklog 요약을 검증 증거로 대신 사용하지 않는다.

## Inputs

- 활성 주문, `worklog.md`, `source-ledger.md`
- 승인된 profile과 evidence ledger
- `intake/material-inventory.md`와 `tailor` 작업이 있을 때 `source-structure.md`
- 모든 research, application, interview, export 산출물
- 실제 primary source 문서와 최종 결과물

검수 결과는 `outputs/{output_slug}/review/quality-review.md`에만 작성한다. 수정은 해당 소유 스킬로 돌려보낸다.

## Independent Review Sequence

1. 주문의 deliverable, operation, source binding, preservation과 scope를 다시 읽는다.
2. 실제 파일 존재와 worklog gate 증거를 확인한다.
3. 각 source를 직접 읽고 source structure가 정확한지 표본이 아니라 전체 최상위 구조 기준으로 확인한다.
4. source와 최종 결과를 블록 순서, 섹션 수, 표·목록·이미지·캡션 기준으로 비교한다.
5. 회사 조사와 면접 자료를 각각의 report contract와 대조한다.
6. 최종 제출 문장의 사실과 수치를 evidence ledger에 역추적한다.
7. findings를 심각도순으로 기록하고 verdict를 마지막에 결정한다.

## Mandatory Checks

- **Profile integrity**: 실행 시 사용한 profile version과 가능한 경우 hash가 일치한다.
- **Evidence and truth**: 중요한 주장과 수치가 verified evidence에 연결되고 상충·미검증 사실이 최종 문구에 없다.
- **Source binding**: 모든 `tailor` deliverable에 실제 source ID가 있고 source가 읽힌다.
- **Source fidelity**: 제목 위계, 섹션·블록 순서, 문단 경계, 목록, 표, 이미지, 캡션이 preservation 규칙과 일치한다.
- **Unauthorized changes**: 삭제, 추가, 병합, 분할, 재배치가 change log의 이유와 승인 상태 없이 적용되지 않았다.
- **Research contract**: 모든 조사 분야의 순차 coverage와 상태, research plan, posting snapshot, source ledger와 고정 보고서 목차가 있고 사실·해석·미확인이 분리됐다.
- **Interview contract**: scope별 카테고리, 최소 질문 수, 질문별 8개 필드, 위험 질문, 역질문, 체크리스트가 있다.
- **Requirement coverage**: 모든 요청 산출물과 주요 직무 요구사항을 다뤘다.
- **Cross-document consistency**: resume, cover letter, portfolio, interview가 같은 사실과 포지셔닝을 사용한다.
- **Submission cleanliness**: 최종 제출 문서에 `EV-`, `SRC-`, TODO, `확인 필요`, 내부 지시, source-page 표식이 없다.
- **Company-name discipline**: resume와 portfolio에서 목표 회사명을 불필요하게 반복하지 않는다.
- **ATS and readability**: 원본 틀 안에서 표준 제목, 읽기 순서, 텍스트 접근성, 자연스러운 키워드를 유지한다.
- **Identity details**: 날짜, 직무명, 연락처, 링크가 원본 및 문서 간 일치한다.
- **Assets**: 이미지 경로, 프로젝트 연결, 캡션, 순서와 비율이 보존된다.
- **DOCX/HTML**: 요청 시 구조 QA와 지원 가능한 시각 QA 결과가 기록되고 내용이 승인 Markdown과 같다.
- **Output isolation**: 최종 파일이 주문 폴더 밖에 없고 PDF 출력이 없다.

## Severity

- `Blocker`: 허위 사실, 잘못된 target, 읽히지 않는 핵심 결과물, `tailor` 원본 미연결, 원본 미열람, `tailor` 구조 명세 없음, 핵심 개인 정보 오류, PDF 출력.
- `Major`: 원본 구조의 무단 변경, 중요 섹션·표·이미지 누락, 회사 조사 고정 섹션 누락, 면접 scope·질문 계약 미충족, unsupported claim, 중요 요구사항 공백, 내부 표식 노출.
- `Minor`: 제출을 막지 않는 표현·정렬·가벼운 형식 문제.

선택 export가 불가능하지만 승인 Markdown과 제한 기록이 완전하면 Blocker가 아니다. 생성하지 않은 DOCX나 HTML을 검수했다고 표시하지 않는다.

## Verdict And Loop

`quality-review.md`는 `Findings -> Gate Evidence -> Contract Coverage -> Source Fidelity -> Evidence And Truth -> Submission Checks -> Verdict -> Fix List` 순서로 작성한다.

- `PASS`: Blocker 0, Major 0이고 모든 실행 대상 gate가 실제 증거로 통과했다.
- `FAIL-REMEDIATE`: 수정 가능한 Blocker 또는 Major가 있다.
- `NEEDS-USER`: 사실 확인, 원본 제공 또는 변경 승인 없이는 해결할 수 없다.

수정 가능한 문제는 소유 스킬로 돌리고 최대 2회 재검수한다. 검수 문구를 완화해 통과시키지 않는다. Blocker가 남으면 주문을 complete로 표시하지 않는다.
