---
name: docx
description: Read DOCX input with capabilities already present in the agent runtime, or create an optional editable DOCX from approved Markdown when native document creation is available. Use for Word input analysis, structure and asset preservation, requested resume or cover-letter DOCX exports, structural validation, and optional visual QA. Never install or ask the user to install document software or programming runtimes.
---

# Local DOCX

## Tool Order

1. Use a document capability already provided by the current agent runtime.
2. If available, use the runtime's existing archive and XML inspection capability to read OOXML structure and embedded media.
3. Use an existing document preview capability for optional visual QA.
4. If the runtime cannot complete the requested operation, follow the fallback rules below.

Do not install or require office suites, converters, programming runtimes, package managers, plugins, or global tools.

## Reading

- Extract main text, headings, paragraphs, lists, tables, headers, footers, image relationships and `word/media/` assets.
- During intake, preserve and record the original source order, assign source block IDs and write the result to `intake/source-structure.md`. This record does not prevent later strategy-backed sequencing by `application-optimization`.
- Record embedded media in `assets/asset-inventory.md` with its relationship to the source block.
- Reading XML gives structure, not trustworthy page geometry. If layout fidelity is important, prefer a companion PDF or runtime preview as the layout authority.
- If the DOCX cannot be read, ask for PDF or HTML when layout matters, or Markdown/TXT when content is sufficient.

## Creation

- Create DOCX only when the order requests `format: docx`.
- Use approved Markdown as the sole content source.
- Use `intake/source-structure.md` as the layout and format constraint and the approved Markdown as the content and sequencing authority; Markdown approval does not authorize a new template.
- Set page size and margins explicitly and use real headings, lists, tables, headers and footers.
- Keep image aspect ratios and embed reused images.
- Store final DOCX under `outputs/{output_slug}/exports/`.
- If native DOCX creation is unavailable, do not attempt an improvised binary file. Deliver the approved Markdown and record `DOCX export: unavailable in current runtime`.

## QA

When DOCX was created, perform every structural check the runtime supports: readable content, source block coverage, strategy-approved unit order, expected tables and images, stable top-level section order and no hidden placeholders. If an existing preview is available, inspect pages for clipping, overlap, missing glyphs, distorted images, broken tables and page breaks. If preview is unavailable, record `DOCX visual QA: not performed` in `export-notes.md` and `quality-review.md`. Never claim QA that was not performed.
