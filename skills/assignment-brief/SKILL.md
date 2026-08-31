---
name: assignment-brief
description: Turn a real pre-interview assignment into a decision document with problem definition, evaluation criteria, alternatives, trade-offs, chosen execution, metrics and risks, while separating given facts, external research and personal assumptions. Use when a company sends a take-home assignment, a case study, or a portfolio deep-dive task, and for building or reviewing mock assignments.
---

# Assignment Brief

라이프사이클 6단계의 사전과제 실행이다. 과제는 결과물 전시가 아니라 의사결정 문서다.

작업 전에 `package/assignment-framework.md`를 읽고 기본 틀을 재사용한다. 틀이 없으면 3단계 `ready-package`로 돌아간다.

## Preflight

1. 제출 조건을 먼저 확인한다 — 마감 일시, 분량 제한, 파일 형식, 제출 경로, 발표 여부.
2. 기밀과 공개 범위를 확인한다 — 회사가 제공한 데이터의 재사용 가능 여부, 내 이전 직장 자료의 사용 가능 범위.
3. 평가 기준을 JD와 과제 문구에서 추출한다. 명시되지 않았으면 JD의 책임·필수요건에서 도출하고 그 사실을 문서에 밝힌다.
4. 결과물 형식이 PDF만 허용되면 이 환경은 Markdown 또는 HTML까지만 만들고 변환은 사용자가 수행한다는 점을 알린다.

## Fact Separation

문서 전체에서 세 가지를 구분해 표기한다.

- **주어진 사실** — 과제 문서와 회사가 제공한 자료에 있는 내용
- **외부 조사** — 공개 자료에서 확인한 내용. 출처와 확인일을 남긴다
- **개인 가정** — 내가 세운 전제. 왜 그렇게 두었는지와 틀렸을 때의 영향을 적는다

가정을 사실처럼 쓰지 않는다. 회사 내부 수치를 추측해 만들지 않는다.

## Structure

`outputs/{output_slug}/assignment/assignment-brief.md`를 다음 순서로 작성한다.

1. 결론 — 첫 화면에서 읽히는 제안과 핵심 지표
2. 문제 정의 — 목표, 고객, 제약, 성공의 정의
3. 평가 기준 — 이 과제가 무엇을 보려 하는지에 대한 해석과 근거
4. 현황 분석 — 주어진 사실, 외부 조사, 가정을 구분한 정리
5. 대안 비교 — 최소 2개 이상, 각 대안의 트레이드오프
6. 선택과 이유 — 판단 기준과 포기한 것
7. 실행 계획 — 순서, 필요한 협업, 일정
8. 성공 지표 — 무엇을 언제 어떻게 측정하는가
9. 리스크와 추가 검증 — 실패 조건과 확인 방법
10. 부록 — 상세 근거, 참고 자료, 초기 스케치

## Review Before Submit

- 결론과 핵심 지표가 첫 화면에서 보이는가.
- 모든 수치에 출처 또는 가정 표기가 있는가.
- 대안을 실제로 비교했는가, 결론을 정당화하는 들러리를 두지 않았는가.
- 분량과 형식이 제출 조건을 지키는가.
- 회사 내부 정보나 이전 직장의 비공개 자료를 노출하지 않았는가.
- 가능한 경우 도메인 리뷰를 받았는가.

## Output Contract

- `assignment/assignment-brief.md` — 제출본
- `assignment/assignment-analysis.md` — 평가 기준 추출, 가정 목록, 검토 기록, 사용한 경험 카드
- 과제에 사용한 이미지·표는 `assets/`에 두고 출처와 재사용 가능 여부를 기록한다

제출 전 `quality-review`를 실행한다. 제출 후 실제 질문과 피드백은 `pipeline/retrospectives/{posting_id}.md`에 남긴다.

## Rules

- 과제 결과를 마스터 자산으로 승격할지는 7단계에서 결정한다.
- 회사가 제공한 데이터와 과제 문구를 이 환경 밖으로 공유하지 않는다.
- 준비된 틀을 그대로 붙여 넣지 않는다. 틀은 구조이고 내용은 이 회사의 문제로 다시 쓴다.
