---
name: start-application
description: Start a company or role application from natural-language conversation and attached materials, bind each requested tailored document to its actual source, create the internal order, validate the persistent profile, and route the gated research, application, interview, export, and review workflow. Use when the user shares a posting, asks to tailor materials, starts interview preparation, or resumes a company order. Never ask the user to author YAML or run setup commands.
---

# Start Application

자연어 대화를 회사별 지원 작업으로 변환하는 기본 진입점이다. 사용자는 파일과 목표를 제공하고 주문 파일과 실행 상태는 에이전트가 관리한다.

작업 전에 `references/intake-and-worklog-contract.md`를 읽는다.

## Intake

대화와 첨부 자료에서 다음을 파악한다.

- 회사, 직무, 지원 단계, 마감일
- 채용공고 URL, 본문 또는 첨부 파일
- 원하는 결과물과 면접 범위
- 각 결과물이 기존 문서의 최적화인지 새 문서 작성인지
- 기존 문서라면 실제 원본 파일과 문서 역할
- 출력 형식, 보존 강도, 언어, 톤, 길이, 제출 조건
- 이번 주문에만 사용할 추가 근거 자료

회사와 직무, 채용공고 또는 역할 설명, 원하는 결과물은 우선 확인한다. 기존 이력서·자기소개서·포트폴리오 최적화 요청에는 해당 원본이 필수다. 지원자 프로필만으로 원본 양식을 재현할 수 있다고 가정하지 않는다.

다음 기본값을 사용한다.

- `mode: linear`
- `research_depth: standard`
- `operation: tailor` when an existing document is being improved
- `format: md`
- `preservation: source-locked`
- `language: ko`
- `tone: professional-natural`
- `interview.scope: full` when interview preparation is requested without a narrower scope

## Material Binding

1. 읽을 수 있는 각 주요 문서에 안정적인 `source_id`를 부여한다. 예: `resume-source`, `portfolio-source`.
2. `materials.primary`에 `id`, `role`, `path`, `authority: source`를 기록한다.
3. 각 `tailor` deliverable의 `source_id`가 올바른 주요 문서를 가리키게 한다.
4. 대화 첨부 파일에 안정적인 경로가 없으면 파일명과 대화 시점을 기록하고, 첫 읽기에서 원문 내용과 구조 스냅샷을 `outputs/{output_slug}/intake/`에 남긴다.
5. 파일이 여러 개라 어느 것이 제출 원본인지 모호할 때만 짧게 확인한다.
6. 원본이 없거나 읽히지 않으면 `tailor` 작업을 `needs-user`로 두고 적절한 대체 형식을 요청한다. 사용자가 새 문서 작성을 원한다고 명시하기 전 `create`로 바꾸지 않는다.

## Profile Gate

1. `inputs/profile/candidate-profile.md`, `evidence-ledger.md`, `source-map.md`가 있으면 버전과 상태만 검증하고 재추출하지 않는다.
2. 승인된 프로필이 없으면 `candidate-profile`의 Initialize 모드로 전환하고 회사별 최종 문서 작성 전에 프로필 제안을 만든다.
3. 새 자료가 기존 프로필에 없는 사실을 포함하면 이번 주문의 supplemental evidence로만 사용한다.
4. 영구 반영이 필요하면 회사별 작업과 분리해 `candidate-profile`의 Update 모드를 제안한다.

## Create Internal Order

1. `orders/order-template.md`의 현재 필드를 사용해 고유한 주문 파일을 작성한다.
2. `order_id`는 회사, 직무, 날짜를 구분할 수 있게 만들고 기존 파일을 덮어쓰지 않는다.
3. `output_slug`는 회사명과 직무명을 사람이 읽기 쉬운 형태로 만들며 경로 구분자와 위험한 문자를 제거한다.
4. 충분한 정보와 모든 source binding이 있으면 `status: ready`, 핵심 정보가 없으면 `draft` 또는 `needs-user`로 둔다.
5. DOCX나 HTML 요청에도 승인 원본인 Markdown deliverable을 함께 계획한다.
6. PDF를 deliverable 형식으로 넣지 않는다.

주문 YAML은 내부 실행 기록이다. 사용자가 요청하지 않는 한 YAML 편집이나 주문 경로 선택을 사용자에게 맡기지 않는다.

## Preflight And Source Lock

주문 실행 전에 다음을 작성한다.

- `intake/preflight.md`: 프로필, 주문, 런타임, 출력 위치
- `intake/material-inventory.md`: 모든 파일의 source ID, 역할, 형식, 가독 여부, 권위, 사용 목적
- `intake/source-structure.md`: 모든 `tailor` 원본의 페이지·섹션·블록·표·이미지·캡션 순서
- `worklog.md`: Gate 0~6 체크포인트 표

`source-structure.md`는 `application-optimization`의 source preservation contract를 따른다. Gate 1이 통과하기 전에는 기존 문서의 최종 초안을 쓰지 않는다.

## Route Work

- 전체 지원 준비는 linear 모드로 Gate 0부터 순서대로 실행한다.
- 특정 문서 수정, 회사 조사만 수행, 면접 준비처럼 범위가 분명하면 flexible 모드를 사용할 수 있다.
- 유연 모드에서도 해당 산출물의 선행 게이트와 독립 품질 검수는 유지한다.
- DOCX 또는 HTML 요청이 있을 때만 `document-output`을 실행한다.
- 현재 런타임이 선택 출력 형식을 지원하지 않으면 설치를 요구하지 않고 Markdown fallback을 전달한다.

## Conversation Rules

- 사용자가 개발 도구를 안다고 가정하지 않는다.
- 터미널, 런타임, 패키지 또는 플러그인 설치를 지시하지 않는다.
- 질문은 한 번에 핵심 1~3개로 제한한다.
- 읽을 수 없는 첨부 파일은 추측하지 말고 목적에 맞는 대체 형식 한두 개를 요청한다.
- 처리 가능한 자료와 단계부터 진행하고, 막힌 게이트와 필요한 사용자 응답을 명확히 구분한다.
- 최종 응답에는 생성된 결과물, 사용한 프로필 버전, 보존 결과와 남은 제한만 간결하게 알린다.

## Completion

- 활성 주문이 대화 내용과 일치한다.
- 회사, 직무, 결과물, 출력 위치가 확정되어 있다.
- 모든 `tailor` 결과물에 실제 원본 `source_id`가 있다.
- 승인된 프로필을 재사용했거나 온보딩 단계로 정확히 전환했다.
- 사용자가 주문 파일이나 실행 도구를 직접 다루지 않았다.
- 요청된 워크플로우의 게이트와 최종 품질 검수가 실행되었다.
