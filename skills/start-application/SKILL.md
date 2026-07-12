---
name: start-application
description: Start a new company or role application from natural-language conversation and attached materials, create the internal order, validate the persistent candidate profile, and route the requested research, application, portfolio, interview, and review work. Use when the user says they are applying to a company, shares a job posting, asks to tailor application materials, begins interview preparation for a new target, or wants to resume a named company order. The user must not be asked to author YAML or run setup commands.
---

# Start Application

자연어 대화를 회사별 지원 작업으로 변환하는 기본 진입점이다. 사용자는 파일을 제공하고 원하는 일을 말하며, 주문 파일과 실행 경로는 에이전트가 관리한다.

## Intake

대화와 첨부 자료에서 다음을 파악한다.

- 회사와 직무
- 채용공고 URL 또는 본문
- 지원 단계와 마감일
- 원하는 결과물
- 보존 방식, 언어, 톤, 길이, 제출 조건
- 이번 주문에만 추가할 자료

결과에 큰 영향을 주는 필수 정보가 없을 때만 질문한다. 회사와 직무, 채용공고 또는 역할 설명, 원하는 결과물은 우선 확인한다. 나머지는 다음 기본값을 사용하고 `worklog.md`에 기록할 수 있다.

- `mode: linear`
- `research_depth: standard`
- `format: md`
- `preservation: structure`
- `language: ko`
- `tone: professional-natural`

## Profile Gate

1. `inputs/profile/candidate-profile.md`, `evidence-ledger.md`, `source-map.md`가 있으면 버전과 상태만 검증하고 재추출하지 않는다.
2. 승인된 프로필이 없으면 `candidate-profile`의 Initialize 모드로 안내하고 회사별 문서 작성 전에 프로필 제안을 만든다.
3. 새 자료가 기존 프로필에 없는 사실을 포함하면 이번 주문의 supplemental evidence로만 사용한다.
4. 영구 반영이 필요하면 회사별 작업과 분리해 `candidate-profile`의 Update 모드를 제안한다.

## Create Internal Order

1. `orders/order-template.md`의 필드를 사용해 고유한 주문 파일을 에이전트가 작성한다.
2. `order_id`는 회사, 직무, 날짜를 구분할 수 있게 만들고 기존 파일을 덮어쓰지 않는다.
3. `output_slug`는 회사명과 직무명을 사람이 읽기 쉬운 형태로 만들며 경로 구분자와 위험한 문자를 제거한다.
4. 충분한 정보가 있으면 `status: ready`, 핵심 정보가 없으면 `status: draft` 또는 `blocked`로 둔다.
5. 사용자가 DOCX나 HTML을 요청해도 승인 원본인 Markdown deliverable을 함께 계획한다.
6. PDF는 deliverable 형식으로 넣지 않는다.

주문 YAML은 내부 실행 기록이다. 사용자가 요청하지 않는 한 YAML 편집이나 주문 경로 선택을 사용자에게 맡기지 않는다.

## Preflight

주문 실행 전에 AGENTS.md의 Agent Preflight를 수행한다. 에이전트가 프로필과 자료를 직접 점검하고 `outputs/{output_slug}/intake/preflight.md`를 작성한다. 읽을 수 있는 자료와 Markdown 산출 경로가 확보되면 선택 기능이 없어도 진행한다.

## Route Work

- 전체 지원 준비는 linear 모드로 실행한다.
- 특정 문서 수정, 회사 조사만 수행, 면접 준비처럼 범위가 분명하면 flexible 모드를 사용할 수 있다.
- 모든 모드에서 profile validation과 `quality-review`는 유지한다.
- DOCX 또는 HTML 요청이 있을 때만 `document-output`을 실행한다.
- 현재 런타임이 선택 출력 형식을 지원하지 않으면 설치를 요구하지 않고 Markdown fallback을 전달한다.

## Conversation Rules

- 사용자가 개발 도구를 안다고 가정하지 않는다.
- 터미널, 런타임, 패키지 또는 플러그인 설치를 지시하지 않는다.
- 읽을 수 없는 첨부 파일은 추측하지 말고 목적에 맞는 대체 형식 한두 개를 요청한다.
- 처리 가능한 자료와 단계부터 진행하고, 막힌 부분과 필요한 사용자 응답을 명확히 분리한다.
- 최종 응답에는 생성된 결과물, 사용한 프로필 버전, 남은 제한만 간결하게 알린다.

## Completion

- 활성 주문이 대화 내용과 일치한다.
- 회사, 직무, 결과물, 출력 위치가 확정되어 있다.
- 승인된 프로필을 재사용했거나 온보딩 단계로 정확히 전환했다.
- 사용자가 주문 파일이나 실행 도구를 직접 다루지 않았다.
- 요청된 워크플로우와 최종 품질 검수가 실행되었다.
