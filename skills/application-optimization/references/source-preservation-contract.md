# Source Preservation Contract

기존 문서를 회사에 맞게 고칠 때 적용하는 형식 보존 계약이다. `source-locked`는 원본과 같은 주제의 새 문서를 만드는 것이 아니라 원본 문서의 각 블록을 대응시켜 수정하는 방식이다. 원본 형식을 보존하는 것과 기존 내용의 우선순서를 고정하는 것은 구분한다.

## Material Inventory

`intake/material-inventory.md`는 다음 표를 사용한다.

| Source ID | Role | Path or attachment locator | Format | Readable | Authority | Used by | Notes |
|---|---|---|---|---|---|---|---|

- `Authority: source`는 구조·문체·기존 내용의 기준 문서다.
- `Authority: evidence`는 사실 확인용이며 원본 양식 기준이 아니다.
- 하나의 deliverable이 여러 문서를 참고해도 반드시 구조 권위 source는 하나를 지정한다.

## Source Structure Record

`intake/source-structure.md`에는 문서별로 다음을 기록한다.

### Document Header

- Source ID
- Role and format
- File or attachment locator
- Page count or top-level item count
- Language
- Observable layout: page ratio, columns, header/footer, major zones
- Reusable assets and asset inventory path
- Unsupported or unreadable features

### Block Map

| Block ID | Order | Parent | Source locator | Type | Heading or role | Boundary and length | Layout zone | Assets | Preserve |
|---|---:|---|---|---|---|---|---|---|---|

Block ID는 문서별 `SB-001`부터 부여한다. Block은 제목, 문단, 목록, 표, 이미지, 캡션, 구분선, 반복 카드처럼 독립적으로 위치를 확인할 수 있는 최소 구조 단위다.

`Boundary and length`에는 정확한 원문 전체를 복제할 필요 없이 문단 수, 목록 항목 수, 표 행·열, 대략적인 문자 범위처럼 결과 비교에 필요한 값을 기록한다.

### Structure Summary

- 최상위 섹션 순서
- 반복되는 프로젝트·경력 항목 패턴
- 고정 연락처·날짜·링크 위치
- 페이지 또는 화면 단위 구분
- 변경하면 레이아웃이 깨질 가능성이 높은 블록
- 읽기 순서가 불명확한 부분과 확인 방법

## Format-Specific Rules

### Markdown And TXT

- 제목 위계, 구분선, 문단 경계, 목록·표 형식, 링크와 이미지 관계를 유지한다.
- 같은 목록의 항목과 같은 섹션의 반복 경력·프로젝트 단위는 전략에 따라 순서를 바꿀 수 있다.
- 원본 문단 하나를 여러 문단으로 쪼개거나 여러 문단을 합치지 않는다.

### JSON

- 키 이름, 키 순서, 중첩, 값 타입, 배열 항목의 내부 구조를 유지한다.
- 기존 경력·프로젝트처럼 표시 순서를 나타내는 배열은 항목을 완전한 단위로 재배치할 수 있다. 추가·삭제 또는 항목 내부 구조 변경은 허용하지 않는다.
- 기존 키를 새 영문 표준 키로 바꾸거나 일반 이력서 스키마로 변환하지 않는다.

### HTML

- 의미 요소, class와 id, CSS 연결, 이미지 경로를 유지한다. 같은 부모 아래의 반복 경력·프로젝트 요소는 완전한 단위로 DOM 순서를 바꿀 수 있다.
- 텍스트 교체가 레이아웃을 넘치는지 확인한다.
- Markdown 출력 요청이라면 DOM의 블록 대응을 유지하되, 전략적으로 재배치한 같은 부모의 반복 단위 순서를 반영한다.

### DOCX

- 관찰 가능한 제목, 문단 경계, 목록·표, 머리글·바닥글, 이미지와 캡션 관계를 유지한다. 같은 섹션의 목록 항목과 반복 경력·프로젝트 단위는 전략적으로 재배치할 수 있다.
- XML만 읽은 경우 페이지 좌표를 알고 있다고 주장하지 않는다. 레이아웃 보존이 중요하면 런타임 preview 또는 companion PDF를 권위로 사용한다.

### PDF

- 페이지 수, 페이지별 읽기 순서, 제목, 문단, 표, 이미지, 캡션과 주요 배치 영역을 기록한다.
- Markdown으로 옮길 때 완전한 경력·프로젝트 페이지 묶음은 전략에 따라 재배치할 수 있다. 묶음 내부 페이지 순서, 이미지·캡션 관계와 블록 구조는 유지하며 페이지 병합·분할은 하지 않는다.
- 최종 Markdown에는 내부 page marker를 노출하지 않고 `source-structure.md`에서 대응 관계를 유지한다.

## Allowed Changes

### Source-Locked

허용:

- 같은 블록 안에서 표현을 직무에 맞게 다듬기
- 검증된 성과를 더 명확하게 쓰기
- 원래 길이와 말투 범위에서 키워드 자연스럽게 반영
- 같은 형식 안에서 관련 있는 내용을 강조하고 덜 관련 있는 내용의 표현 강도나 분량 낮추기
- 같은 목록의 글머리표 순서를 회사·직무 적합도에 따라 바꾸기
- 같은 섹션의 기존 경력·프로젝트 반복 단위를 완전한 단위로 재배치하기
- 오탈자와 사실 불일치 수정

위 전략 변경은 `company-signal-evidence-matrix.md`와 `matching-strategy.md`에 근거가 있고 `change-log.md`에 company signal ID와 evidence ID가 있을 때만 허용한다.

승인 또는 명시적 제출 규격 없이는 금지:

- 섹션·프로젝트·문단 삭제 또는 추가
- 블록 합치기·나누기
- 최상위 섹션 순서 변경 또는 서로 다른 부모 간 블록 이동
- 표를 목록으로 바꾸기
- 이미지 삭제·교체, 다른 프로젝트로 이동 또는 프로젝트 내부 이미지 순서 변경
- 원본에 없던 새 프로필, 역량, 케이스 스터디 섹션 생성

### Layout-Aware

Source-locked 전부에 더해 페이지 수, 페이지 비율, 영역, 이미지 위치, 텍스트 밀도를 보존한다. 관찰할 수 없는 폰트명, 좌표, 간격은 추측하지 않는다.

### Redesign

사용자의 명시적 요청이 있을 때만 새 구조를 제안한다. 원본 보존본과 redesign 결과를 구분하고 변경 승인을 기록한다.

### Create

기존 문서가 없는 새 작성이다. 이를 기존 문서 최적화로 표현하지 않는다.

## Structural Diff

`application/change-log.md`에는 최소 다음 열을 둔다.

| Source ID | Source block | Output file and block | Change type | Before summary | After summary | Reason | Company signal ID | Evidence ID | Approval | Structure result |
|---|---|---|---|---|---|---|---|---|---|---|

문서별 끝에는 다음 집계를 둔다.

- Source blocks
- Output blocks
- Preserved one-to-one
- Rewritten in place
- Added
- Removed
- Merged or split
- Strategy-approved reorder
- Unmapped or unapproved reorder
- Unapproved deviations
- Tables and images expected / delivered

`source-locked` 결과의 `Unapproved deviations`는 0이어야 한다.

## Failure Conditions

- `tailor`인데 source ID가 없음: Blocker
- source file을 읽지 않고 profile로 새 문서를 작성: Blocker
- source structure 없이 보존 완료 주장: Blocker
- 원본과 다른 일반 템플릿으로 resume 또는 portfolio 작성: Major 이상
- 회사 신호·지원자 근거 매핑 없이 임의로 어휘·강조·순서를 바꿈: Major
- 이미지가 있는 portfolio를 이미지 없이 텍스트 문서로 대체: Major
- 최종 제출 문서에 evidence ID를 노출: Major
