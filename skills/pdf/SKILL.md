---
name: pdf
description: Read and inspect PDF input for job-application work, including text extraction, page boundaries, layout review, image extraction, and scanned-document detection. Use when a resume, portfolio, cover letter, job posting, or supplemental source is a PDF. This project does not create, edit, convert, or export PDF files.
---

# PDF Input

PDF는 입력과 검토에만 사용한다. PDF 산출물을 만들지 않는다.

## License And Modification Notice

This file is based on the OpenAI `pdf` skill from
`https://github.com/openai/skills/tree/main/skills/.curated/pdf`, licensed
under the Apache License 2.0. It has been substantially modified for this
project: PDF output and conversion were removed, installation and local
runtime dependencies were removed, and the workflow was rewritten for
input-only, runtime-native document handling. See `LICENSE.txt`.

## Tool Order

1. 현재 에이전트 런타임의 PDF 읽기·비전 기능을 먼저 사용한다.
2. 런타임이 제공하는 문서 미리보기나 OCR 기능이 있으면 레이아웃 또는 스캔 페이지 확인에 사용한다.
3. PDF를 읽을 수 없으면 내용을 추측하거나 도구 설치를 시도하지 않는다.
4. 레이아웃이 중요하면 같은 문서의 읽을 수 있는 PDF 또는 HTML, 내용만 필요하면 Markdown이나 TXT를 요청한다.

사용자에게 프로그램, 패키지, 플러그인 또는 명령줄 도구 설치를 요구하지 않는다. 읽을 수 있는 페이지만으로 일부 진행했다면 범위와 누락 페이지를 명확히 기록한다.

## Workflow

1. PDF 종류를 digital text, scanned image, OCR text layer 중 하나로 판별한다.
2. 텍스트와 페이지 수를 추출하고 Markdown에 `<!-- source-page: N -->` 표식을 남긴다.
3. 레이아웃이 중요하거나 읽기 순서가 불명확한 페이지만 렌더링해 확인한다.
4. 런타임이 지원하면 포트폴리오 이미지와 재사용 가능한 자산을 추출하고 `assets/asset-inventory.md`에 원본 페이지, 크기와 용도를 기록한다.
5. 텍스트 추출만으로 표, 열, 캡션 또는 이미지 위치를 추정하지 않는다.
6. 암호화, 손상, OCR 불가 또는 권한 문제는 `worklog.md`에 기록하고 필요한 대체 자료를 요청한다.

## Output

- Temporary page renders: `outputs/{output_slug}/intake/`
- Reusable images: `outputs/{output_slug}/assets/`
- Final optimized content: Markdown created by `application-optimization`

중간 페이지 렌더는 최종 제출물이 아니다. PDF 파일을 `exports/`에 작성하지 않는다.
