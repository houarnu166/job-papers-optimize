---
name: pipeline-retro
description: Record funnel results per posting, find where applications stall, and convert the findings into master package updates or follow-up gaps. Use after a rejection, an offer, a silent posting, an assignment result, or an interview round, and when deciding which lifecycle stage to return to.
---

# Pipeline Retro

라이프사이클 7단계다. 합격과 탈락을 지원 건의 끝으로 보지 않고 다음 기회의 READY 수준을 높이는 데이터로 바꾼다. 회고 없이 지원 건을 닫지 않는다.

## Inputs

- `pipeline/postings/{posting_id}.md`, `pipeline/triage/{posting_id}.md`
- `outputs/{output_slug}/`의 지원·과제·면접 산출물과 즉시 복기 기록
- `pipeline/application-log.md`
- `package/readiness.md`와 마스터 자산

## Per-Posting Retro

`pipeline/retrospectives/{posting_id}.md`를 다음 고정 목차로 작성한다.

1. 결과 — 단계별 진행과 최종 결과, 통보일, 통보 방식
2. 사용한 자산 — 마스터 버전, 변형(A/B/C), 앞에 둔 대표 경험, 사용한 경험 카드
3. 실제 반응 — 서류 통과 여부, 과제 피드백, 면접 질문과 면접관 반응, 막힌 지점
4. 잘 작동한 것 — 반응이 좋았던 경험, 표현, 과제 구조
5. 작동하지 않은 것 — 설명이 길어진 지점, 근거가 약했던 주장, 준비되지 않았던 질문
6. 원인 가설 — 사실과 해석을 구분해서 기록
7. 다음 행동 — 승격, 보완, 되돌아갈 단계
8. 소요 — 발견부터 제출까지 걸린 시간과 병목

면접 직후 복기는 기억이 남아 있을 때 즉시 남긴다. 질문, 답변, 막힌 지점, 면접관 반응, 보완할 내용을 그대로 적는다.

## Funnel Analysis

`pipeline/application-log.md`를 갱신하고 누적 데이터를 본다.

- 단계는 발견 → 지원 → 서류 → 과제 → 면접 → 레퍼런스 → 결과다.
- 직무축, 산업, 회사 유형, 사용한 변형별로 통과와 탈락이 집중된 지점을 찾는다.
- 표본이 적으면 결론을 단정하지 않고 관찰로 기록한다. 지원 3건 미만에서 패턴을 확정하지 않는다.

## Promotion And Return

병목의 위치에 따라 되돌아갈 단계를 정한다.

- 목표가 바뀌었거나 공고 자체가 맞지 않았다 → 1단계 `target-map`
- 경험 증거나 개인 기여가 부족했다 → 2단계 `experience-interview`
- 기준본의 순서·표현·분량이 약했다 → 3단계 `ready-package`
- 판정이 잘못돼 준비 비용을 낭비했다 → 4단계 `opportunity-triage`의 기준 보정

승격은 다음 규칙을 따른다.

1. 실제로 반응이 좋았던 표현·경험·구조만 마스터로 올린다. 추측으로 올리지 않는다.
2. 승격 시 `package/`의 해당 파일에 변경 이유와 근거가 된 지원 건을 남긴다.
3. 마스터가 바뀌면 `package/readiness.md`의 READY 판정을 다시 하고 버전을 올린다.
4. 이전 회사별 산출물은 새 마스터 버전으로 소급 갱신하지 않는다.

## Rules

- 탈락 사유를 회사가 알려주지 않았으면 추정임을 명시한다.
- 한 번의 결과로 마스터의 검증된 축을 뒤집지 않는다.
- 부족했던 도메인 지식과 막힌 질문은 보완 과제로 등록하고 담당 단계를 지정한다.
- 개인적인 감정 평가가 아니라 다음 행동으로 바꿀 수 있는 관찰만 기록한다.

## Gate L7 Completion

- 지원 건의 회고 파일이 있고 결과·사용 자산·반응·다음 행동이 채워졌다.
- `pipeline/application-log.md`의 해당 행이 최종 상태로 갱신됐다.
- 승격 또는 보완 항목이 담당 단계와 함께 등록됐다.
- 마스터를 바꿨다면 버전과 변경 이유가 남고 READY 재판정이 이뤄졌다.
