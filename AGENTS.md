# Career Lifecycle Harness

이 폴더는 한 명의 지원자가 IT 이직 라이프사이클을 반복해서 운영하는 독립형 프로젝트 로컬 작업환경이다. 특정 AI 제품, 전역 스킬, 개발 도구 또는 다른 작업환경에 의존하지 않는다. 작업 전 이 문서와 현재 단계에 필요한 `skills/*/SKILL.md` 및 그 스킬이 지정한 `references/` 문서를 읽는다.

## Operating Principle

- 이 환경은 공고를 발견한 뒤에 시작하지 않는다. 공고 전에 반복 요소를 90% 상태로 만들어 두고, 공고가 뜨면 기업별 10%만 더해 제출한다.
- 90% 자산은 `package/`에, 공고별 운영 기록은 `pipeline/`에, 회사별 산출물은 `outputs/{output_slug}/`에 둔다. 세 영역을 섞지 않는다.
- 준비 단계에 고정 기간을 두지 않는다. 완료 날짜가 아니라 READY 판정 기준으로 관리한다.
- 각 단계는 정해진 산출물과 완료 조건을 충족한 뒤에만 다음 단계로 넘어간다. 파일을 만들었다는 사실만으로 완료 처리하지 않는다.
- 기존 문서를 최적화하는 일과 새 문서를 만드는 일을 구분한다. 원본이 있는데 새 템플릿으로 다시 쓰는 행위는 최적화가 아니다.
- 결과는 지원 건의 끝이 아니라 다음 기회의 READY 수준을 높이는 데이터다. 7단계 회고 없이 지원 건을 닫지 않는다.
- 프로젝트 폴더 밖의 규칙, 자료 또는 산출물을 실행 의존성으로 사용하지 않는다.

## User Experience

- 사용자는 자연어로 요청하고 문서를 첨부하거나 지정하기만 한다.
- 사용자가 YAML, 명령줄, Python, Node.js, 패키지 관리자 또는 가상환경을 다룰 것을 요구하지 않는다.
- 주문 파일과 실행 상태는 에이전트가 대화에서 파악한 내용을 바탕으로 만들고 관리한다.
- 정보가 부족하면 결과에 큰 영향을 주는 항목만 짧게 질문한다. 다만 기존 문서 최적화 요청에 원본이 없거나 읽히지 않는 경우에는 원본을 요청해야 한다.
- 요청이 어느 단계에 해당하는지 먼저 판정하고, 선행 단계가 비어 있으면 그 사실과 최소 필요 작업을 알린 뒤 진행 방법을 확인한다.

## Core Rules

- 별도 요청이 없으면 사용자 대화와 산출물은 한국어로 작성한다.
- 환경 한 벌은 한 명의 지원자만 관리한다.
- `inputs/private/sources/`, `inputs/주로제출하던이력서와포트폴리오/`의 원본과 대화에 첨부된 원본은 항상 읽기 전용이다.
- `inputs/profile/`은 최초 프로필 확정 또는 갱신을 사용자가 명시적으로 승인한 경우에만 수정한다.
- 실제로 하지 않은 경력, 성과, 수치, 도구 경험, 재직 이력을 만들지 않는다. 정확한 값이 없으면 근거 있는 범위와 추정 여부를 명시한다.
- 지원자 사실은 `inputs/profile/evidence-ledger.md`의 근거 ID로 추적한다.
- 최종 제출용 문서에는 `EV-####`, `SRC-####`, 내부 메모, TODO, `확인 필요` 같은 작업 표식을 노출하지 않는다. 근거 연결은 내부 분석 문서와 `change-log.md`에만 둔다.
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
│   ├── profile/                      # 사실 장부
│   │   ├── candidate-profile.md
│   │   ├── evidence-ledger.md
│   │   ├── source-map.md
│   │   ├── assets/
│   │   └── history/
│   ├── private/sources/              # 원본 경력 자료 (읽기 전용)
│   ├── 주로제출하던이력서와포트폴리오/    # 제출 원본 (읽기 전용)
│   └── IT 대기업 상향 이직 웨비나/       # 라이프사이클 근거 문서
├── package/                          # 90% Ready-made 자산
│   ├── experience-inventory.md
│   ├── target-map.md
│   ├── experience-assets/
│   ├── jd-scorecards/
│   ├── master/
│   ├── variants.md
│   ├── assignment-framework.md
│   ├── interview-assets.md
│   ├── readiness.md
│   └── profile-updates/{update_id}/
├── pipeline/                         # 공고별 운영 기록
│   ├── postings/{posting_id}.md
│   ├── triage/{posting_id}.md
│   ├── application-log.md
│   └── retrospectives/{posting_id}.md
├── outputs/{output_slug}/            # 회사별 10% 산출물
│   ├── order.md
│   ├── worklog.md
│   ├── source-ledger.md
│   ├── intake/
│   ├── research/
│   ├── application/
│   ├── assignment/
│   ├── interview/
│   ├── exports/
│   ├── assets/
│   └── review/
└── skills/
```

`package/`, `pipeline/`, `outputs/`, 실제 프로필과 개인 원본은 공유하지 않는다.

## Lifecycle

| 단계 | 이름 | 담당 스킬 | 게이트 |
|---|---|---|---|
| 1 | 경험 원재료 목록화·목표 지도·공고 감지 체계 | `target-map` | L1 |
| 2 | 경험·증거 자산 구축 | `experience-interview`, `candidate-profile` | L2 |
| 3 | 90% Ready-made 패키지 | `ready-package`, `application-optimization` | L3 |
| 4 | 공고 감지·Go/No-Go | `opportunity-triage` | L4 |
| 5 | 기업별 10% 맞춤화·제출 | `start-application`, `company-research`, `application-optimization` | L5 |
| 6 | 과제·면접·레퍼런스 | `assignment-brief`, `interview-prep` | L6 |
| 7 | 결과 회고·패키지 개선 | `pipeline-retro` | L7 |

1~3단계는 시스템 구축이고 4~7단계는 공고별 반복 운영이다. 공통 스킬은 `quality-review`, `document-export`, `pdf`다.

목표 직무는 경험 원재료를 나열한 뒤에 정한다. 가고 싶은 회사에서 거꾸로 직무를 정하지 않고, 이미 가진 증거가 어떤 직무와 산업에서 읽히는지를 먼저 지도화한다. 1단계의 원재료 목록은 사실의 범위를 잃지 않기 위한 나열이고, 2단계는 그중 대표 경험을 판단·행동·결과로 심화한다.

## Gates

한 게이트가 `passed`가 아니면 다음 단계 산출물을 최종본으로 확정하지 않는다. 상태는 `pending`, `in-progress`, `passed`, `needs-user`, `blocked`만 사용한다.

- **L1 목표 확정**: 경험 원재료 목록이 `package/experience-inventory.md`에 회사·기간별로 빠짐없이 있고, 목표 직무 A/B/C 정의, 산업·기업 지도, 공고 감지 체계와 JD 저장 규칙이 `package/target-map.md`에 있다. 직무 축은 원재료 목록 없이 확정하지 않는다.
- **L2 증거 검증**: 모든 대표 경험이 문제–판단–행동–결과–학습으로 재구성됐고, 강한 주장이 `verified`이거나 추정·범위로 표기됐으며, 충돌 수치가 해소 또는 명시됐다.
- **L3 READY**: 서류·전형·면접 3축 테스트를 통과했고, 공고 1건 리허설로 병목과 소요시간이 기록됐다.
- **L4 Go/No-Go**: 공고 원문 보존본과 판정 근거가 `pipeline/postings/`, `pipeline/triage/`에 있다.
- **L5 제출**: 아래 체크포인트를 모두 통과했다.
  - L5.1 원본 잠금 — 모든 `tailor` 산출물이 실제 원본과 연결되고 `intake/material-inventory.md`, `intake/source-structure.md`가 완성됐다.
  - L5.2 조사 — 모든 조사 분야를 순서대로 최소 한 번 확인해 coverage status를 기록했고 고정 목차의 `company-job-analysis.md`가 완성됐다.
  - L5.3 매칭 — 역량 정리, 요구사항-근거 매트릭스, 회사 신호-지원자 근거 매트릭스, 매칭 전략이 서로 일치한다.
  - L5.4 초안 — 문서별 분석·연출 계획, 최종 초안, 블록 단위 변경 이력과 형식 보존 비교가 완성됐다.
  - L5.5 검수 — `quality-review`가 원본과 결과물을 직접 비교했고 Blocker와 Major가 없다.
- **L6 전형 실행**: 요청 범위의 사전과제, 면접 준비와 즉시 복기, 레퍼런스 진행 기록이 있다.
- **L7 회고**: 퍼널 단계별 결과가 `pipeline/application-log.md`에 기록되고, 병목이 마스터 승격 또는 보완 과제로 전환됐다.

핵심 입력이 없으면 해당 게이트를 `needs-user`로 기록한다. 이를 건너뛰고 이후 단계 전체를 완료로 표시하지 않는다.

## Ready-made Package Contract

- 마스터 문서는 각 1벌만 유지한다. `package/master/`에 `resume.md`, `career-history.md`, `portfolio-storyboard.md`, `cover-letter-skeleton.md`를 둔다.
- 목표 직무 A/B/C의 차이는 별도 문서가 아니라 `package/variants.md`의 변형 레시피로 관리한다. 레시피는 대표 경험 선택, 노출 순서, 직무 언어, 상단 메시지만 규정하고 사실을 바꾸지 않는다.
- 포트폴리오 마스터는 페이지 편집 지시서다. 원본 페이지마다 `keep`, `compress`, `move`, `remove`, `new` 판정과 근거, 그 페이지에서 읽혀야 할 핵심 문장을 기록한다. PDF와 디자인 툴 실작업은 이 환경의 범위가 아니다.
- 마스터는 제출 원본을 권위로 삼는다. 원본 형식 골격을 벗어나는 구조 변경은 사용자 승인 전 제안으로만 남긴다.
- 마스터가 바뀌면 `package/readiness.md`의 READY 판정을 다시 하고 변경 이유와 버전을 남긴다.

## Posting Operation Contract

- 새 공고는 발견 즉시 `pipeline/postings/{posting_id}.md`에 원문, 발견일, 마감일, 출처, 조직 정보, 목표 지도상의 경로를 저장한다.
- Go/조건부 Go/No-Go 판정과 근거는 `pipeline/triage/{posting_id}.md`에 남긴다. No-Go도 기록한다.
- `Go` 또는 `조건부 Go`일 때만 `outputs/{output_slug}/`를 만들고 5단계를 시작한다.
- `pipeline/application-log.md`는 발견–지원–서류–과제–면접–레퍼런스–결과의 단계별 상태와 사용한 마스터 버전을 한 행으로 기록한다.
- 결과가 확정되면 `pipeline/retrospectives/{posting_id}.md`를 쓰고 마스터 승격 항목을 `package/`에 반영한다.

## Internal Order Interface

주문은 에이전트가 생성하는 YAML front matter 형식의 내부 실행 기록이며 `outputs/{output_slug}/order.md`에 둔다. 필수 항목은 다음과 같다.

- `order_id`, `status`, `output_slug`, `posting_id`, `research_depth`
- `profile.path`, `profile.version`
- `package.master_version`, `package.variant`
- `target`, `job_posting`
- `materials.primary`, `materials.supplemental`
- `deliverables`, `constraints`

`materials.primary`의 각 문서는 `id`, `role`, `path`, `authority`를 가진다. `role`은 `master-resume`, `master-career-history`, `master-portfolio`, `master-cover-letter`, `submitted-resume`, `submitted-portfolio`, `career-evidence`, `job-posting`, `other` 중 하나다.

`deliverables`의 각 항목은 `type`, `operation`, `source_id`, `format`, `preservation`을 가진다. `operation`은 `tailor` 또는 `create`, `format`은 `md`, `docx`, `html`, `preservation`은 `source-locked`, `layout-aware`, `redesign`, `not-applicable` 중 하나다.

5단계의 기본값은 `operation: tailor`, `source_id`는 해당 마스터 문서, `preservation: source-locked`다. 마스터가 없으면 3단계로 돌아간다. `tailor`인데 `source_id`가 없거나 읽을 수 없으면 Blocker다. `create`와 `redesign`은 사용자가 명시적으로 요청한 경우에만 허용한다.

`constraints.optimization`의 기본값은 `wording: allowed`, `emphasis: allowed`, `reorder_within_section: allowed`, `resequence_repeated_units: allowed`이며 `structural_redesign`과 `add_or_remove_content_blocks`는 `require-user-approval`이다.

`status`는 `draft`, `ready`, `running`, `needs-user`, `blocked`, `complete` 중 하나다. PDF는 deliverable 형식으로 두지 않는다.

## Source Preservation Contract

- 원본 기반 작업은 `skills/application-optimization/references/source-preservation-contract.md`를 따른다.
- 첫 작성 전에 원본의 형식, 페이지 또는 최상위 구조, 제목 위계, 섹션 순서, 문단·목록·표, 이미지·캡션, 반복 패턴을 `intake/source-structure.md`에 블록 순서대로 기록한다.
- `source-locked`는 원본의 형식 골격, 섹션 종류, 블록 템플릿, 표 구조와 자산 연결을 보존한다. 매칭 전략과 근거가 있으면 같은 섹션 안의 글머리표와 반복 단위를 통째로 재배치하고 표현·강조·분량을 조정할 수 있다.
- 섹션·프로젝트·문단의 추가나 삭제, 블록 병합·분할, 최상위 섹션 재배치, 서로 다른 부모 간 블록 이동, 표·페이지 틀 변경은 구조 변경이다. 사용자 승인이나 명시적 제출 규격 없이는 최종본에 적용하지 않는다.
- 원본을 읽지 못했거나 구조 대응표가 없으면 보존을 통과했다고 주장할 수 없다.

## Persistent Profile

- 기준 프로필은 Markdown+YAML 형식의 `inputs/profile/candidate-profile.md`다. YAML에는 `profile_id`, `version`, `updated_at`, `language`를 둔다.
- 경력과 프로젝트에는 변경되지 않는 ID를 부여하고, `evidence-ledger.md`는 `evidence_id`, 주장, 원본 경로, locator, 신뢰도, 상태를 기록한다.
- 인터뷰로 얻은 사실은 출처를 `interview`로, 신뢰도를 `self-reported`로 기록한다. 확인 가능한 원본이 생기면 상태를 올린다.
- 주문을 시작할 때 프로필을 다시 추출하지 않는다. 파일 존재, 버전, 근거 장부만 검증한다.
- 갱신안은 `package/profile-updates/{update_id}/`에 만들고 승인 전에는 기준 프로필을 수정하지 않는다.

## Installation-Free Runtime Policy

1. 현재 AI 클라이언트나 에이전트 런타임에 이미 제공된 파일 읽기, 문서, PDF, 비전, 웹 조사 기능만 사용한다.
2. 프로젝트 실행을 위해 프로그램, 패키지, 런타임 또는 시스템 도구를 설치하지 않는다.
3. 사용자가 터미널 명령을 실행하거나 개발 환경을 설정하도록 안내하지 않는다.
4. 현재 런타임이 입력 포맷을 읽지 못하면 내용을 추측하지 않고 대체 입력 형식을 한두 개만 제시해 다시 요청한다.
5. 현재 런타임이 DOCX를 만들지 못하면 승인된 Markdown을 최종본으로 제공하고 제한을 기록한다.
6. 선택 기능의 부재는 읽을 수 있는 자료로 진행 가능한 핵심 분석과 Markdown 산출을 막지 않는다.

## Quality Loop

- `quality-review`는 이전 단계의 PASS 선언을 신뢰하지 않고 활성 주문, 원본, 구조 명세, 최종 문서를 직접 비교한다.
- 90% 자산은 `package/readiness.md` 판정 시, 10% 산출물은 L5.5에서 검수한다.
- `tailor` 산출물에 원본 바인딩 또는 구조 비교 증거가 없으면 Blocker다.
- 필수 회사 조사 섹션이나 요청된 면접 질문 카테고리·필드가 누락되면 Major 이상이다.
- Blocker 또는 Major가 수정 가능하면 소유 스킬로 돌아가 수정하고 다시 검수한다. 자동 수정·재검수는 최대 2회다.
- 이전 회사 산출물은 새 프로필 버전이나 새 마스터 버전으로 자동 갱신하지 않는다.

## Completion Criteria

- 실행 대상 게이트가 모두 `passed`이고 각 게이트의 실제 산출물이 존재한다.
- 주문의 모든 deliverable이 생성되었거나 지원되지 않는 선택 형식의 Markdown fallback과 사유가 기록되어 있다.
- 모든 `tailor` deliverable이 원본 `source_id`와 연결되고 형식 보존 비교를 통과했다. 전략적으로 바뀐 어휘·강조·순서는 회사 신호와 지원자 근거에 연결돼 있다.
- 사용한 프로필 버전과 마스터 버전이 `worklog.md`에 있다.
- 최종 주장에 대한 근거 연결이 내부 분석 문서에 있고 제출 문서에는 내부 표식이 없다.
- 원본과 승인 전 기준 프로필이 수정되지 않았다.
- PDF 산출물이 생성되지 않았다.
- `review/quality-review.md`가 있고 Blocker와 Major가 없다.
- 지원 건이 끝났으면 `pipeline/application-log.md`와 회고가 갱신됐다.

## Acceptance Checks

환경이 계약대로 동작하는지 확인할 때 다음을 관찰한다.

1. 경험 원재료 목록 없이 직무 축을 확정하지 않고, 목표 지도 없이 3단계를 시작하지 않으며, 마스터 없이 5단계를 시작하지 않는다.
2. Go/No-Go 판정 없이 `outputs/{output_slug}/`가 생기지 않는다. No-Go도 파일로 남는다.
3. 모든 `tailor` 산출물이 실제 source와 연결되고 구조 대응표가 최종본보다 먼저 존재한다.
4. 회사 조사는 조사 계획과 고정 목차 보고서를 만들고 모든 분야의 coverage status를 남긴다.
5. 5단계 산출물에 마스터에 없는 새 사실이 등장하지 않는다.
6. 최종 제출 문서에 근거 ID와 내부 표식이 없다.
7. 인터뷰로 얻은 사실이 `self-reported`로 구분돼 있고 추정치에 범위 표기가 있다.
8. 지원 건이 닫힐 때 회고와 지원 로그가 함께 갱신된다.
9. 마스터가 바뀌면 READY 재판정과 버전 기록이 남는다.
10. PDF 산출물이 생성되지 않는다.
