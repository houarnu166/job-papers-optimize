---
name: document-export
description: Read DOCX input with capabilities already present in the agent runtime, and convert approved Markdown into optional DOCX or HTML without rewriting content. Use for Word input analysis, structure and asset preservation, requested resume, career-history, cover-letter or portfolio exports, structural validation, and optional visual QA. PDF output is not supported. Never install or ask the user to install document software or programming runtimes.
---

# Document Export

DOCX 입력 읽기와 선택 출력(DOCX·HTML) 변환을 담당한다. PDF 입력은 `skills/pdf/SKILL.md`가 담당한다.

## Runtime Policy

1. 현재 에이전트 런타임에 이미 있는 문서 기능을 사용한다.
2. 가능하면 런타임의 압축·XML 검사 기능으로 OOXML 구조와 내장 미디어를 읽는다.
3. 미리보기 기능이 있으면 선택적 시각 QA에 사용한다.
4. 런타임이 요청 작업을 수행하지 못하면 아래 fallback 규칙을 따른다.

오피스 제품군, 변환기, 프로그래밍 런타임, 패키지 관리자, 플러그인 또는 전역 도구의 설치를 요구하지 않는다.

## Reading DOCX Input

- 본문, 제목, 문단, 목록, 표, 머리말·꼬리말, 이미지 관계와 `word/media/` 자산을 추출한다.
- 원본 순서를 보존해 기록하고 소스 블록 ID를 부여한 뒤 `intake/source-structure.md`에 쓴다. 이 기록은 이후 `application-optimization`의 근거 있는 재배치를 막지 않는다.
- 내장 미디어는 소스 블록과의 관계를 포함해 `assets/asset-inventory.md`에 기록한다.
- XML은 구조를 주지만 신뢰할 수 있는 페이지 기하는 주지 않는다. 레이아웃 충실도가 중요하면 동반 PDF나 런타임 미리보기를 레이아웃 권위로 사용한다.
- DOCX를 읽지 못하면 레이아웃이 중요할 때는 PDF 또는 HTML을, 내용만 필요하면 Markdown 또는 TXT를 요청한다.

## Export Contract

- 승인된 Markdown을 유일한 내용 원천으로 사용한다. 회사별 산출물은 `outputs/{output_slug}/application/`, 90% 자산은 `package/master/`에서 읽는다.
- 변환 전에 `intake/source-structure.md`와 해당 산출물의 원본 바인딩을 읽는다.
- 회사별 결과 파일은 `outputs/{output_slug}/exports/`, 마스터 결과 파일은 `package/master/exports/`에 쓴다.
- 추출·재사용 이미지는 해당 작업 폴더의 `assets/`에 둔다.
- PDF를 만들거나 PDF로 변환하지 않는다.
- 변환 단계에서 내용을 다시 쓰지 않는다.
- 원본 잠금 레이아웃을 일반 문서 템플릿으로 대체하지 않는다. 승인된 Markdown의 전략적 순서가 권위이며, 변환이 최적화 이전 순서를 되살리지 않는다.

## DOCX Output

요청되고 런타임이 지원할 때 편집 가능한 이력서·경력기술서·자기소개서에 사용한다. 원본 형식 골격과 승인된 Markdown의 전략적 내용 순서를 보존한다: 최상위 섹션 순서, 제목 위계, 문단 경계, 표, 머리말·꼬리말, 이미지 관계. 페이지 크기와 여백은 명시적으로 설정하고, 관찰 가능한 값이 없으면 보수적 가정을 기록한다. 이미지 비율을 유지하고 재사용 이미지를 임베드한다. 포트폴리오의 픽셀 단위 재현을 약속하지 않는다.

네이티브 DOCX 생성이 불가능하면 임의의 바이너리 파일을 만들지 않는다. 승인된 Markdown을 최종 제출 원천으로 두고 `DOCX export: unavailable in current runtime`을 기록하며 설치를 요구하지 않는다.

## HTML Output

요청된 시각 포트폴리오나 레이아웃 인지 문서에 사용한다. 승인된 Markdown의 내용 순서, 원본 페이지·블록 템플릿, 이미지, 캡션, 클래스와 자산 연결을 보존한다. 최적화가 경력·사례 단위를 통째로 재배치했다면 연결된 페이지·블록과 자산을 함께 옮기되 내부 순서는 바꾸지 않는다.

페이지형 원본에서는 관찰 가능한 페이지 비율을 도출해 명시적 페이지 컨테이너, 안정적 치수, 일관된 여백, 인쇄 CSS, 통제된 페이지 나눔과 왜곡 없는 이미지 크기를 사용한다. 텍스트가 페이지 경계를 넘지 않게 하고, 페이지를 추가하거나 내용을 축소해 원본 잠금 구성을 바꾸는 변경은 기록과 승인 없이 적용하지 않는다. 요청 없이 마케팅 랜딩 페이지나 장식적 재디자인을 더하지 않는다.

## Verification

출력 종류, 승인된 Markdown과의 내용 동일성, 소스 블록 커버리지, 전략 승인 단위 순서, 텍스트 넘침, 이미지 누락, 링크 파손, 표, 페이지 나눔, 형식 골격을 확인한다.

`exports/export-notes.md`에 source ID, 원천 Markdown, 요청 형식, 전달 형식, 결과 파일, 자산, 레이아웃 가정, 구조 편차, 사용한 런타임 기능과 QA 한계를 기록한다. 미리보기가 없으면 `DOCX visual QA: not performed`를 `export-notes.md`와 `review/quality-review.md`에 남긴다. 수행하지 않은 QA를 수행했다고 기록하지 않는다.

최종 결과 파일은 `quality-review`로 보낸다.
