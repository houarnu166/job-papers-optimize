---
name: application-optimization
description: Tailor resumes, cover letters, portfolios, and application strategy to a target role while binding every tailored output to its actual source document and preserving that source's structure. Use for capability assessment, requirement matching, source diagnosis, block-level rewrite planning, Markdown application drafts, asset preservation, and change tracking.
---

# Application Optimization

## Required References

작업 전에 다음을 읽는다.

- `references/source-preservation-contract.md`
- `references/artifact-contract.md`

## Inputs

- 활성 주문, 승인된 candidate profile, evidence ledger
- `intake/material-inventory.md`, `intake/source-structure.md`
- `research/company-job-analysis.md`와 `source-ledger.md`
- 주문에 연결된 primary source와 supplemental 자료

프로필은 사실 근거로, primary source는 문서의 형식·목소리·구조 권위로 사용한다. 일반 회사 주문에서 모든 원시 경력 자료를 다시 intake하지 않는다.

## Source Gate

- `operation: tailor`인 각 deliverable은 읽을 수 있는 `source_id`와 연결되어야 한다.
- `source-structure.md`에는 해당 source의 모든 최상위 섹션과 주요 블록, 표, 목록, 이미지, 캡션, 순서가 있어야 한다.
- 둘 중 하나라도 없으면 Gate 1은 실패다. 프로필로 새 문서를 작성해 빈자리를 메우지 않는다.
- `operation: create`는 사용자가 새 문서 작성을 명시한 경우에만 사용하며, 이때도 `artifact-contract.md`의 분석·근거 절차는 유지한다.

## Truth And Identity

- 승인된 프로필의 `verified` 사실만 최종 문구에 사용한다.
- 주문 전용 supplemental 사실은 직접 검증됐을 때만 사용할 수 있고 영구 프로필을 변경하지 않는다.
- 고용주, 프로젝트, 도구, 수치, 수상, 도메인 경험을 만들지 않는다.
- 기존 후보자의 방향, 말투, 문장 밀도와 자기 정체성을 유지하고 강조점만 조정한다.
- 회사가 원하는 인재상을 그대로 따라 말하지 말고 후보자의 실제 경험이 자연스럽게 맞닿는 지점을 보여준다.

## Gated Workflow

1. **Capability assessment**: 고정 목차의 `capability-assessment.md`를 작성한다.
2. **Requirement mapping**: 공고의 주요 요구사항을 빠짐없이 `requirement-evidence-matrix.md`에 매핑한다.
3. **Matching strategy**: 포지셔닝, 메시지 우선순위, 키워드, 간격 대응, 문서별 적용 계획을 `matching-strategy.md`에 작성한다.
4. **Source diagnosis**: 요청 문서마다 원본 구조, 강점·약점, ATS/가독성, 보존·변경 계획을 분석한다.
5. **Block plan**: 원본 블록마다 `keep`, `rewrite`, `reorder-requested`, `remove-requested`, `add-requested` 중 하나를 지정하고 근거 ID와 이유를 기록한다.
6. **Draft**: 원본 블록 순서와 형식을 따라 요청된 Markdown 최종본을 작성한다. 일반적인 새 이력서·포트폴리오 템플릿으로 바꾸지 않는다.
7. **Structural diff**: source block과 output block을 1:1로 대조하고 모든 차이를 `change-log.md`에 기록한다.
8. **Submission package**: 최종 제출 파일, 선택 export, 보류 항목과 제출 전 확인사항을 `submission-package.md`에 정리한다.

Gate 3이 통과하기 전 최종 문구를 확정하지 않고, Gate 4의 structural diff가 끝나기 전 문서 작성을 완료 처리하지 않는다.

## Source Preservation

- 기본 `source-locked`에서는 제목 위계, 섹션 순서, 블록 경계, 문단 수, 목록·표 구조, 이미지 순서와 캡션을 유지한다.
- 문장 길이는 원래 블록과 레이아웃에 들어갈 수 있는 범위를 우선한다. 크게 늘어나는 경우 `change-log.md`에서 overflow 위험을 표시한다.
- 원본에 존재하는 모든 섹션을 결과물에 대응시킨다. 빈번하지 않거나 직무 관련성이 낮다는 이유만으로 삭제하지 않는다.
- 재배치나 삭제가 전략적으로 유리해도 사용자 승인이나 주문의 명시적 허용이 없으면 계획 문서에서 제안만 하고 최종본에는 적용하지 않는다.
- 포트폴리오 이미지는 원본 순서, 프로젝트 연결, 캡션과 비율을 유지한다. 이미지 없이 텍스트 케이스 스터디로 대체하지 않는다.
- JSON은 키·중첩·배열 구조를, HTML은 의미 구조와 자산 연결을 유지한다.

## Final Copy Rules

- 최종 제출 문서에는 evidence ID, source ID, 인용 표식, 내부 주석, 분석 메모를 넣지 않는다.
- evidence ID는 requirement matrix, 문서별 분석서와 change log에서 최종 문장 또는 블록과 연결한다.
- 회사명은 자기소개서에서 자연스럽게 사용하고 이력서·포트폴리오에서 불필요하게 반복하지 않는다.
- ATS 키워드는 자연스럽게 사용하고 실제 경험이 없는 키워드를 경력처럼 삽입하지 않는다.
- 지원하지 않은 변경은 계획 문서에서 `사용자 확인 필요`로 남기고 최종 문구에 넣지 않는다.

## Gate 4 Completion

- 요청 문서별 분석·계획과 최종본이 존재한다.
- 모든 `tailor` 최종본이 source structure에 대응한다.
- 변경 이력에 source block, output block, 변경 유형, 이유, evidence ID, 승인 상태가 있다.
- 내부 표식이 최종 제출 문서에 없다.
- 필수 사실과 수치가 verified evidence에 연결된다.
