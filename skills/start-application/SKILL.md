---
name: start-application
description: Enter stage 5 for a posting that passed triage — create the internal order under the posting output folder, bind each tailored document to its master or submitted source, validate the profile and package versions, and route the gated research, tailoring, export and review work. Use when the user is ready to apply to a specific company, resumes an existing posting order, or asks to tailor materials for a posting. Never ask the user to author YAML or run setup commands.
---

# Start Application

라이프사이클 5단계의 진입점이다. 90% 마스터에서 기업별 10%만 바꿔 제출한다. 사용자는 파일과 목표를 제공하고 주문 파일과 실행 상태는 에이전트가 관리한다.

작업 전에 `references/intake-and-worklog-contract.md`를 읽는다.

## Preconditions

1. `pipeline/triage/{posting_id}.md`의 판정이 `Go` 또는 `조건부 Go`다. 판정이 없으면 `opportunity-triage`를 먼저 실행한다.
2. `package/master/`에 필요한 마스터가 있다. 없으면 `ready-package`로 돌아간다. 마스터 없이 원본에서 매번 새로 만드는 방식은 이 환경의 운영 방식이 아니다.
3. 승인된 프로필이 있다. 없으면 `candidate-profile`의 Initialize로 전환한다.
4. 사용자가 마스터 대신 특정 제출 원본을 쓰라고 지정하면 그 문서를 source로 쓰고 이유를 주문에 기록한다.

## Intake

대화와 첨부 자료에서 다음을 파악한다.

- 회사, 직무, 지원 단계, 마감일, 목표 제출일
- 채용공고 원문 위치(`pipeline/postings/{posting_id}.md`)
- 원하는 결과물과 면접·과제 범위
- 각 결과물의 source가 마스터인지 특정 제출 원본인지
- 출력 형식, 보존 강도, 언어, 톤, 길이, 제출 조건
- 이번 주문에만 사용할 추가 근거 자료

기본값:

- `research_depth: standard`
- `operation: tailor`, `source_id`는 해당 마스터
- `format: md`, `preservation: source-locked`
- `language: ko`, `tone: professional-natural`
- `constraints.optimization.wording|emphasis|reorder_within_section|resequence_repeated_units: allowed`
- `constraints.optimization.structural_redesign|add_or_remove_content_blocks: require-user-approval`
- `package.variant`: triage에서 정한 직무축
- `interview.scope: full` when interview preparation is requested without a narrower scope

## Material Binding

1. 각 주요 문서에 안정적인 `source_id`를 부여한다. 예: `master-resume`, `master-portfolio`, `submitted-resume`.
2. `materials.primary`에 `id`, `role`, `path`, `authority: source`를 기록한다.
3. 각 `tailor` deliverable의 `source_id`가 올바른 문서를 가리키게 한다.
4. 대화 첨부 파일에 안정적인 경로가 없으면 파일명과 대화 시점을 기록하고 첫 읽기에서 내용·구조 스냅샷을 `intake/`에 남긴다.
5. 원본이 없거나 읽히지 않으면 해당 작업을 `needs-user`로 두고 목적에 맞는 대체 형식을 요청한다. 사용자가 새 문서 작성을 명시하기 전 `create`로 바꾸지 않는다.

## Create Internal Order

1. `outputs/{output_slug}/order.md`를 만든다. `output_slug`는 회사명과 직무명을 사람이 읽기 쉬운 형태로 만들고 경로 구분자와 위험한 문자를 제거한다.
2. `order_id`는 회사, 직무, 날짜를 구분할 수 있게 만들고 기존 파일을 덮어쓰지 않는다.
3. `posting_id`로 `pipeline/postings/`의 공고와 연결한다.
4. `profile.version`과 `package.master_version`을 기록한다.
5. 충분한 정보와 모든 source binding이 있으면 `status: ready`, 없으면 `draft` 또는 `needs-user`로 둔다.
6. DOCX나 HTML 요청에도 승인 원본인 Markdown deliverable을 함께 계획한다. PDF는 deliverable 형식으로 두지 않는다.

주문 YAML은 내부 실행 기록이다. 사용자에게 YAML 편집이나 경로 선택을 맡기지 않는다.

## Preflight And Source Lock

주문 실행 전에 다음을 작성한다.

- `intake/preflight.md`: 프로필 버전, 마스터 버전, 주문, 런타임, 출력 위치
- `intake/material-inventory.md`: 모든 파일의 source ID, 역할, 형식, 가독 여부, 권위, 사용 목적
- `intake/source-structure.md`: 모든 `tailor` source의 페이지·섹션·블록·표·이미지·캡션 순서. source가 마스터면 `package/master/source-structure.md`를 인용하고 이번 주문의 대응표를 만든다.
- `worklog.md`: L5 체크포인트 표

L5.1이 통과하기 전에는 최종 초안을 쓰지 않는다.

## Route Work

- `company-research` → L5.2
- `application-optimization` → L5.3, L5.4
- `document-export` → DOCX 또는 HTML 요청이 있을 때만
- `quality-review` → L5.5
- `assignment-brief`, `interview-prep` → 6단계
- `pipeline-retro` → 결과 확정 후 7단계

범위가 분명한 요청(회사 조사만, 특정 문서만)은 해당 체크포인트만 실행하되 선행 체크포인트와 L5.5 검수는 유지한다.

## Conversation Rules

- 사용자가 개발 도구를 안다고 가정하지 않는다.
- 터미널, 런타임, 패키지 또는 플러그인 설치를 지시하지 않는다.
- 질문은 한 번에 핵심 1~3개로 제한한다.
- 읽을 수 없는 첨부 파일은 추측하지 말고 목적에 맞는 대체 형식 한두 개를 요청한다.
- 처리 가능한 자료와 단계부터 진행하고, 막힌 체크포인트와 필요한 사용자 응답을 명확히 구분한다.
- 최종 응답에는 생성된 결과물, 사용한 프로필·마스터 버전, 보존 결과와 남은 제한만 간결하게 알린다.

## Completion

- 활성 주문이 대화 내용과 triage 판정에 일치한다.
- 회사, 직무, 결과물, 출력 위치가 확정되어 있다.
- 모든 `tailor` 결과물에 실제 source가 연결됐다.
- 승인된 프로필과 마스터를 재사용했거나 정확한 선행 단계로 전환했다.
- 사용자가 주문 파일이나 실행 도구를 직접 다루지 않았다.
- L5 체크포인트와 최종 품질 검수가 실행되었다.
- `pipeline/application-log.md`의 해당 행이 제출 상태로 갱신됐다.
