---
name: quality-review
description: Independently review company-specific application, interview, Markdown, DOCX, and HTML outputs for profile-version integrity, evidence coverage, truthfulness, source-structure preservation, format compliance, ATS readability, asset handling, and submission readiness. Use as the final gate and after each remediation cycle.
---

# Quality Review

## Inputs

- Read the active order, `worklog.md`, `source-ledger.md`, approved profile and evidence ledger.
- Review all files under the order's output folder.
- Compare final materials with source structure and approved Markdown.
- Write only under `outputs/{output_slug}/review/`.

## Checks

- Profile integrity: worklog version matches the profile used at execution time; SHA-256 matches when available, otherwise the hash limitation and `updated_at` are recorded.
- Evidence: important claims map to verified evidence IDs; conflicts and unsupported metrics are excluded.
- Truth: no invented employer, project, role, tool, award, domain or outcome.
- Requirement coverage: every requested deliverable and major role requirement is addressed.
- Structure: heading hierarchy, section order, paragraph boundaries, lists, tables, image order and captions are preserved as requested.
- Cross-document consistency: resume, portfolio, cover letter and interview materials tell the same factual story.
- Company-name discipline: resumes and portfolios do not repeat the target company unnecessarily.
- ATS/readability: standard headings, readable text flow, sensible keyword use and no content hidden only in images.
- Identity details: dates, role titles, contact details and links are internally consistent.
- Assets: image paths work, captions are present and aspect ratios are not distorted.
- DOCX: structural QA passed; visual QA status is stated and visual defects are Blockers when render QA was performed.
- Format fallback: requested DOCX or HTML that was unavailable is replaced by the same approved Markdown, and the reason is disclosed in the worklog and export notes.
- HTML: links, assets, overflow and layout behavior are checked.
- Output isolation: no final file exists outside the order output folder and no PDF output exists.

## Severity And Loop

- `Blocker`: false claim, wrong target, broken core Markdown output, missing required content, unresolved profile conflict used in final copy, or PDF output.
- `Major`: unsupported claim, inconsistent positioning, broken structure preservation or important requirement gap.
- `Minor`: wording or polish issue.

An unavailable optional export is not a Blocker when the approved Markdown fallback is complete and the limitation is clearly disclosed. Do not mark a DOCX or HTML file as reviewed when it was not created.

Write `quality-review.md` with verdict, findings, requirement coverage, evidence check and fix list. Route fixable Blocker and Major findings to the owning skill, then re-run review. Allow at most 2 remediation cycles. If a Blocker remains, record the order as blocked and request user input.
