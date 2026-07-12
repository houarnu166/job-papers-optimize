# Profile Schema

## YAML Front Matter

```yaml
profile_id: stable-single-candidate-id
version: 1
updated_at: 2026-01-01T09:00:00+09:00
language: ko
```

`profile_id`는 환경 수명 동안 바꾸지 않는다. `version`은 승인된 갱신마다 1 증가한다.

## Required Sections

1. Professional Summary
2. Career Direction
3. Career History
4. Projects
5. Skills
6. Verified Outcomes
7. Interview Story Bank
8. Constraints And Unknowns

경력 ID는 `career-{organization}-{role}`, 프로젝트 ID는 `project-{short-name}`, 스토리 ID는 `story-{short-name}` 형식을 사용한다. 동일 대상을 수정할 때 ID를 바꾸지 않는다.

## Evidence Ledger

| Field | Values |
|---|---|
| Evidence ID | `EV-####` |
| Source Path | Project-relative path |
| Locator | Page, heading/paragraph, or JSON path |
| Confidence | `high`, `medium`, `low` |
| Status | `verified`, `candidate`, `conflict`, `retired` |

최종 지원 문구는 원칙적으로 `verified` 근거만 사용한다. `candidate`와 `conflict`는 사용자 확인 전까지 계획 문서에만 남긴다.
