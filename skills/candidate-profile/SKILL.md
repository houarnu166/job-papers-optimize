---
name: candidate-profile
description: Initialize or update the persistent single-candidate career profile from PDF, DOCX, Markdown, HTML, JSON, or text source materials. Use for first-time onboarding, adding new career facts or projects, resolving profile conflicts, staging evidence-backed profile changes, or applying an explicitly approved profile update. Do not run for ordinary company-specific orders that already have an approved profile.
---

# Candidate Profile

한 명의 지원자에 대한 장기 프로필과 근거 장부를 관리한다. 회사별 지원 작업에서는 이 스킬을 반복 실행하지 않는다.

## Required Files

- Raw sources: `inputs/private/sources/`
- Profile template: `inputs/profile/candidate-profile.template.md`
- Evidence template: `inputs/profile/evidence-ledger.template.md`
- Source map template: `inputs/profile/source-map.template.md`
- Schema: `references/profile-schema.md`
- Approved profile: `inputs/profile/candidate-profile.md`
- Approved evidence: `inputs/profile/evidence-ledger.md`
- Approved source map: `inputs/profile/source-map.md`

PDF를 읽을 때는 `skills/pdf/SKILL.md`, DOCX를 읽을 때는 `skills/docx/SKILL.md`를 함께 사용한다.

## Modes

### Initialize

승인된 프로필이 없을 때만 사용한다.

1. 원본을 읽고 경력, 프로젝트, 역할, 기간, 성과, 도구, 커리어 방향과 인터뷰 스토리를 추출한다.
2. 사실마다 안정적인 `EV-####` 근거 ID와 원본 locator를 부여한다.
3. 상충하거나 불확실한 정보는 최종 프로필에 단정하지 않고 `conflict` 또는 `candidate`로 기록한다.
4. `outputs/_profile-updates/{update_id}/`에 `update-proposal.md`, `evidence-diff.md`, `staged-profile.md`, `evidence-ledger.md`, `source-map.md`와 신규 자산을 작성한다.
5. 사용자에게 변경안 승인을 요청한다. 승인 전 `inputs/profile/`을 수정하지 않는다.

### Update

승인된 프로필과 새 자료의 차이만 분석한다.

1. 기존 프로필·근거 장부를 읽고 신규 자료만 intake한다.
2. 기존 사실을 재작성하지 말고 추가, 수정, 충돌, 폐기 후보로 분류한다.
3. 기존 경력·프로젝트·근거 ID는 같은 대상을 가리키는 한 유지한다.
4. 변경 전후와 이유를 `evidence-diff.md`에 기록한다.
5. 전체 원본을 다시 추출하지 않고 staged profile을 만든다.
6. 사용자 승인을 기다린다.

## Approval Workflow

사용자가 변경안을 명시적으로 승인한 뒤에만 에이전트가 다음 파일 작업을 수행한다.

1. `staged-profile.md`, `evidence-ledger.md`, `update-proposal.md`, `evidence-diff.md`와 source map 변경이 서로 일치하는지 검증한다.
2. 현재 기준 프로필이 있으면 프로필, 근거 장부, source map을 `inputs/profile/history/`에 버전과 승인 시점을 포함한 이름으로 복사한다.
3. staged profile의 `version`을 이전 버전보다 1 높이고 `updated_at`을 승인 시점으로 갱신한다. 최초 승인 버전은 1이다.
4. staged profile과 staged evidence ledger를 각각 `inputs/profile/candidate-profile.md`, `inputs/profile/evidence-ledger.md`에 반영한다.
5. staged source map과 신규 자산이 있으면 기존 파일을 임의로 덮어쓰지 않도록 충돌을 확인한 뒤 `inputs/profile/source-map.md`와 `inputs/profile/assets/`에 반영한다.
6. 업데이트 폴더에 승인 시점, 반영 버전, 반영 파일, 사용자 승인 문구를 담은 `decision.md`를 작성한다.
7. 반영된 기준 파일을 다시 읽어 버전, 근거 ID, 링크와 파일 경로를 검증한다.

명령 실행이나 별도 프로그램은 필요하지 않다. 거절하거나 승인 의사가 불명확하면 기준 프로필을 수정하지 않고 `decision.md`에 상태만 기록한다.

## Evidence Rules

- 검증 가능한 사실만 `verified`로 둔다.
- PDF locator는 페이지, DOCX/MD/HTML은 제목·문단, JSON은 JSON path를 사용한다.
- 정량 수치는 원본에 정확히 있을 때만 프로필에 넣는다.
- 추정, 해석, 회사별 포지셔닝은 영구 프로필 사실로 저장하지 않는다.
- 연락처와 민감정보는 지원에 필요한 최소 범위만 유지한다.

## Completion

- staged profile이 Markdown+YAML 스키마를 만족한다.
- 모든 주요 경력·프로젝트 주장에 근거 ID가 있다.
- 변경 제안과 상충 정보가 분리되어 있다.
- 승인 전 기준 프로필이 변경되지 않았다.
