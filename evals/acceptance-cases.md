# Harness Acceptance Cases

이 문서는 에이전트가 개선판의 핵심 계약을 회귀 검증할 때 사용하는 익명 시나리오다. 사용자가 직접 실행할 필요는 없다.

## Case 1: Linear Source-Faithful Application

입력:

- `orders/example-linear.md`
- 익명 profile, resume Markdown, portfolio JSON
- resume, portfolio, full interview 요청

반드시 관찰할 결과:

1. Gate 0~6이 순서대로 진행된다.
2. resume와 portfolio에 서로 다른 source ID가 연결된다.
3. material inventory와 source structure가 final draft보다 먼저 생성된다.
4. company research는 research plan과 고정 1~9장 보고서를 만든다.
5. research plan은 8개 조사 분야를 순서대로 모두 방문하고 각 상태를 기록한다.
6. resume analysis와 portfolio plan이 생성된다.
7. final resume는 원본 Markdown 구조, final portfolio는 원본 JSON 구조의 읽기 순서를 유지한다.
8. full interview는 실무 12개, 임원·문화 12개 이상과 질문별 8개 필드를 갖는다.
9. final submission documents에 evidence ID가 없다.
10. quality review가 source block 수와 deviation을 직접 비교한다.

## Case 2: Missing Original Document

입력:

- 승인 profile만 존재
- 사용자가 기존 이력서 최적화를 요청
- 이력서 원본은 제공되지 않음

기대 판정:

- order는 `operation: tailor`을 유지한다.
- Gate 1은 `needs-user`다.
- 에이전트는 원본 이력서를 요청한다.
- profile로 generic resume를 만들어 완료하지 않는다.
- `operation: create`로 자동 변경하지 않는다.

## Case 3: Generic Rewrite Regression

입력 조건:

- order에 `preservation: structure`만 있고 source ID가 없음
- material inventory와 source structure가 없음
- final resume와 portfolio가 generic template으로 작성됨
- final document에 `EV-####`가 노출됨

기대 판정:

- 이전 `structure`는 `source-locked`로 해석한다.
- source 미연결과 structure map 부재는 Blocker다.
- generic template 대체와 evidence tag 노출은 Major다.
- quality review는 PASS를 줄 수 없다.

## Case 4: Research Compression Regression

입력 조건:

- company report가 짧은 요약 7개 섹션만 포함
- research plan이 없음
- fixed report 1~9장과 required tables가 없음

기대 판정:

- research plan 부재와 report contract 누락은 Major다.
- 정보가 없는 섹션은 삭제하지 않고 확인되지 않음과 조사 한계를 기록하게 돌려보낸다.

## Case 5: Interview Compression Regression

입력 조건:

- 면접 scope 미지정 상태에서 전체 준비 요청
- practical 8문항만 있고 executive 질문 없음
- 질문별 의도, 근거, 꼬리질문 또는 함정이 일부 없음

기대 판정:

- scope 기본값은 `full`이다.
- 질문 수와 question contract 미충족은 Major다.
- interview-prep 소유 단계로 remediation한다.

## Case 6: PDF Portfolio With Images

입력:

- 여러 페이지의 portfolio PDF
- Markdown 최적화 요청, `source-locked`

반드시 관찰할 결과:

1. 페이지 수, 페이지별 block order, 이미지와 캡션을 source structure에 기록한다.
2. 추출 가능한 이미지는 asset inventory와 source block에 연결한다.
3. final Markdown은 페이지와 케이스 순서를 바꾸지 않는다.
4. 이미지 누락이나 텍스트-only 대체는 Major다.
5. PDF output은 생성하지 않는다.

## Case 7: Flexible Research Only

입력:

- company research만 요청
- resume와 portfolio 수정은 요청하지 않음

기대 판정:

- Gate 0, Gate 2와 research quality review만 실행한다.
- application 문서를 억지로 만들지 않는다.
- research plan, posting snapshot, source ledger와 fixed report는 생략하지 않는다.

## Completion Rule

모든 케이스의 기대 판정을 `AGENTS.md`와 로컬 skill references만 읽고 일관되게 결정할 수 있어야 한다. 어느 판정이 모호하면 해당 계약을 먼저 수정한 뒤 실제 지원 작업을 진행한다.
