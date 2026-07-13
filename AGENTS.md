# Job Papers Optimize Harness

이 폴더는 한 명의 지원자가 여러 회사와 직무에 지원할 때 사용하는 독립형 프로젝트 로컬 작업환경이다. 특정 AI 제품, 전역 스킬, 개발 도구 또는 다른 작업환경에 의존하지 않는다. 작업 전 이 문서와 현재 단계에 필요한 `skills/*/SKILL.md` 및 그 스킬이 지정한 `references/` 문서를 읽는다.

## Operating Principle

- 유연성은 실행 범위를 고르는 기능이다. 필수 근거, 원본 보존, 단계 게이트 또는 최종 검수를 생략하는 기능이 아니다.
- 회사별 작업은 `intake -> research -> strategy -> application -> interview -> review`의 상태를 파일로 남긴다.
- 각 단계는 정해진 산출물과 완료 조건을 충족한 뒤에만 다음 단계로 넘어간다. 파일을 만들었다는 사실만으로 완료 처리하지 않는다.
- 기존 문서를 최적화하는 일과 새 문서를 만드는 일을 구분한다. 원본이 있는데 새 템플릿으로 다시 쓰는 행위는 최적화가 아니다.
- 프로젝트 폴더 밖의 규칙, 자료 또는 산출물을 실행 의존성으로 사용하지 않는다.

## User Experience

- 사용자는 자연어로 요청하고 문서를 첨부하거나 지정하기만 한다.
- 사용자가 YAML, 명령줄, Python, Node.js, 패키지 관리자 또는 가상환경을 다룰 것을 요구하지 않는다.
- 새 회사 지원 요청에는 `skills/start-application/SKILL.md`를 기본 진입점으로 사용한다.
- 주문 파일은 에이전트가 대화에서 파악한 내용을 바탕으로 내부적으로 생성하고 관리한다. 사용자가 직접 편집하게 하지 않는다.
- 정보가 부족하면 결과에 큰 영향을 주는 항목만 짧게 질문한다. 다만 기존 문서 최적화 요청에 원본이 없거나 읽히지 않는 경우에는 원본을 요청해야 한다.

## Core Rules

- 별도 요청이 없으면 사용자 대화와 산출물은 한국어로 작성한다.
- 환경 한 벌은 한 명의 지원자만 관리한다. 회사별 주문이 바뀌어도 승인된 지원자 프로필을 재사용한다.
- `inputs/private/sources/`의 원본과 대화에 첨부된 원본은 항상 읽기 전용이다.
- `inputs/profile/`은 최초 프로필 확정 또는 갱신을 사용자가 명시적으로 승인한 경우에만 수정한다.
- 실제로 하지 않은 경력, 성과, 수치, 도구 경험, 재직 이력을 만들지 않는다.
- 지원자 사실은 `inputs/profile/evidence-ledger.md`의 근거 ID로 추적한다.
- 최종 제출용 이력서, 자기소개서, 포트폴리오에는 `EV-####`, `SRC-####`, 내부 메모, TODO, `확인 필요` 같은 작업 표식을 노출하지 않는다. 근거 연결은 내부 분석 문서와 `change-log.md`에만 둔다.
- 회사명은 조사 문서와 자기소개서처럼 필요한 곳에 사용하고 이력서와 포트폴리오에서는 반복하지 않는다.
- 모든 회사별 산출물은 해당 주문의 `outputs/{output_slug}/` 아래에만 작성한다.
- PDF는 입력 전용이다. PDF 생성, 변환 또는 PDF 제출본 제작을 수행하지 않는다.
- 기본 출력은 Markdown이다. DOCX와 HTML은 사용자가 요청하고 현재 런타임이 지원할 때만 승인된 Markdown을 변환해 만든다.
- 최종 전달 전 `quality-review`를 독립된 시선으로 실행하고 Blocker나 Major가 있으면 최대 2회 수정·재검수한다.

## Directory Contract

```text
job_papers_optimize/
├── AGENTS.md
├── inputs/
│   ├── profile/
│   │   ├── candidate-profile.md
│   │   ├── evidence-ledger.md
│   │   ├── source-map.md
│   │   ├── assets/
│   │   └── history/
│   ├── private/sources/
│   └── examples/
├── orders/
├── outputs/
│   ├── _profile-updates/{update_id}/
│   └── {회사명-직무명}/
│       ├── worklog.md
│       ├── source-ledger.md
│       ├── intake/
│       │   ├── preflight.md
│       │   ├── material-inventory.md
│       │   └── source-structure.md
│       ├── research/
│       │   ├── research-plan.md
│       │   └── company-job-analysis.md
│       ├── application/
│       ├── exports/
│       ├── assets/
│       ├── interview/
│       └── review/
└── skills/
```

공유본에는 템플릿과 익명 예시만 포함한다. 실제 `candidate-profile.md`, `evidence-ledger.md`, `source-map.md`, 개인 원본, 회사별 산출물은 공유하지 않는다.

## Installation-Free Runtime Policy

1. 현재 AI 클라이언트나 에이전트 런타임에 이미 제공된 파일 읽기, 문서, PDF, 비전, 웹 조사 기능만 사용한다.
2. 프로젝트 실행을 위해 프로그램, 패키지, 런타임 또는 시스템 도구를 설치하지 않는다.
3. 사용자가 터미널 명령을 실행하거나 개발 환경을 설정하도록 안내하지 않는다.
4. 현재 런타임이 입력 포맷을 읽지 못하면 내용을 추측하지 않는다. 가능한 대체 입력 형식을 한두 개만 제시하고 사용자에게 다시 제공해 달라고 요청한다.
5. 현재 런타임이 DOCX를 만들지 못하면 승인된 Markdown을 최종본으로 제공하고 제한을 `worklog.md`, `exports/export-notes.md`, `review/quality-review.md`에 기록한다.
6. 선택 기능의 부재는 읽을 수 있는 자료로 진행 가능한 핵심 분석과 Markdown 산출을 막지 않는다.

대체 입력은 목적에 맞게 요청한다. 레이아웃 확인이 필요하면 PDF 또는 HTML, 내용만 필요하면 Markdown 또는 TXT, 구조화 데이터면 JSON을 우선한다. 변환 방법이나 특정 앱 설치를 사용자에게 강요하지 않는다.

## Persistent Profile

- 기준 프로필은 Markdown+YAML 형식의 `inputs/profile/candidate-profile.md`다.
- YAML에는 `profile_id`, `version`, `updated_at`, `language`를 둔다.
- 경력과 프로젝트에는 변경되지 않는 ID를 부여한다.
- `evidence-ledger.md`는 `evidence_id`, 주장, 원본 경로, locator, 신뢰도, 상태를 기록한다.
- 주문을 시작할 때 프로필을 다시 추출하지 않는다. 파일 존재, 버전, 근거 장부만 검증한다.
- 사용한 프로필 버전과 SHA-256을 에이전트가 계산할 수 있으면 회사별 `worklog.md`에 기록한다. 불가능하면 버전과 `updated_at`을 기록하고 해시 미기록 사유를 남긴다.
- 신규 자료는 주문별 임시 근거로 사용할 수 있지만 기준 프로필 갱신은 별도 승인을 거친다.

## Profile Initialization And Update

- 최초 생성과 갱신에는 `skills/candidate-profile/SKILL.md`를 사용한다.
- 갱신안은 `outputs/_profile-updates/{update_id}/`에 `update-proposal.md`, `evidence-diff.md`, `staged-profile.md`, `evidence-ledger.md`, 필요한 경우 `source-map.md`를 작성한다.
- 승인 전에는 기준 프로필을 수정하지 않는다.
- 사용자가 명시적으로 승인한 뒤에만 에이전트가 `candidate-profile`의 Approval Workflow에 따라 기준 파일을 갱신한다.
- 승인 시 기존 프로필과 근거 장부를 `inputs/profile/history/`에 보존하고 버전을 1 증가시킨다.
- 거절된 제안은 기준 프로필에 반영하지 않는다.

## Internal Order Interface

주문은 에이전트가 생성하는 YAML front matter 형식의 내부 실행 기록이다. 필수 항목은 다음과 같다.

- `order_id`, `status`, `mode`, `output_slug`, `research_depth`
- `profile.path`, `profile.version`
- `target`, `job_posting`
- `materials.primary`, `materials.supplemental`
- `deliverables`, `constraints`

`materials.primary`의 각 문서는 `id`, `role`, `path`, `authority`를 가진다. `role`은 `resume`, `cover-letter`, `portfolio`, `submitted-resume`, `submitted-portfolio`, `career-evidence`, `job-posting`, `other` 중 하나다. 대화 첨부 파일의 안정적인 경로가 없으면 파일명과 대화 시점을 기록하고 첫 읽기에서 내용·구조 스냅샷을 `intake/`에 남긴다.

`deliverables`의 각 항목은 다음을 가진다.

- `type`: 산출물 종류
- `operation`: `tailor` 또는 `create`
- `source_id`: `tailor`일 때 필수인 원본 문서 ID
- `format`: `md`, `docx`, `html` 중 하나
- `preservation`: `source-locked`, `layout-aware`, `redesign`, `not-applicable` 중 하나

기존 문서를 개선하는 기본값은 `operation: tailor`, `preservation: source-locked`다. `tailor`인데 `source_id`가 없거나 읽을 수 없으면 Blocker다. 프로필은 사실의 근거이지 원본 문서 형식의 대체물이 아니다. `create`, `redesign`은 사용자가 새 문서나 새 디자인을 명시적으로 요청한 경우에만 허용한다. 이전 주문의 `preservation: structure`는 `source-locked`로 해석한다.

`status`는 `draft`, `ready`, `running`, `needs-user`, `blocked`, `complete`, `example` 중 하나다. PDF는 입력 자료로만 허용하고 deliverable 형식으로 두지 않는다.

현재 대화에서 새 지원 요청이 들어오면 에이전트가 고유한 주문 파일을 만들고 그 파일을 활성 주문으로 사용한다. 기존 주문 실행을 명시한 경우 해당 파일을 사용한다. 대화 맥락 없이 실행만 요청했고 `status: ready`인 주문이 정확히 하나일 때만 자동 선택하며, 모호하면 사용자에게 회사와 직무를 확인한다.

## Workflow State And Gates

`worklog.md`에는 `Phase`, `Status`, `Required artifacts`, `Gate result`, `Notes` 열의 체크포인트 표를 둔다. 상태는 `pending`, `in-progress`, `passed`, `needs-user`, `blocked`만 사용한다. 한 단계의 게이트가 `passed`가 아니면 다음 단계 산출물을 최종본으로 확정하지 않는다.

1. **Gate 0 - Profile And Order**: 활성 주문, 프로필 버전, 출력 경로가 확정됐다.
2. **Gate 1 - Source Lock**: 모든 `tailor` 산출물의 `source_id`가 실제 원본에 연결됐고 `material-inventory.md`, `source-structure.md`가 완성됐다.
3. **Gate 2 - Research**: `research-plan.md`, 채용공고 보존본, source ledger, 고정 목차의 `company-job-analysis.md`가 완성됐다.
4. **Gate 3 - Matching Strategy**: 역량 정리, 요구사항-근거 매트릭스, 매칭 전략이 서로 일치한다.
5. **Gate 4 - Application Drafts**: 문서별 분석·계획, 최종 초안, 블록 단위 변경 이력과 구조 비교가 완성됐다.
6. **Gate 5 - Interview**: 요청 범위의 고정 포맷, 질문 수, 답변 근거, 꼬리질문, 역질문과 체크리스트가 충족됐다.
7. **Gate 6 - Independent Review**: `quality-review`가 원본과 결과물을 직접 비교했고 Blocker와 Major가 없다.

핵심 입력이 없으면 해당 게이트를 `needs-user`로 기록한다. 이를 건너뛰고 이후 단계 전체를 완료로 표시하지 않는다.

## Run Modes

### Linear

Gate 0부터 Gate 6까지 순서대로 진행한다. 인터뷰가 주문에 없으면 Gate 5를 `not requested` 근거와 함께 통과 처리할 수 있다. DOCX 또는 HTML이 요청되면 Gate 4와 Gate 6 사이에 `document-output`을 실행한다.

### Flexible

요청 산출물에 직접 필요한 단계만 실행하되 그 산출물의 선행 게이트와 Gate 6은 유지한다. 예를 들어 회사 조사만 요청하면 Gate 0과 Gate 2 및 연구 검수를, 기존 이력서 수정만 요청하면 Gate 0, Gate 1, 필요한 Gate 3, Gate 4, Gate 6을 실행한다. 유연 모드는 고정 보고서 포맷이나 원본 비교를 생략하는 근거가 아니다.

## Source Preservation Contract

- 원본 기반 작업은 `skills/application-optimization/references/source-preservation-contract.md`를 따른다.
- 첫 작성 전에 원본의 형식, 페이지 또는 최상위 구조, 제목 위계, 섹션 순서, 문단·목록·표, 이미지·캡션, 반복 패턴을 `intake/source-structure.md`에 블록 순서대로 기록한다.
- `source-locked`에서는 기존 블록의 순서와 역할을 유지하고 각 블록 안의 문구만 최적화한다. 삭제, 추가, 병합, 분할, 순서 변경은 사용자 승인이나 제출 규격상 불가피한 사유를 `change-log.md`에 남긴 경우에만 허용한다.
- `layout-aware`에서는 페이지 수, 페이지 비율, 주요 영역과 이미지 배치를 추가로 보존한다. 관찰할 수 없는 좌표나 폰트는 추측하지 않는다.
- Markdown 출력은 원본의 논리 구조와 페이지/블록 대응을 보존하지만 폰트와 좌표를 복제하지 않는다. 내부 페이지 대응표는 `source-structure.md`에 두고 최종 제출 문서에는 작업 표식을 넣지 않는다.
- JSON 입력은 키 이름, 중첩, 키 순서, 배열 항목 구조를 유지한다. 값만 수정하며 항목 재배열도 승인된 변경으로 기록한다.
- HTML 입력은 의미 구조, DOM 순서, 클래스와 자산 연결을 유지한다. DOCX/PDF는 관찰 가능한 문단, 표, 이미지와 페이지 구조를 기준으로 삼는다.
- 원본에서 확인되는 이미지와 재사용 자산은 `assets/asset-inventory.md`에 원본 위치, 크기·비율, 캡션, 사용 위치를 기록한다. 추출할 수 없으면 누락을 숨기지 않는다.
- 원본을 읽지 못했거나 구조 대응표가 없으면 `source-locked` 또는 `layout-aware` 보존을 통과했다고 주장할 수 없다.

## Output Contract

회사별 전체 작업은 다음 핵심 파일을 사용한다.

- `intake/preflight.md`, `material-inventory.md`, `source-structure.md`
- `research/research-plan.md`, `job-posting.md`, `company-job-analysis.md`
- `application/capability-assessment.md`
- `application/requirement-evidence-matrix.md`
- `application/matching-strategy.md`
- 요청 문서별 `application/{type}-analysis.md` 또는 `portfolio-plan.md`
- 요청된 `application/resume.md`, `cover-letter.md`, `portfolio.md`
- `application/change-log.md`, `submission-package.md`
- 지원되는 경우 선택적 `exports/*.docx`, `exports/*.html`
- 요청된 경우 `interview/interview-plan.md`, `interview/interview-prep.md`
- `review/quality-review.md`

`company-job-analysis.md`, 면접 자료와 문서별 분석·계획은 각 스킬의 `references/`에 정의된 목차를 따른다. 정보가 없다는 이유로 필수 섹션을 삭제하지 않고 `확인되지 않음`, 조사 범위와 필요한 검증을 기록한다.

DOCX와 HTML은 승인된 Markdown 내용을 변환하며 변환 단계에서 내용을 새로 쓰지 않는다. 선택 출력이 지원되지 않을 때 Markdown은 정식 fallback 산출물이며 제한을 명확히 알린다.

## Quality Loop

- `quality-review`는 이전 단계의 PASS 선언을 신뢰하지 않고 활성 주문, 원본, 구조 명세, 최종 문서를 직접 비교한다.
- 검수는 프로필 버전·근거 ID, 사실성, 상충 정보, 회사 조사 목차, 면접 포맷, 원본 구조 대응, 회사명 사용, ATS 가독성, 날짜·연락처·링크, 표와 이미지 누락, 내부 표식 노출을 검사한다.
- `tailor` 산출물에 원본 바인딩 또는 구조 비교 증거가 없으면 Blocker다.
- 필수 회사 조사 섹션이나 요청된 면접 질문 카테고리·필드가 누락되면 Major 이상이다.
- Blocker 또는 Major가 수정 가능하면 소유 스킬로 돌아가 수정하고 다시 검수한다. 자동 수정·재검수는 최대 2회다.
- 이후 Blocker가 남으면 주문 상태를 `needs-user` 또는 `blocked`로 기록하고 사용자 확인을 요청한다.
- 이전 회사 산출물은 새 프로필 버전으로 자동 갱신하지 않는다.

## Completion Criteria

- `worklog.md`의 실행 대상 게이트가 모두 `passed`이고 각 게이트의 실제 산출물이 존재한다.
- 주문의 모든 deliverable이 생성되었거나 지원되지 않는 선택 형식의 Markdown fallback과 사유가 기록되어 있다.
- 모든 `tailor` deliverable이 원본 `source_id`와 연결되고 구조 비교를 통과했다.
- 회사 조사 보고서와 면접 자료가 해당 고정 산출물 계약을 충족한다.
- 사용한 프로필 버전과 가능한 경우 해시가 `worklog.md`에 있다.
- 최종 주장에 대한 근거 연결이 내부 분석 문서에 있고 제출 문서에는 내부 표식이 없다.
- 원본과 승인 전 기준 프로필이 수정되지 않았다.
- PDF 산출물이 생성되지 않았다.
- DOCX 시각 QA를 못 했다면 제한이 명시되어 있다.
- `review/quality-review.md`가 있고 Blocker와 Major가 없다.
