---
name: document-output
description: Convert approved Markdown job-application content into optional DOCX or HTML without rewriting the content. Use only when a job order explicitly requests DOCX or HTML, source-aware layout preservation, reusable images, or a page-like HTML presentation. PDF output is not supported.
---

# Document Output

## Contract

- Read approved Markdown from `outputs/{output_slug}/application/`.
- Read `intake/source-structure.md` and the deliverable's source binding before conversion.
- Write optional final files under `outputs/{output_slug}/exports/`.
- Store extracted or reusable images under `outputs/{output_slug}/assets/`.
- Never create or convert to PDF.
- Never rewrite content during format conversion.
- Never replace a source-locked layout with a generic document template during conversion. Treat the approved Markdown's strategy-backed ordering as authoritative; conversion must not restore the pre-optimization source order.

## Routing

- DOCX: read `skills/docx/SKILL.md`.
- HTML: use this skill and preserve the approved Markdown structure.
- PDF source intake: read `skills/pdf/SKILL.md`; PDF remains input-only.
- Final exports: send to `quality-review`.

## DOCX

Use DOCX for editable resumes and cover letters when requested and supported by the current runtime. Preserve the source format skeleton and the approved Markdown's strategy-backed content order: top-level section order, heading hierarchy, paragraph boundaries, tables, headers, footers and image relationships. Use observable page size and margins when known; otherwise record the conservative assumptions. Do not promise pixel-perfect portfolio reproduction. If DOCX creation is unavailable, keep the approved Markdown as the final submission source and disclose the fallback without asking for an installation.

## HTML

Use HTML for requested visual portfolios or layout-aware documents. Preserve the approved Markdown's content order, source page/block templates, images, captions, classes and asset relationships. When application optimization has resequenced a complete experience or case-study unit, move its connected page/block and assets together without changing their internal order. For page-like sources, derive each page's aspect ratio when it is observable and use explicit page containers, stable dimensions, consistent margins, print CSS, controlled page breaks and non-distorting image sizing. Keep text within page bounds; do not add pages or shrink content in a way that changes a source-locked composition without recording and obtaining approval for the deviation. Do not add a marketing landing page or decorative redesign unless requested.

## Verification

Check output type, content equality against approved Markdown, source block coverage, strategy-approved unit order, text overflow, missing images, broken links, tables, page breaks and format skeleton. Write `exports/export-notes.md` with source ID, source Markdown, requested format, delivered format, output files, assets, layout assumptions, structural deviations, runtime capabilities used and QA limitations.
