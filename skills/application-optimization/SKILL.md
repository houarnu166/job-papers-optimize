---
name: application-optimization
description: Tailor resumes, cover letters, portfolios, and application strategy to a target company and role using an approved persistent candidate profile and evidence ledger. Use for requirement matching, capability assessment, evidence selection, Markdown application drafts, source-structure preservation, and company-specific change tracking.
---

# Application Optimization

## Inputs

- Read the active order, approved candidate profile and evidence ledger.
- Read `research/company-job-analysis.md` when present.
- Read supplemental materials only when the order lists them.
- Do not re-intake all raw career sources for an ordinary company order.
- Write only under `outputs/{output_slug}/application/`.

## Truth And Identity

- Use approved profile facts and `verified` evidence.
- Order-local supplemental facts may be used when directly verified, but they do not mutate the persistent profile.
- Do not invent employers, projects, tools, metrics, awards or domain experience.
- Keep the candidate's existing direction and voice; adjust emphasis rather than identity.

## Workflow

1. Write `capability-assessment.md` covering strengths, gaps, domain/platform experience, methods and reusable interview stories.
2. Write `requirement-evidence-matrix.md` mapping every important role requirement to evidence IDs, strength and gaps.
3. Write `matching-strategy.md` with positioning, priority messages, keyword guidance and risks.
4. Produce requested Markdown files: `resume.md`, `cover-letter.md`, `portfolio.md`.
5. Write `change-log.md` with source section, output section, change type, reason and evidence IDs.
6. Write `submission-package.md` listing requested and optional artifacts.

## Structure Preservation

- Preserve heading hierarchy, section order, paragraph boundaries, lists, tables, image order and captions unless the order explicitly requests `redesign`.
- Use `<!-- source-page: N -->` markers when the source is PDF.
- Preserve JSON keys when an order explicitly requests JSON analysis, but Markdown remains the default final format.
- Do not collapse distinct source paragraphs into generic summaries without recording the change.

## Style

- Use company names in cover letters and research where natural; use them sparingly in resumes and portfolios.
- Prefer problem, action and outcome language backed by evidence IDs.
- Keep ATS keywords natural and never keyword-stuff.
- Put unsupported claims in planning notes as `확인 필요`, never in final application copy.
