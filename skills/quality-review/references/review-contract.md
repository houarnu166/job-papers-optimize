# Quality Review Contract

최종 검수는 작성자의 자신감이나 이전 PASS 문구가 아니라 실제 원본과 산출물 증거로 판정한다.

## Review Report Order

`review/quality-review.md`는 다음 순서를 사용한다.

1. Findings
2. Gate Evidence
3. Deliverable And Contract Coverage
4. Source Fidelity
5. Evidence And Truth
6. Cross-Document Consistency
7. Submission And Format Checks
8. Verdict
9. Fix List And Remediation History

Findings가 없더라도 `명시적 findings 없음`과 남은 검수 한계를 먼저 쓴다. Verdict를 문서 첫 줄에 두지 않는다.

## Gate Evidence Table

| Gate | Required evidence | Actual file or observation | Result | Finding ID |
|---|---|---|---|---|

실행 범위 밖인 gate는 `not requested`와 주문 근거를 쓴다. 단순히 worklog가 passed라고 적혀 있다는 이유로 통과시키지 않는다.

## Deliverable Coverage Table

| Deliverable | Operation | Source ID | Preservation | Required contract | Output | Result |
|---|---|---|---|---|---|---|

`tailor`인데 Source ID가 없거나 source를 열 수 없으면 즉시 Blocker다.

## Source Fidelity Table

문서별로 다음을 기록한다.

| Check | Source | Output | Approved deviation | Result |
|---|---:|---:|---|---|
| Top-level sections | | | | |
| Ordered blocks | | | | |
| Paragraph/list boundaries | | | | |
| Tables | | | | |
| Images and captions | | | | |
| Reordered blocks | | | | |
| Added/removed blocks | | | | |

모든 source-locked 문서에 대해 `Unapproved deviations: 0`인지 확인한다. 전체 구조 비교 없이 “대체로 보존”이라고 판정하지 않는다.

## Contract Checks

### Company Research

- research plan 1~6 항목
- source coverage 8개 분야의 순서, 확인 범위와 상태
- posting snapshot
- source ledger 필수 열과 source ID
- final report 1~9장
- 필수 요구사항, 우대사항, 경쟁 제품, 요구사항-근거 표
- 사실·해석·미확인 구분

### Application

- capability assessment 1~8장
- 공고의 주요 요건이 모두 있는 requirement matrix
- matching strategy 1~8장
- 요청 문서별 분석·계획
- 최종 문서와 block-level change log
- submission package

### Interview

- interview plan 1~10장
- scope별 최소 질문 수
- 질문마다 8개 필드
- 포트폴리오·경력 검증, 공통·위험 질문
- 역질문 5개 이상과 질문별 의도
- 최종 체크리스트

## Submission Cleanliness Search

최종 제출용 파일에서 다음 표식을 확인한다.

- `EV-` 또는 `SRC-`
- `TODO`, `TBD`, `FIXME`
- `확인 필요`, `사용자 답변 필요`
- `source-page`, `source block`, `internal note`
- 빈 placeholder와 예시 문구

하나라도 사용자에게 그대로 제출될 수 있는 본문에 남으면 Major다. Interview preparation과 내부 분석 문서에는 evidence ID를 사용할 수 있다.

## Required Failure Decisions

| Condition | Minimum severity |
|---|---|
| Tailored document has no source binding | Blocker |
| Tailor source was not read or its structure map is absent | Blocker |
| Candidate profile was used as a replacement template | Blocker |
| False employer, role, project, metric or method | Blocker |
| Generic new resume/portfolio structure replaced the source | Major |
| Source section, table, image or caption missing without approval | Major |
| Research fixed section or required table missing | Major |
| Interview scope or question-unit contract incomplete | Major |
| Internal evidence tags leaked into submission copy | Major |
| Optional DOCX unavailable with complete Markdown fallback | Not a failure by itself |
| Unknown company information explicitly marked unknown | Not a failure by itself |

## Verdict Rules

- `PASS`: Blocker 0, Major 0, all applicable gate evidence independently verified.
- `FAIL-REMEDIATE`: at least one fixable Blocker or Major.
- `NEEDS-USER`: source, fact, personal answer or structural change approval is required.

Minor findings can remain with a PASS only when they do not change truth, source fidelity, required format or submission readiness.

## Remediation History

| Cycle | Finding IDs | Owning skill | Fix made | Recheck result |
|---:|---|---|---|---|

최대 2회 후에도 Blocker가 있으면 주문 상태를 complete로 바꾸지 않는다.
