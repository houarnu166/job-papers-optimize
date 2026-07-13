---
order_id: company-role-YYYYMMDD
status: draft
mode: linear
output_slug: 회사명-직무명
research_depth: standard
profile:
  path: inputs/profile/candidate-profile.md
  version: latest
target:
  company: ""
  product: ""
  role: ""
  language: ko
  application_stage: application
job_posting:
  url: ""
  full_text: ""
  deadline: ""
materials:
  primary:
    - id: resume-source
      role: resume
      path: ""
      authority: source
  supplemental: []
interview:
  scope: full
  answer_length: 60-120-seconds
  known_stage: ""
  interviewers: []
deliverables:
  - type: resume
    operation: tailor
    source_id: resume-source
    format: md
    preservation: source-locked
constraints:
  tone: professional-natural
  length: source-compatible
  structural_changes: require-user-approval
  must_include: []
  must_avoid: []
  submission_rules: ""
---

# Order Notes

이 파일은 에이전트가 자연어 대화에서 내부 주문을 생성할 때 사용하는 템플릿이다. 사용자에게 복사하거나 직접 편집하도록 요구하지 않는다.

기존 문서 개선은 `operation: tailor`와 실제 `source_id`를 사용한다. 새 문서 작성은 사용자가 명시했을 때만 `operation: create`, `preservation: not-applicable`로 둔다. PDF는 입력 자료로만 지정할 수 있고 deliverable 형식으로 사용할 수 없다.
