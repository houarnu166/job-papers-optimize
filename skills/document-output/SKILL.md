---
name: document-output
description: Convert approved Markdown job-application content into optional DOCX or HTML without rewriting the content. Use only when a job order explicitly requests DOCX or HTML, source-aware layout preservation, reusable images, or a page-like HTML presentation. PDF output is not supported.
---

# Document Output

## Contract

- Read approved Markdown from `outputs/{output_slug}/application/`.
- Write optional final files under `outputs/{output_slug}/exports/`.
- Store extracted or reusable images under `outputs/{output_slug}/assets/`.
- Never create or convert to PDF.
- Never rewrite content during format conversion.

## Routing

- DOCX: read `skills/docx/SKILL.md`.
- HTML: use this skill and preserve the approved Markdown structure.
- PDF source intake: read `skills/pdf/SKILL.md`; PDF remains input-only.
- Final exports: send to `quality-review`.

## DOCX

Use DOCX for editable resumes and cover letters when requested and supported by the current runtime. Preserve section order, heading hierarchy, paragraph boundaries, tables and image placement. Use a conservative layout and record whether visual render QA was available. Do not promise pixel-perfect portfolio reproduction. If DOCX creation is unavailable, keep the approved Markdown as the final submission source and disclose the fallback without asking for an installation.

## HTML

Use HTML for requested visual portfolios or layout-aware documents. Preserve case-study order, images, captions and evidence. For page-like sources, derive each page's aspect ratio when it is observable and use explicit page containers, stable dimensions, consistent margins, print CSS, controlled page breaks and non-distorting image sizing. Keep text within page bounds and create additional pages instead of shrinking content unpredictably. Do not add a marketing landing page or decorative redesign unless requested.

## Verification

Check output type, content equality against approved Markdown, text overflow, missing images, broken links and structure order. Write `exports/export-notes.md` with source Markdown, requested format, delivered format, output files, assets, layout assumptions, runtime capabilities used and QA limitations.
