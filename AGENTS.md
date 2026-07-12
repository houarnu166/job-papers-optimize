# Job Papers Optimize Harness

이 폴더는 한 명의 지원자가 여러 회사와 직무에 지원할 때 사용하는 독립형 프로젝트 로컬 작업환경이다. 특정 AI 제품, 전역 스킬, 개발 도구 또는 이전 환경에 의존하지 않는다. 작업 전 이 문서와 필요한 `skills/*/SKILL.md`를 읽는다.

## User Experience

- 사용자는 자연어로 요청하고 문서를 첨부하거나 지정하기만 한다.
- 사용자가 YAML, 명령줄, Python, Node.js, 패키지 관리자 또는 가상환경을 다룰 것을 요구하지 않는다.
- 새 회사 지원 요청에는 `skills/start-application/SKILL.md`를 기본 진입점으로 사용한다.
- 주문 파일은 에이전트가 대화에서 파악한 내용을 바탕으로 내부적으로 생성하고 관리한다. 사용자가 직접 편집하게 하지 않는다.
- 정보가 부족하면 결과에 큰 영향을 주는 항목만 짧게 질문한다. 답을 기다리지 않아도 되는 항목은 보수적인 기본값을 적용하고 기록한다.

## Core Rules

- 별도 요청이 없으면 사용자 대화와 산출물은 한국어로 작성한다.
- 환경 한 벌은 한 명의 지원자만 관리한다. 회사별 주문이 바뀌어도 승인된 지원자 프로필을 재사용한다.
- `inputs/private/sources/`의 원본은 항상 읽기 전용이다.
- `inputs/profile/`은 최초 프로필 확정 또는 갱신을 사용자가 명시적으로 승인한 경우에만 수정한다.
- 실제로 하지 않은 경력, 성과, 수치, 도구 경험, 재직 이력을 만들지 않는다.
- 지원자 사실은 `inputs/profile/evidence-ledger.md`의 근거 ID로 추적한다.
- 회사명은 조사 문서와 자기소개서처럼 필요한 곳에 사용하고 이력서와 포트폴리오에서는 반복하지 않는다.
- 모든 회사별 산출물은 해당 주문의 `outputs/{output_slug}/` 아래에만 작성한다.
- PDF는 입력 전용이다. PDF 생성, 변환 또는 PDF 제출본 제작을 수행하지 않는다.
- 기본 출력은 Markdown이다. DOCX와 HTML은 사용자가 요청하고 현재 런타임이 지원할 때만 승인된 Markdown을 변환해 만든다.
- 최종 전달 전 `quality-review`를 실행하고 Blocker가 있으면 최대 2회 수정·재검수한다.

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
│       ├── research/
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

## Agent Preflight

회사별 실행 전에 에이전트가 다음을 직접 확인하고 `outputs/{output_slug}/intake/preflight.md`에 결과를 기록한다.

- 승인된 프로필, 근거 장부, source map의 존재와 버전 일치
- 주문의 회사, 직무, 채용공고, 결과물, 출력 경로
- supplemental 자료의 존재와 현재 런타임에서의 가독 여부
- 회사 조사가 필요할 때 웹 조사 가능 여부와 제공된 대체 자료
- 요청 형식별 처리 경로와 Markdown fallback
- 출력 폴더가 다른 주문과 충돌하지 않는지 여부

점검은 에이전트의 파일 읽기와 현재 런타임 기능 확인으로 수행한다. 사용자가 별도 진단 명령을 실행할 필요가 없다. 웹 조사가 불가능하면 제공된 채용공고와 회사 자료만으로 범위를 제한하고 그 사실을 기록한다. 핵심 입력이 읽히지 않는 경우에만 적절한 대체 파일을 요청한다.

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

- `order_id`, `status`, `mode`, `output_slug`
- `profile.path`, `profile.version`
- `target`, `job_posting`, `materials.supplemental`
- `deliverables`, `constraints`

`status`는 `draft`, `ready`, `running`, `blocked`, `complete`, `example` 중 하나다. `mode`는 `linear` 또는 `flexible`이다. `deliverables`의 각 항목은 `type`, `format`, `preservation`을 가진다.

- 기본 `format`: `md`
- 허용 형식: `md`, `docx`, `html`
- 금지 형식: `pdf`
- 기본 `preservation`: `structure`
- 허용 보존 방식: `structure`, `layout-aware`, `redesign`
- `redesign`은 사용자가 명시적으로 요청한 경우에만 허용한다.

현재 대화에서 새 지원 요청이 들어오면 에이전트가 고유한 주문 파일을 만들고 그 파일을 활성 주문으로 사용한다. 기존 주문 실행을 명시한 경우 해당 파일을 사용한다. 대화 맥락 없이 실행만 요청했고 `status: ready`인 주문이 정확히 하나일 때만 자동 선택하며, 모호하면 사용자에게 회사와 직무를 확인한다.

## Run Modes

### Linear

1. Profile validation
2. `company-research`
3. `application-optimization`
4. `document-output` when DOCX or HTML is requested
5. `interview-prep` when requested
6. `quality-review`

### Flexible

요청 산출물에 직접 필요한 스킬만 실행한다. 지원 문서를 생성하거나 면접 자료를 만들 때는 profile validation과 `quality-review`를 생략하지 않는다. 필요한 선행 자료가 없으면 `worklog.md`와 사용자 응답에 누락을 기록하고 임의로 채우지 않는다.

## Material And Structure Preservation

- 일반 입력 형식은 PDF, DOCX, Markdown, HTML, JSON, TXT다. 실제 처리는 현재 런타임이 읽을 수 있는 형식에 한한다.
- PDF는 텍스트, 페이지 표식, 이미지, 문서 구조를 파악하는 데만 사용한다.
- 원본 기반 최적화는 제목 위계, 섹션 순서, 문단 경계, 목록, 표, 이미지 순서와 캡션을 보존한다.
- Markdown에는 확인 가능한 PDF 페이지 경계를 `<!-- source-page: N -->`으로 남긴다.
- JSON 입력은 사용자가 새 구조를 요청하지 않는 한 기존 키 구조를 보존한다.
- 원본에 없는 수치는 최종 제출 문구에 넣지 않는다. 계획 문서에는 `확인 필요`로 표시한다.
- 추출할 수 있는 이미지와 재사용 자산은 `outputs/{output_slug}/assets/`에 안정적인 이름으로 저장한다. 추출이 불가능하면 누락을 숨기지 않고 원본 이미지 파일 제공을 요청한다.

## Output Contract

회사별 작업은 다음 핵심 파일을 사용한다.

- `application/capability-assessment.md`
- `application/requirement-evidence-matrix.md`
- `application/matching-strategy.md`
- `application/change-log.md`
- 요청된 `application/resume.md`, `cover-letter.md`, `portfolio.md`
- 지원되는 경우 선택적 `exports/*.docx`, `exports/*.html`
- 선택적 `interview/interview-prep.md`
- `review/quality-review.md`

DOCX와 HTML은 승인된 Markdown 내용을 변환하며 변환 단계에서 내용을 새로 쓰지 않는다. Markdown은 논리 구조를 보존하지만 폰트, 좌표, 정확한 페이지 배치를 복제하지 않는다. 선택 출력이 지원되지 않을 때 Markdown은 정식 fallback 산출물이며, 에이전트가 사용자에게 제한을 명확히 알린다.

## Quality Loop

- `quality-review`는 프로필 버전·가능한 경우 해시, 근거 ID, 사실성, 상충 정보, 구조 보존, 회사명 사용, ATS 가독성, 날짜·연락처·링크, 표와 이미지 누락을 검사한다.
- Blocker 또는 Major가 수정 가능하면 소유 스킬로 돌아가 수정하고 다시 검수한다.
- 자동 수정·재검수는 최대 2회다.
- 이후 Blocker가 남으면 주문 상태를 `blocked`로 기록하고 사용자 확인을 요청한다.
- 이전 회사 산출물은 새 프로필 버전으로 자동 갱신하지 않는다.

## Completion Criteria

- 주문의 모든 deliverable이 생성되었거나 지원되지 않는 선택 형식의 Markdown fallback과 사유가 기록되어 있다.
- 사용한 프로필 버전과 가능한 경우 해시가 `worklog.md`에 있다.
- 최종 주장에 근거 ID가 연결되어 있다.
- 원본과 승인 전 기준 프로필이 수정되지 않았다.
- PDF 산출물이 생성되지 않았다.
- DOCX 시각 QA를 못 했다면 제한이 명시되어 있다.
- `review/quality-review.md`가 있고 Blocker가 없다.
