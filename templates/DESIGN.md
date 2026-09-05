<!--
B-4 산출물 템플릿 — 디자인 시스템 문서. 프로젝트 폴더로 복사해서 채운다.
빈 템플릿입니다 — 아래는 전부 TODO/형식 예시이며 실제 내용이 아닙니다.

포맷: DESIGN.md (google-labs-code/design.md, version alpha)
  https://github.com/google-labs-code/design.md
  YAML front matter = 기계가 읽는 토큰 / 마크다운 본문 = 왜 그 값인지의 산문.
  **산문이 본체다.** 토큰은 산문이 참조하는 맥락이지 렌더링 지시가 아니다.

작성 규칙은 `context/design-system-doc.md`의 `DS-01`~`DS-07`에 있다. 채우기 전에 Read한다.

이 하네스는 **모바일** 디자인 하네스다. 폼팩터는 축이 아니라 고정 제약이므로,
아래 `mobile:` 블록과 `## Layout`의 뷰포트·세이프에어리어·터치 타깃은 비워둘 수 없다.

이 파일이 정본인 것 (다른 파일에 중복해서 쓰지 않는다):
  - 모든 디자인 토큰 값 (컬러·타이포·spacing·radius·elevation)
  - A단계 `SC` 체크의 기준값
  - `SL0` 게이트가 검사하는 대상
`brief.md`가 정본인 것: 반응 원문 · 역추출한 **방향성 제약** · 안티슬롭 제약 · 산출물 유형.
방향("뉴트럴은 웜")은 brief.md, 값(`#F7F5F2`)은 여기. 이 분업이 깨지면 두 파일이 서로 다른 말을 한다.
-->

---
version: alpha
name: TODO(프로젝트명)
description: TODO — 한 줄. 무엇을 위한 시스템인가

colors:
  # 값만 적고 끝내지 않는다. 각 토큰이 아래 ## Colors 산문에서 최소 1회 참조돼야 한다 (DS-05).
  primary: "TODO"
  on-primary: "TODO"
  surface: "TODO"
  on-surface: "TODO"
  surface-container: "TODO"
  outline: "TODO"
  # 상태색은 쓰는 만큼만. 안 쓸 색을 미리 정의하면 DS-05에 걸린다.

typography:
  # 모바일 본문 하한은 아래 mobile.minBodyFontSize 를 지킨다.
  display:
    fontFamily: TODO
    fontSize: TODO
    fontWeight: "TODO"
    lineHeight: TODO
  title:
    fontFamily: TODO
    fontSize: TODO
    fontWeight: "TODO"
    lineHeight: TODO
  body:
    fontFamily: TODO
    fontSize: TODO
    fontWeight: "TODO"
    lineHeight: TODO
  caption:
    fontFamily: TODO
    fontSize: TODO
    lineHeight: TODO

spacing:
  # 종류 수가 곧 위계다. harness.scaleFloor.spacing 이상이어야 한다.
  xs: TODO
  sm: TODO
  md: TODO
  lg: TODO

rounded:
  # 한 종류만 쓰면 카드와 버튼의 위계가 사라진다 (layout.uniform-rounding).
  sm: TODO
  md: TODO

components:
  # B-3.5에서 선택된 화면에 실제로 등장한 것만 적는다. 라이브러리를 미리 설계하는 자리가 아니다 (DS-06).
  # Figma에는 컴포넌트/variant를 만들지 않으므로, 상태 값의 정본은 이 블록뿐이다.
  # 상태 변형은 별도 엔트리로 선언한다 (`-pressed`, `-disabled`, `-loading`, `-empty`).
  # 여기 선언된 엔트리 목록이 곧 A단계 Variant 커버리지 체크의 정답지다 (DS-06).
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    rounded: "{rounded.sm}"
    height: TODO   # mobile.minTouchTarget 이상
    padding: TODO
  button-primary-pressed:
    backgroundColor: "TODO"
  list-row:
    backgroundColor: "{colors.surface}"
    typography: "{typography.body}"
    height: TODO   # mobile.minTouchTarget 이상

mobile:
  # 모바일 하네스의 고정 제약. 값은 프로젝트가 정하되 비워둘 수 없다.
  # 근거는 CH-04(Apple HIG / Material Design)에서 가져와 ## Layout 산문에 인용한다.
  platform: TODO              # ios | android | 크로스플랫폼
  designViewportWidth: TODO   # 숫자만 (예: 390)
  minViewportWidth: TODO      # 좁은 기기에서 무너지지 않아야 하는 하한 (예: 360)
  minTouchTarget: TODO        # 숫자만 (예: iOS 44 / Android 48)
  minBodyFontSize: TODO       # 숫자만
  safeAreaTop: TODO
  safeAreaBottom: TODO
  primaryNavigation: TODO     # 탭바 | 스택 | 허브-스포크 | 없음

harness:
  # A단계 SC 체크가 이 값으로 판정한다. 비우면 그 체크는 `판정 불가`다.
  layerNamingConvention: TODO   # 예: "역할/상태" (Card/Empty). 산문으로 적어도 된다
  componentReuseFloor: TODO     # 0~1 사이 숫자. 인스턴스 비율이 아니라 반복 노드의 값 일치율이다
  variantCoverage: TODO         # 위 components 의 상태 엔트리 목록과 일치시킬 것.
                                # Figma variant가 아니라, 보이는 상태=화면 존재 / 나머지=이 문서 선언으로 판정한다
  scaleFloor:
    # "토큰을 지켰는가"(SC 재사용률)와 "토큰에 단계가 있는가"(layout.uniform-rounding)는
    # 방향이 반대다. 이 하한이 없으면 같은 화면이 한쪽에선 합격, 다른 쪽에선 불합격이 된다.
    rounded: TODO      # 종류 수 하한 (예: 2)
    spacing: TODO      # 예: 4
    fontSize: TODO     # 예: 4
---

## Overview

<!--
DS-02 — 첫 문장은 **구체적인 하나의 대상**이어야 한다. 형용사 나열("모던하고 신뢰감 있는")은
영역을 그릴 뿐 점을 찍지 못하고, 그 자체가 `meta.vague-taste-word-prompting`(strong) 확정 사유다.
이 문장은 지어내는 것이 아니라 `references.md`의 메커니즘 카드에서 나온다. 카드가 없으면 쓸 수 없다.
그리고 그 대상은 **손에 쥔 화면**이어야 한다 — 인쇄물·포스터 비유는 모바일 제약을 데려오지 않는다.
-->

TODO — 한 문단. 무엇을 닮은 물건인가. 근거: `ref-nn` / `PT-nn`

TODO — 두 번째 문단. 누가 어떤 상황에서 이걸 손에 쥐는가. `core-problem.md §1`의 핵심 사용자와
`§2`의 핵심 문제를 한 줄씩 받아 적는다. 사용 맥락(한 손 / 이동 중 / 밝은 야외)이 여기 없으면
`## Layout`의 수치가 근거를 잃는다.

## Colors

TODO — 팔레트 전체를 한 문장으로 설명한다. (예: "단일 잉크 + 액센트 하나")

- **TODO** `{colors.primary}` — 어디에 쓰고, **어디에는 쓰지 않는가**. 근거: `ref-nn`
- **TODO** `{colors.surface}` — TODO. 근거: `ref-nn`

<!--
DS-05 — 위 front matter에 정의했는데 이 목록에서 한 번도 참조되지 않는 토큰은 지운다.
안 쓸 색을 정의해두면 나중에 누군가 근거 없이 집어 쓴다.
DS-01 — 줄마다 `ref-nn` 또는 `PT-nn`을 단다. 근거 없는 줄은 하네스가 지어낸 것이다.
-->

## Typography

TODO — 왜 이 서체인가. **이름만 적는 것은 고른 게 아니라 기본값을 받은 것이다**
(`type.inter-for-everything`). 흔한 기본값(Inter/Geist/Poppins)이나 알려진 조합
(Space Grotesk + Instrument Serif 등)일수록 이유가 더 필요하다 (`type.repeated-font-combos`).

- **TODO** `{typography.display}` — 쓰는 곳. 장식적 서체라면 **어느 요소로 좁혔는지**까지.
- **TODO** `{typography.body}` — 본문. `mobile.minBodyFontSize` 이상인지 확인한다.

**Figma 설치 확인**: TODO — 이 서체가 대상 Figma 파일에서 실제로 로드되는지 확인한 결과.
확인 없이 적으면 `meta.no-verification`(strong)이 확정된다.

## Layout

<!-- 모바일 하네스의 핵심 섹션. 여기가 비면 B-4를 통과할 수 없다. -->

**뷰포트**: `{mobile.designViewportWidth}` 기준으로 그리고, `{mobile.minViewportWidth}`에서
무너지지 않아야 한다. TODO — 좁은 폭에서 먼저 접히는 요소를 지정한다.

**세이프 에어리어**: 상단 `{mobile.safeAreaTop}` / 하단 `{mobile.safeAreaBottom}`.
TODO — 이 영역에 무엇을 넣지 않는가. (하단 인디케이터 위에 CTA를 붙이면 실제 기기에서 눌리지 않는다)

**터치 타깃**: 최소 `{mobile.minTouchTarget}`. TODO — 근거(CH-04의 어느 문서). 시각적 크기가
이보다 작아도 되지만 **히트 영역은 안 된다**. 이 값 미만인 인터랙티브 요소는 A단계에서 불합격이다.

**한 손 도달**: TODO — 주요 동작을 화면 어느 대역에 두는가. 상단에 둘 수밖에 없는 동작이 있다면
그 이유를 적는다. `core-problem.md`의 사용 맥락(이동 중인가)이 이 결정을 가른다.

**세로 스크롤과 리듬**: 간격은 `{spacing.xs}`~`{spacing.lg}` 네 단계만 쓴다.
TODO — 섹션 사이와 항목 사이에 각각 어느 단계를 쓰는가.

**네비게이션**: `{mobile.primaryNavigation}`. TODO — 왜 이 구조인가. 근거: `ref-nn` / `PT-nn`

## Elevation & Depth

TODO — 그림자를 쓰는가, 면 분리로 가는가. 안 쓴다면 "쓰지 않는다"라고 명시한다.
비워두면 다음 사람이 임의로 넣는다.

## Shapes

TODO — `{rounded.sm}`과 `{rounded.md}`를 각각 어디에 쓰는가. 두 값이 같으면 한 종류만 정의한
것과 같고, `harness.scaleFloor.rounded`에 걸린다.

## Components

TODO — front matter의 각 컴포넌트가 **어떤 상태를 갖는가**를 산문으로 적는다.

- **button-primary** — TODO. 상태: `-pressed` TODO. 눌린 상태가 없으면 실제 기기에서 반응이 없다.
- **list-row** — TODO. 빈 목록일 때: TODO (`-empty` 엔트리 필요 여부)

<!--
DS-06 — 여기 선언한 상태 엔트리 목록 = A단계 Variant 커버리지 체크의 정답지다.
모바일에는 hover가 없다. hover 자리에 `-pressed`를 놓는다.
빈 상태·로딩·에러 화면을 선언만 하고 Figma에 안 만들면 C단계에서 `판정 불가`가 되고,
`판정 불가`는 합격이 아니다.
-->

## Motion

TODO — 전환의 성격을 한 문장으로. 모바일은 전환이 곧 위치 감각이므로 "안 쓴다"도 결정이다.
`motion.generic-fade-in` / `motion.without-meaning`이 여기 산문의 부재를 먹고 자란다.

## Do's and Don'ts

<!--
DS-03 — Don't를 발명하지 않는다. 두 곳에서만 온다:
  ① `references.md`의 "클리셰 후보" 중 *피해야 할 클리셰*로 판정된 것
  ② `brief.md`의 "안티슬롭 제약 — 금지하는 슬롭 id"
Don't가 10줄을 넘으면 `## Overview`가 부실하다는 신호다. 구체적인 레퍼런스는 금지 목록을
공짜로 데려온다 — 길어진다는 건 대상을 못 정했다는 뜻이므로 DS-02로 돌아간다.
C단계는 이 목록을 `VC-06`의 프로젝트별 항목으로 소환해 판정한다.
-->

- **Don't** TODO — 근거: `references.md` 클리셰 후보 / 금지 슬롭 id `TODO`
- **Do** TODO — 근거: `ref-nn`
