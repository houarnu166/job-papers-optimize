# 라이프사이클 환경 리빌딩 계획

작성일: 2026-07-30
근거: `inputs/IT 대기업 상향 이직 웨비나/it-career-lifecycle-execution-guide.html` (7단계·20작업)
목표: 웨비나 라이프사이클을 반복 실행할 수 있는 환경으로 전면 재설계하고, 그 위에서 90% Ready-made 패키지를 실제로 구축해 READY 게이트와 리허설까지 통과한다.

## 확정된 결정

1. 환경 전면 재설계. 기존 Gate 0~6은 폐기하지 않고 5·6단계 실행 절차로 흡수한다.
2. 마스터 문서는 각 1벌만 유지하고, 직무 A/B/C 차이는 변형 레시피로 관리한다.
3. `experience-interview` 스킬을 신설해 본인만 아는 사실을 2단계 정식 절차로 확보한다.
4. 포트폴리오 마스터는 47p 페이지 편집 지시서로 산출한다. PDF·Figma 실작업은 범위 밖이다.
5. 완료 기준은 READY 게이트 통과 + 공고 1건 리허설(4~7단계 완주)이다.
6. 새 환경에 불필요한 하네스·산출물은 제거한다. 오직 새 환경을 위한 리빌딩이다.

가정: 자기소개서는 마스터를 만들지 않고 "지원 동기 골격 + 경험 연결 규칙"만 90% 자산으로 두며, 완성본은 5단계에서 생성한다.

## 목표 디렉터리 계약

```text
AGENTS.md                     # 7단계 운영 모델 (재작성)
README.md                     # 실사용 안내 (재작성)
THIRD_PARTY_NOTICES.md        # pdf 스킬 파생 고지 (유지)
REBUILD-PLAN.md               # 이 문서. Phase 5 완료 후 제거
inputs/
  profile/                    # 사실 장부: candidate-profile, evidence-ledger, source-map
  private/sources/            # 원본 JSON 7종 (읽기 전용)
  주로제출하던이력서와포트폴리오/  # 제출 원본 7종 (읽기 전용, 마스터의 source)
  IT 대기업 상향 이직 웨비나/     # 라이프사이클 근거 (유지)
package/                      # 90% Ready-made 자산 (반복 재사용)
  target-map.md               # 직무 A/B/C, 산업·기업 지도, 감지 체계
  experience-assets/          # 경험 카드 (문제–판단–행동–결과–학습)
  jd-scorecards/              # 직무별 채점표 기준본
  master/                     # resume.md, career-history.md, portfolio-storyboard.md, cover-letter-skeleton.md
  variants.md                 # 직무축별 변형 레시피
  assignment-framework.md     # 사전과제 기본 틀 + 모의 과제
  interview-assets.md         # 경험 자산 8개 + 레퍼런스 준비
  readiness.md                # READY 3축 판정 기록
pipeline/                     # 공고별 운영 기록
  postings/                   # JD 원문·발견일·마감일·출처
  triage/                     # Go / 조건부 Go / No-Go 판정
  application-log.md          # 발견–지원–서류–과제–면접–레퍼런스 퍼널
  retrospectives/             # 건별 회고와 마스터 승격 제안
outputs/{공고}/               # 회사별 10% 산출물 (기존 산출물 계약 유지)
skills/
```

## 스킬 체계

| 단계 | 스킬 | 상태 |
|---|---|---|
| 1 | `target-map` | 신설 |
| 2 | `experience-interview` | 신설 |
| 2 | `candidate-profile` | 개편 (사실 장부 담당으로 축소) |
| 3 | `ready-package` | 신설 |
| 4 | `opportunity-triage` | 신설 |
| 5 | `start-application` | 개편 (10% 진입점·주문·소스 잠금) |
| 5 | `company-research` | 유지 (보고서 계약 존치) |
| 5 | `application-optimization` | 개편 (마스터→10% 변형 기준으로 재정의, 원본 보존 계약 존치) |
| 6 | `assignment-brief` | 신설 |
| 6 | `interview-prep` | 확장 (컬처핏·레퍼런스·즉시 복기 흡수) |
| 7 | `pipeline-retro` | 신설 |
| 공통 | `quality-review` | 유지 (검수 계약 존치) |
| 공통 | `document-export` | `docx` + `document-output` 병합 |
| 공통 | `pdf` | 유지 (입력 전용) |

## 게이트 재설계

- **L1 목표 확정** — 직무 A/B/C 정의와 감지 체계가 실제로 동작한다.
- **L2 증거 검증** — 모든 강한 주장이 verified이거나 추정·범위로 표기됐다. 충돌 수치가 해소됐다.
- **L3 READY** — 서류·전형·면접 3축 테스트 통과 + 리허설로 병목과 소요시간이 기록됐다.
- **L4 Go/No-Go** — 판정과 근거가 `pipeline/triage/`에 남았다.
- **L5 제출** — 원본 잠금 → 조사 → 매칭 → 초안 → 독립 검수 (구 Gate 1~4·6).
- **L6 전형 실행** — 과제·면접·레퍼런스 실행과 즉시 복기가 기록됐다.
- **L7 회고** — 퍼널 병목이 마스터 승격 또는 보완 과제로 전환됐다.

## 진행 상태

| Phase | 상태 | 비고 |
|---|---|---|
| 0 정리 | 완료 (2026-07-30) | outputs 전체 비움, 배포용 자산·구 주문 스키마·평가 케이스 제거, docx+document-output 병합 |
| 1 하네스 재작성 | 완료 (2026-07-30) | AGENTS.md 재작성, 스킬 14종 확정, package/pipeline 골격과 .gitignore 갱신 |
| 2 원재료 목록화 + 목표 지도 | 완료 (2026-07-31) | 작업 단위 32건 나열, JD 6건 수집, 단일 직무축 + 산업 3축(B2B SaaS / AI / 에너지) 확정. **L1 통과** |
| 3 경험 자산 | 진행 중 | 대표 경험 카드 10건 중 6건 완료, 1건 초안. 세션 인계 상세는 `HANDOFF.md`(로컬 전용) |
| 4 90% 패키지 | 대기 | |
| 5 READY + 리허설 | 대기 | |

## 실행 순서

### Phase 0 — 정리

1. `outputs/` 전체 비우기 (git 미추적, 복구 불가 — 실행 직전 재확인). 2026-07-27 진단은 구 기준의 판단이므로 이관하지 않는다. 문서 판정은 3단계에서 제출 원본을 다시 읽어 웨비나 기준으로 새로 내린다.
3. 제거: `inputs/examples/`, `inputs/profile/*.template.md`, `orders/` 전체, `evals/`, `LICENSE`.
4. `skills/docx` + `skills/document-output` → `skills/document-export` 병합.

### Phase 1 — 하네스 재작성

1. `AGENTS.md` 재작성: 7단계 운영 모델, 90%/10% 분리, L1~L7 게이트, 디렉터리 계약, 상태 판정 규칙.
2. 신설 스킬 6종 작성, 기존 스킬 5종 개편, 계약 문서 4종 이식.
3. `README.md` 실사용 안내로 재작성.
4. 새 기준의 수용 케이스를 `AGENTS.md` 안 또는 별도 최소 문서로 재정의.

### Phase 2 — 1단계 실행

1. 경험 원재료 목록화 — 회사·기간별 프로젝트와 루틴 업무 전수 나열, 프로필 미반영 경력의 최소 사실 확인 → `package/experience-inventory.md`.
2. 목표 직무 A/B/C 정의, 반복 요건과 증거 대조, 산업·기업 지도, 공고 감지 체계 → `package/target-map.md`. **L1 게이트.**

웨비나 원본의 순서(업무·경험 목록화 → 경험 재해석 → 세부 직무 A/B/C → 산업·기업 → 실행 계획, `[02:04:50–02:08:13]`)를 따른다. 가고 싶은 회사에서 역산해 직무를 정하지 않는다.

### Phase 3 — 2단계 실행

1. `experience-interview` 세션: A사 2025~현재 경력, 충돌 수치 3건, 면접 경험 자산 소재.
2. 경험 카드화 → `package/experience-assets/`.
3. 프로필 v2 갱신안 작성 → 사용자 승인 후 반영. **L2 게이트.**

### Phase 4 — 3단계 실행

1. JD 채점표 기준본.
2. 마스터 이력서·경력기술서 — 제출 원본을 다시 읽고 웨비나 3단계 기준(첫 화면 직무 정체성·대표 성과, JD 요건별 증거 연결, 설명 못 할 표현 삭제)으로 판정·구성.
3. 포트폴리오 페이지 편집 지시서 — 47p를 페이지별로 유지·압축·이동·삭제·신규 판정.
4. 자소서 골격, 사전과제 틀 + 모의 과제 1편, 면접 경험 자산 8개 + 레퍼런스 준비.
5. 변형 레시피.

### Phase 5 — READY + 리허설

1. 서류·전형·면접 3축 테스트 → `package/readiness.md`.
2. 공고 1건으로 4~7단계 완주, 병목·소요시간 기록. **L3 게이트.**
3. 리허설 결과를 마스터에 반영하고 이 문서를 제거.

## 열린 질문

1. A사(2025~현재) 회사·역할·재직 여부·노출 범위 — Phase 3 인터뷰 1순위.
2. 목표 직무 A/B/C 확정 — Phase 2에서 함께 결정. 진단 가설: A=복잡한 데이터·시스템 프로덕트 디자인, B=AI 프로덕트, C=디자인 시스템·디자인옵스.
3. 리허설용 JD 출처 — 실제 관심 공고 여부.
