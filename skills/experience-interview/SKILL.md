---
name: experience-interview
description: Interview the candidate to recover facts that no source file contains, then convert each experience into a problem-judgment-action-result-learning asset card with verified personal contribution. Use when career facts are missing or conflicting, when recent employment is not in the profile, when metrics lack a calculation basis, or when interview experience assets such as failure, conflict, persuasion and urgent decisions are needed. Never invent numbers or fill gaps with plausible wording.
---

# Experience Interview

라이프사이클 2단계다. 파일을 아무리 읽어도 나오지 않는 사실을 사용자에게서 직접 얻어 재사용 가능한 경험 자산으로 바꾼다.

1단계에서 만든 경험 원재료 목록을 심화하는 단계다. 원재료 목록이 없으면 `target-map`의 Step 0을 먼저 실행한다. 1단계에서는 최근 경력의 최소 사실(회사·기간·역할·범위)만 확인하고, 판단·성과·실패 사례는 여기서 다룬다.

## When To Run

- 프로필에 없는 재직·프로젝트가 제출 원본이나 대화에 나타났을 때
- 근거 장부에 `conflict` 또는 `candidate` 상태의 사실이 있을 때
- 수치의 기준 시점, 비교 대상, 계산 근거가 없을 때
- 면접용 경험 자산(성과, 실패, 갈등, 반대 의견, 설득, 고객 문제, 긴급 판단, 구조 개선)이 부족할 때

## Preparation

1. `package/experience-inventory.md`, `package/target-map.md`, `inputs/profile/`, `inputs/private/sources/`, 제출 원본을 먼저 읽는다.
2. 이미 확인 가능한 사실은 질문하지 않는다. 파일에서 확인된 내용은 질문 대신 "이렇게 기록돼 있는데 맞는지"로 확인한다.
3. 공백 목록을 만든다. 1단계의 원재료 목록과 요건-증거 대조표에서 비어 있는 항목이 출발점이다. 각 공백에 왜 필요한지(어느 직무축의 어느 요건을 증명하는지)를 붙인다.
4. 질문 순서는 영향이 큰 것부터다. 최신 경력 > 충돌 사실 > 대표 경험의 판단 근거 > 면접 자산 순으로 둔다.

## Session Rules

- 한 번에 3~5개 질문만 한다. 답변을 받은 뒤 다음 묶음으로 넘어간다.
- 원하는 답을 암시하지 않는다. "성과가 있었죠?"가 아니라 "무엇이 어떻게 달라졌고 무엇으로 확인했는가"를 묻는다.
- 숫자를 요구하지 않는다. 숫자가 없으면 오류, 시간, 실패율, 만족도, 클레임, 재작업, 문의량처럼 확인 가능한 변화를 찾는다.
- 팀 성과와 본인 판단·행동을 분리해 묻는다.
- 모르거나 기억나지 않으면 그대로 기록한다. 사용자가 답하지 않은 항목을 추정으로 채우지 않는다.
- 공개 범위를 확인한다. 재직 중인 회사, 사명 비공개, NDA 대상은 표기 방법을 함께 정한다.

## Question Set

각 경험마다 다음을 확보한다.

1. 문제 또는 목적은 무엇이었는가. 누가 어떤 상황에서 곤란했는가.
2. 내 역할과 팀의 역할은 어디까지였는가. 내가 직접 결정한 범위는 무엇인가.
3. 어떤 대안이 있었고 무엇을 기준으로 선택했는가. 포기한 대안은 무엇인가.
4. 실제로 무엇을 만들고 조율했는가. 누구와 어떻게 합의했는가.
5. 무엇이 달라졌는가. 그것을 무엇으로 확인했는가. 기준 시점과 비교 대상은 무엇인가.
6. 무엇을 배웠고 다음 업무에서 어떻게 다시 썼는가.
7. 이 경험에서 가장 아팠던 지점은 무엇인가. 다시 한다면 무엇을 바꾸겠는가.

## Output Contract

경험마다 `package/experience-assets/{asset_id}.md`를 다음 고정 목차로 작성한다.

1. 메타 — asset_id, 관련 직무축(A/B/C), 조직, 기간, 한 줄 결론
2. 문제와 목적
3. 역할 경계 — 내 역할, 팀 역할, 직접 결정 범위
4. 판단 — 선택한 대안, 포기한 대안, 판단 기준, 제약
5. 행동 — 실제 산출물, 협업과 합의 과정, 갈등과 처리
6. 결과 — 정량(값, 기준 시점, 비교 대상, 계산 근거, 확인 방법), 정성
7. 학습과 재현 — 다음 업무에서 다시 쓴 방식
8. 증거 상태 — 근거 ID, 신뢰도(`verified`, `self-reported`, `estimated`), 확인 필요 항목
9. 예상 후속 질문 — 데이터, 대안, 실패, 확장성 각 1개 이상과 답변 뼈대
10. 공개 제약 — 사명·수치·이미지의 사용 가능 범위

인터뷰로 새로 확인된 사실은 `candidate-profile` 스킬의 Update 모드로 넘겨 `package/profile-updates/{update_id}/`에 갱신안을 만든다. 이 스킬은 기준 프로필을 직접 수정하지 않는다.

## Evidence Rules

- 인터뷰 답변은 근거 장부에 출처 `interview`, 신뢰도 `self-reported`로 등재한다.
- 확인 가능한 원본(계약서, 지표 화면, 회의록, 릴리스 노트)이 나중에 제공되면 상태를 올리고 locator를 채운다.
- 값이 불확실하면 단일 숫자 대신 범위와 `추정`을 함께 기록한다.
- 충돌하던 수치는 사용자가 확정한 값과 그 근거를 남기고, 확정하지 못하면 문서에서 그 수치를 쓰지 않는 선택지를 제시한다.

## Gate L2 Contribution

- 목표 직무축별 대표 경험 2~3개가 카드로 존재한다.
- 각 카드에 개인 기여와 판단 기준이 팀 성과와 분리돼 있다.
- 면접 경험 자산 8개 유형이 채워졌거나 부족분이 보완 과제로 등록됐다.
- 모든 강한 주장이 `verified`이거나 `self-reported`/`estimated`로 표기됐다.
