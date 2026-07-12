---
name: company-research
description: Research a target company and role for a specific job order, analyze the job posting, and create a source-backed application brief. Use for company, product, market, design organization, hiring role, culture, interview context, or job-posting analysis under a company-specific output folder.
---

# Company Research

## Inputs

- Read the exact active order.
- Validate the approved profile path and record its version and SHA-256 in `worklog.md` when the runtime can calculate it. Otherwise record `updated_at` and the hash limitation.
- Write only under `outputs/{output_slug}/research/` plus the shared `source-ledger.md`.

## Workflow

1. Confirm company identity, role, application stage, posting source and submission rules.
2. Save the provided or retrieved posting as `research/job-posting.md` so expired URLs do not erase the evidence.
3. Separate responsibilities, required skills, preferred skills, collaboration context and evaluation signals.
4. Research company basics, products, customers, business model, recent developments and role-relevant risks.
5. Research product/design environment only when reliable information exists.
6. Write `research/company-job-analysis.md` with facts, interpretations and unknowns clearly separated.

`research_depth: standard`은 직무와 지원 전략에 직접 필요한 범위만 조사한다. `deep`은 경쟁사, 재무·투자, 조직 문화, 디자인 조직과 최근 동향을 추가하되 근거 없는 조직 내부 정보는 만들지 않는다.

## Sources

공식 채용공고, 회사 사이트, 공시·투자자 자료, 공식 블로그와 발표를 우선한다. 후기와 익명 커뮤니티는 관찰 신호로만 사용한다. 외부 주장마다 `source-ledger.md`에 날짜, URL, 용도, 신뢰도와 주석을 남긴다.

현재 런타임에 웹 조사 기능이 없으면 설치나 설정을 요구하지 않는다. 사용자가 제공한 채용공고와 회사 자료만 사용하고 조사 범위 제한을 명시한다. 핵심 판단에 꼭 필요한 경우에만 공식 페이지 내용이나 링크 제공을 요청한다.

## Report

1. Executive Summary
2. Company And Product Context
3. Role Requirements
4. Product And Design Environment
5. Candidate Fit Signals
6. Risks, Unknowns And Verification Needs
7. Recommended Application Strategy
