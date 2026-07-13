# Intake And Worklog Contract

회사별 작업의 시작 상태와 순차 진행을 파일로 확인하기 위한 계약이다.

## Preflight Format

`intake/preflight.md` 목차:

1. Active Order
   - order path, order ID, status, mode
   - target company, product, role, stage, deadline
   - output slug and collision check
2. Profile
   - profile path, profile ID, requested version, actual version
   - updated_at, hash or hash limitation
   - evidence ledger and source map status
3. Requested Deliverables
   - type, operation, source ID, format, preservation
4. Runtime Capabilities
   - readable input formats
   - web research availability
   - DOCX/HTML export availability
   - visual preview availability
5. Input And Source Gate
   - primary source readability
   - supplemental readability
   - missing or ambiguous authority source
6. Decision
   - ready, needs-user or blocked
   - applied defaults and their reasons

Preflight는 `source-locked`를 실제 검증하기 전 보존 성공을 선언하지 않는다.

## Worklog Header

`worklog.md` 상단에는 다음을 둔다.

- Order ID and order path
- Target and mode
- Profile ID, version, updated_at and hash status
- Research depth
- Requested formats and preservation
- Started at and last updated at
- Current overall status

## Gate Table

```markdown
| Phase | Status | Required artifacts | Gate result | Notes |
|---|---|---|---|---|
| Gate 0 - Profile And Order | in-progress | active order, preflight | pending | |
| Gate 1 - Source Lock | pending | material inventory, source structure | pending | |
| Gate 2 - Research | pending | research plan, posting, report, source ledger | pending | |
| Gate 3 - Matching Strategy | pending | capability, requirement matrix, company-signal matrix, strategy | pending | |
| Gate 4 - Application Drafts | pending | document plans, drafts, change log, package | pending | |
| Gate 5 - Interview | pending | interview plan, interview prep | pending | |
| Gate 6 - Independent Review | pending | quality review | pending | |
```

허용 상태: `pending`, `in-progress`, `passed`, `needs-user`, `blocked`.

- 현재 실행 단계만 `in-progress`로 둔다.
- artifact가 실제로 존재하고 계약을 충족한 후 `passed`로 바꾼다.
- 실행 범위 밖인 단계는 Notes에 `not requested`와 주문 근거를 남기고 Gate result를 `passed`로 둘 수 있다.
- 선행 gate가 실패했는데 후속 gate를 passed로 두지 않는다.

## Execution Log

Gate table 아래에 append-only 실행 로그를 둔다.

| Time | Phase | Action | Inputs | Outputs | Decision or limitation |
|---|---|---|---|---|---|

중요한 기본값, 사용자 승인, 구조 변경 승인, 조사 한계, remediation을 기록한다. 내부 사고 과정을 장황하게 기록하지 않고 재개와 검수에 필요한 결정만 남긴다.

## Job Posting Snapshot

`research/job-posting.md` 형식:

1. Target metadata: company, role, source, captured at, deadline
2. Submission rules
3. Full posting text or complete provided excerpt
4. Posting sections: responsibilities, required, preferred, process, benefits
5. Missing or inaccessible parts

공고 문구와 에이전트 해석을 섞지 않는다. 해석은 company report에 둔다.
