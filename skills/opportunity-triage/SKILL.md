---
name: opportunity-triage
description: Capture a discovered job posting with its original text and deadline, classify it against the target map, and decide Go, conditional Go, or No-Go with recorded reasons before any tailoring work starts. Use when a new posting is found, when deciding whether a posting is worth applying to, or when several postings compete for limited time.
---

# Opportunity Triage

라이프사이클 4단계다. 모든 공고에 반응하지 않고, 준비한 증거가 읽힐 기회만 빠르게 선택한다. 이 판정 없이 5단계를 시작하지 않는다.

## Inputs

- 공고 원문 또는 URL, 발견 경로
- `package/target-map.md`, `package/jd-scorecards/`, `package/readiness.md`
- `inputs/profile/candidate-profile.md`와 근거 장부

## Capture

발견 즉시 `pipeline/postings/{posting_id}.md`를 만든다. `posting_id`는 `{회사}-{직무}-{발견일}` 형태로 사람이 읽을 수 있게 만든다.

1. 원문 보존 — 공고 본문을 그대로 저장한다. URL만 남기지 않는다. 원문을 얻지 못하면 확보한 범위와 누락을 명시한다.
2. 메타 — 회사, 조직·팀, 직무명, 고용 형태, 근무지, 발견일, 마감일, 출처, 링크
3. 요건 — 핵심 업무, 필수요건, 우대요건, 제출물, 전형 절차와 일정
4. 지도 연결 — 목표 직무 A/B/C 중 어느 경로인지, 기업 지도상의 위치
5. 관련 공고 — 같은 회사의 중복 공고, 계열사, 인접 역할

마감일이 없으면 롤링 채용으로 간주하고 조기 마감 가능성을 기록한다.

## Decision

`pipeline/triage/{posting_id}.md`에 판정을 남긴다. No-Go도 반드시 기록한다.

판정 기준:

1. **필수요건** — 충족하거나, 설득할 직접 증거가 있는가. 없으면 그 요건과 공백을 적는다.
2. **대표 경험** — 준비된 경험 2~3개로 핵심 업무와 문제를 설명할 수 있는가.
3. **전략적 가치** — 직무·산업·커리어 방향에서 이 기회가 갖는 의미와 준비 비용의 비교.
4. **일정 현실성** — 마감, 과제, 면접 일정을 현재 업무와 병행할 수 있는가.
5. **패키지 상태** — 필요한 마스터와 변형 레시피가 준비돼 있는가. 없으면 조건부다.

결과는 셋 중 하나다.

- `Go` — 즉시 5단계를 시작한다. 사용할 변형(A/B/C)과 목표 제출일을 함께 정한다.
- `조건부 Go` — 무엇이 충족되면 진행하는지 조건과 확인 시점을 적는다.
- `No-Go` — 이유를 적는다. 요건 공백이면 보완 과제로, 목표 불일치면 목표 지도 갱신 후보로 연결한다.

## Output Contract

`pipeline/triage/{posting_id}.md`의 고정 목차.

1. 판정 — `Go` / `조건부 Go` / `No-Go`, 판정일, 판정 근거 요약
2. 요건 대조표 — 필수·우대 요건별 대응 경험, 근거 ID, 충족 여부
3. 대표 경험 구성 — 이 공고에서 앞에 둘 경험 2~3개와 이유
4. 전략적 가치와 비용
5. 일정 — 마감, 목표 제출일, 예상 작업량, 병행 가능성
6. 조건 또는 보류 사유 — 조건부·No-Go일 때 필수
7. 다음 행동 — 5단계 시작, 조건 확인, 보완 과제 등록 중 하나

판정 후 `pipeline/application-log.md`에 한 행을 추가한다. Go일 때만 `outputs/{output_slug}/`를 만든다.

## Rules

- 준비되지 않은 상태에서 마감이 임박했다는 이유만으로 품질을 희생하는 지원을 권하지 않는다.
- 필수요건 미충족을 "설득 가능"으로 낙관 처리하지 않는다. 설득할 직접 증거를 명시하거나 공백으로 남긴다.
- 공고에 없는 정보를 회사 일반론으로 채우지 않는다. 회사 조사는 5단계 `company-research`의 일이다.
- 조기 마감 가능성이 있으면 목표 제출일을 앞당겨 제안한다. 발표 근거는 공고 발견 후 1~2주 안 제출이다.
