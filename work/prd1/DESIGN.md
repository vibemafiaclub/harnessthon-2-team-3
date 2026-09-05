---
version: alpha
name: 청첩장모임 스케줄러
description: 예식일까지 남은 시간 안에 "아직 청첩장을 못 준 사람"을 0으로 만드는 모바일 조율 도구
omitted:
  - section: Elevation & Depth
    reason: 면 분리를 그림자가 아니라 뉴트럴 명도차와 1px 보더로만 처리한다. 야간 저조도에서 미세 그림자는 소실되고, 그림자를 쓰기 시작하면 "무엇이 앞인가"가 "무엇을 지금 해야 하는가"와 경쟁한다.

colors:
  surface: "#FAFAF9"
  surface-container: "#FFFFFF"
  surface-subtle: "#F5F5F4"
  outline: "#E7E5E4"
  outline-strong: "#D6D3D1"
  on-surface: "#1C1917"
  on-surface-variant: "#78716C"
  on-surface-muted: "#A8A29E"
  primary: "#B0442A"
  on-primary: "#FFFFFF"
  primary-container: "#FBEEEA"
  outline-primary: "#F0D9D1"

typography:
  display:
    fontFamily: Pretendard
    fontSize: 30px
    fontWeight: 800
    lineHeight: 1.15
    letterSpacing: -1px
  title:
    fontFamily: Pretendard
    fontSize: 19px
    fontWeight: 700
    lineHeight: 1.4
    letterSpacing: -0.3px
  body-lg:
    fontFamily: Pretendard
    fontSize: 17px
    fontWeight: 400
    lineHeight: 1.5
    letterSpacing: -0.3px
  body:
    fontFamily: Pretendard
    fontSize: 15px
    fontWeight: 400
    lineHeight: 1.5
    letterSpacing: -0.3px
  caption:
    fontFamily: Pretendard
    fontSize: 13px
    fontWeight: 400
    lineHeight: 1.5
    letterSpacing: -0.2px
  label:
    fontFamily: Pretendard
    fontSize: 13px
    fontWeight: 700
    lineHeight: 1.5
    letterSpacing: 0
  numeral:
    fontFamily: Pretendard
    fontSize: 19px
    fontWeight: 800
    lineHeight: 1.2
    letterSpacing: -0.3px
    fontFeature: tnum

rounded:
  sm: 6px
  md: 10px
  lg: 16px
  full: 999px

spacing:
  xs: 4px
  sm: 8px
  md: 12px
  lg: 16px
  gutter: 20px
  xl: 24px
  xxl: 32px
  safe-top: 59px
  safe-bottom: 34px

components:
  screen:
    width: 390px
    backgroundColor: "{colors.surface}"
    textColor: "{colors.on-surface}"
    typography: "{typography.body}"

  app-bar:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.on-surface}"
    typography: "{typography.title}"
    padding: "{spacing.gutter}"
  app-bar-contextual:
    backgroundColor: "{colors.surface-container}"
    textColor: "{colors.on-surface}"
    padding: "{spacing.gutter}"

  list-row:
    backgroundColor: "{colors.surface-container}"
    textColor: "{colors.on-surface}"
    typography: "{typography.body}"
    height: 72px
    padding: "{spacing.md}"
  list-row-compact:
    height: 64px
  list-row-alert:
    textColor: "{colors.primary}"
  list-row-pressed:
    backgroundColor: "{colors.surface-subtle}"
  list-row-empty:
    textColor: "{colors.on-surface-variant}"
    typography: "{typography.caption}"

  checkbox:
    size: 24px
    height: 48px
    rounded: "{rounded.sm}"
    backgroundColor: "{colors.surface-container}"
  checkbox-selected:
    backgroundColor: "{colors.primary}"
  checkbox-indeterminate:
    backgroundColor: "{colors.on-surface-muted}"

  button:
    backgroundColor: "{colors.surface-container}"
    textColor: "{colors.on-surface}"
    typography: "{typography.label}"
    rounded: "{rounded.sm}"
    height: 48px
    padding: "{spacing.md}"
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
  button-primary-pressed:
    backgroundColor: "#8E3722"
  button-disabled:
    backgroundColor: "{colors.surface-subtle}"
    textColor: "{colors.on-surface-muted}"

  cta:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.body-lg}"
    rounded: "{rounded.md}"
    height: 52px
  cta-pressed:
    backgroundColor: "#8E3722"
  cta-ghost:
    backgroundColor: "{colors.surface-container}"
    textColor: "{colors.on-surface}"
  cta-loading:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"

  badge:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.on-surface-variant}"
    typography: "{typography.caption}"
    rounded: "{rounded.sm}"
    padding: "{spacing.xs}"
  badge-alert:
    backgroundColor: "{colors.primary-container}"
    textColor: "{colors.primary}"

  unassigned-pill:
    backgroundColor: "{colors.primary-container}"
    textColor: "{colors.primary}"
    typography: "{typography.label}"
    rounded: "{rounded.sm}"
    height: 48px
    padding: "{spacing.md}"

  alert-bar:
    backgroundColor: "{colors.primary-container}"
    textColor: "{colors.primary}"
    typography: "{typography.label}"
    padding: "{spacing.sm}"

  tab-bar-item:
    backgroundColor: "{colors.surface-container}"
    textColor: "{colors.on-surface-muted}"
    height: 48px
  tab-bar-item-selected:
    textColor: "{colors.primary}"

  date-cell:
    textColor: "{colors.on-surface}"
    typography: "{typography.body}"
    height: 48px
  date-cell-conflict:
    textColor: "{colors.primary}"
  date-cell-outside:
    textColor: "{colors.on-surface-muted}"
---

## Overview

**청첩장 봉투 뒷면에 연필로 적어 내려간 명단.** 종이는 미색이고, 줄은 촘촘하고, 장식은 없고, 아직 못 만난 사람 옆에만 빨간 펜이 한 번 그어져 있다. 이 앱은 그 종이를 손에 쥔 것처럼 보여야 한다 — 봉투는 결혼이라는 정서 안에 있지만, 뒷면에 적히는 것은 **누구를 만났고 누구를 아직 못 만났는가**라는 운영이다. 이 대상은 `ref-12`(warm 뉴트럴이 액센트와 경쟁하지 않는다는 실측), `ref-13`("never decoratively" — 액센트를 브랜드마크·포커스링·주 CTA에만), `ref-04`(리스트 한 줄의 예산), `ref-14`(정서적 도메인의 도구에서 따뜻함은 추가가 아니라 제거의 결과)를 한 장면으로 압축한 것이다.

이걸 쥐는 사람은 **예식일까지 3개월 남은 예비신부 또는 예비신랑 중 편성 부하를 지는 쪽**이고(`core-problem.md §1`), 지인 40~60명을 20~30개 모임으로 묶어 각각의 날짜를 맞추는 중이다. 여는 순간은 즐기려는 때가 아니라 **놓친 게 없는지 확인하려는 때**다 — 주 수회, 한 번에 수십 초, 대개 한 손으로, 자주 잠들기 전 어두운 방에서. 이 앱이 푸는 문제는 *"수십 건의 조율이 서로 다른 상태로 동시에 흐르는데 그 상태를 보관하는 곳이 사람의 기억뿐이고, 마감(예식일)은 고정인데 진행은 남의 응답 속도에 달려 있다"*는 것이다(`core-problem.md §2`).

## Colors

**미색 종이 한 장 위에 펜 한 자루.** 뉴트럴은 전부 warm 한 방향이고, 유채색은 `{colors.primary}` 하나뿐이며 그것은 언제나 **상태를 말할 때만** 쓴다. 장식으로 색을 쓰는 자리는 이 시스템에 없다 (`ref-13`).

- **`{colors.surface}`** — 앱 배경. Tailwind stone-50 실측값 (`ref-12`). 이 위에서 `{colors.surface-container}`가 순백으로 떠오르는 것이 면 분리의 전부이고, 그래서 그림자가 필요 없다.
- **`{colors.surface-container}`** — 리스트 행·카드·하단 바. 스크롤되는 내용은 전부 이 색 위에 있고, 배경은 스크롤되지 않는 헤더에만 남는다 (`ref-04`).
- **`{colors.surface-subtle}`** — 눌린 상태(`list-row-pressed`)와 비활성 버튼 면. 모바일에는 hover가 없으므로 이 색의 유일한 쓰임이 pressed다 (`ref-07`).
- **`{colors.outline}`** — 리스트 행 사이 구분선. stone-200. **면을 나누는 유일한 수단**이다.
- **`{colors.outline-strong}`** — 버튼 보더와 체크박스 테두리. stone-300. 눌리는 것에만 쓰고 눌리지 않는 것에는 쓰지 않는다.
- **`{colors.on-surface}`** — 본문. 대비 16.7:1. 모임 이름·사람 이름·숫자처럼 **식별자**가 이 색이다.
- **`{colors.on-surface-variant}`** — 보조 설명("4명 중 2명 응답"). 대비 4.59:1로 AA를 **간신히** 넘으므로, 이보다 옅은 값을 보조 텍스트에 쓰지 않는다.
- **`{colors.on-surface-muted}`** — ⚠ **텍스트 금지.** 대비 2.41:1이라 본문에 쓰면 `surface.low-contrast-body` 위반이다. 쓰이는 곳은 응답 0건을 나타내는 큰 숫자, 비활성 탭 아이콘, 부분선택 체크박스처럼 **읽는 것이 아니라 보는 것**뿐이다.
- **`{colors.primary}`** — 액센트 1색. 벽돌빛. 쓰이는 자리는 **셋뿐**이다 — ① 행동이 필요한 항목의 리드 점과 원인 문구 ② 주 CTA ③ 미배정 인원 pill. 대비 5.43:1, 흰 글자를 얹으면 5.67:1 (`ref-12`의 warm 구조 덕에 뉴트럴과 경쟁하지 않는다).
- **`{colors.primary-container}` · `{colors.outline-primary}`** — 액센트의 저채도 면과 그 보더. 경고 바·알림 노트·미배정 pill에만.

**색으로 상태의 *종류*를 구분하지 않는다.** 마감 임박·무응답·날짜 충돌은 전부 같은 `{colors.primary}`로 뜨고, 무엇인지는 문구가 말한다. 모임이 20~30개인 제품에서 상태마다 색을 주면 색 어휘가 고갈되고 무지개 화면이 된다 (`ref-14`의 Huckleberry 한계, `ref-09`의 컬러 칩 붕괴).

## Typography

**한글 화면이라는 것이 이 스케일의 전제다.** 서체는 **Pretendard**를 쓴다. 기본값이라서가 아니라, 한글 본문에서 검증된 선택지가 좁고(`ref-15`) KRDS가 정부 표준 본문 서체로 채택한 것의 일반판이기 때문이다(`ref-11`). 라틴 기본값 회피를 위해 한글 가독성을 버릴 수는 없다 — 이 허용은 `brief.md`의 안티슬롭 제약에 사유와 함께 등재돼 있다.

크기는 **5종**(30 / 19 / 17 / 15 / 13), weight는 **2종**(400 / 700)이다. **위계를 크기가 아니라 weight로 만든다** — KRDS가 크기 4종과 weight 2종만으로 전 위계를 처리한 방식이고, 크기 종류를 늘리는 것보다 고밀도 리스트에서 안전하다 (`ref-11`).

행간은 **1.5 단일**이다(`{typography.display}`만 1.15). 행간을 다양화하지 않는 것이 핵심인데, 고밀도 리스트에서 줄 리듬이 깨지지 않기 때문이다 (`ref-11`). 그래서 **"여백이 넓다"는 인상은 행간이 아니라 블록 사이 간격으로 만든다**.

자간은 본문 계열 **−0.3px**다. 한글은 라틴과 **반대 방향**이라, 16~17px에서 좁혀야 한다 (`ref-15`). `ref-13`의 −0.05px 같은 라틴 기준값을 그대로 쓰면 한글에서는 자간이 넓어 보인다.

- **`{typography.body-lg}`** — 기본 본문 17px. Pretendard는 시각적 크기가 작아 17px을 기본으로 잡는다 (`ref-15`). CTA 라벨과 카드 제목이 이 크기다.
- **`{typography.body}`** — 리스트 행의 첫 줄(모임 이름·사람 이름). 15px은 `ref-15`가 제시한 한글 본문 하한이다.
- **`{typography.caption}`** — 리스트 행의 둘째 줄(원인 문구). 이 크기 아래로 내려가지 않는다.
- **`{typography.label}`** — 섹션 헤더·버튼·배지. caption과 크기가 같고 weight로만 갈린다.
- **`{typography.numeral}`** — 날짜별 응답 수. `fontFeature: tnum`으로 자릿수를 고정해 세로로 정렬되게 한다.
- **`{typography.display}`** — D-day. **세리프를 쓰지 않는다.** 한글 명조는 획 대비가 크고 x-height가 낮아 20px 미만에서 획이 소실되고(`ref-15`), 20px 이상 2줄 이하라는 성립 조건을 만족하는 자리가 이 화면에 D-day 하나뿐이라 서체를 하나 더 들일 값어치가 없다.

**Figma 설치 확인**: 미확인. Figma 파일에서 Pretendard가 실제로 로드되는지 아직 확인하지 않았다. 확인 전에 화면을 그리면 `meta.no-verification`(strong)이 확정되므로, A단계 이전에 확인하고 이 줄을 갱신한다.

## Layout

**뷰포트**: `{components.screen.width}`(390px) 기준으로 그리고 **360px에서 무너지지 않아야 한다**. 좁은 폭에서 먼저 접히는 것은 리스트 행의 둘째 줄 문구이고(말줄임), 첫 줄의 이름과 트레일링 버튼은 절대 접지 않는다 — 그 둘이 "무엇을, 어떻게"이기 때문이다.

**세이프 에어리어**: 상단 `{spacing.safe-top}` / 하단 `{spacing.safe-bottom}`. 이 대역에 조작 요소를 넣지 않는다. 하단 고정 CTA는 `{spacing.safe-bottom}`만큼의 패딩 위에 놓이고, 홈 인디케이터와 겹치면 실기기에서 눌리지 않는다.

**터치 타깃**: 최소 **48px**(`{components.button.height}` · `{components.checkbox.height}` · `{components.tab-bar-item.height}` · `{components.date-cell.height}`). 근거는 material-components-android의 리스트·선택 컴포넌트 문서와 Compose 접근성 기본값이다 (`ref-07`). iOS HIG의 44pt는 이번 소싱에서 1차 출처로 확인하지 못했으므로 인용하지 않고, **두 규범 중 큰 쪽인 48을 취해** 양 플랫폼을 동시에 만족시킨다. 시각적 크기는 이보다 작아도 되지만(체크박스 지표는 `{components.checkbox.size}` 24px) **히트 영역은 안 된다**. 타깃 사이 간격은 최소 `{spacing.sm}`.

**리스트 행의 예산**: 행은 **2줄 72px가 상한**이다(`{components.list-row.height}`). 3줄 88px로 올리면 20줄 과밀 시 스크롤이 1760px가 되어 한 화면 노출이 급감한다 (`ref-04`). 그래서 **다음 행동은 셋째 줄 텍스트가 아니라 트레일링 버튼으로 밀어낸다.** 390px에서 리딩 요소 자리를 쓰면 텍스트 가용폭은 약 302px다.

**한 손 도달**: 파괴적이지 않은 주요 동작은 화면 **하단 1/3**에 둔다. 선택 개수와 선택 해제(✕)는 상단 컨텍스추얼 바에 붙지만 **실행 버튼은 하단**에 둔다 — 390px 한 손에서 상단 우측은 엄지 사각지대다 (`ref-06`의 상하 분리, `ref-07`의 상단 치환을 조합한 것). 편성처럼 두 손을 쓰게 되는 작업만 상단 진입을 허용한다.

**세로 스크롤과 리듬**: 간격은 `{spacing.xs}`~`{spacing.xxl}` 일곱 단계만 쓴다(4의 배수, `ref-13`). 리스트 행 **안쪽**은 `{spacing.md}`, 행 **사이**는 1px 보더, 섹션 **사이**는 `{spacing.xl}`, 섹션 헤더와 첫 행 사이는 `{spacing.lg}`, 화면 좌우는 `{spacing.gutter}`다. 좌우 여백 16~24px 범위는 `ref-15`의 한글 모바일 권장에서 왔다.

**네비게이션**: 탭바 4개(할일 / 사람 / 모임 / 달력). 주 작업이 하나가 아니라 **사람·모임·시간 세 축을 서로 오가는 것**이므로 스택이나 허브가 아니라 병렬 구조여야 한다 (`core-problem.md §2`의 세 문제, `PT-01`). 첫 탭이 목록이 아니라 행동 큐인 것이 이 제품의 성격을 결정한다 — `ref-01`·`ref-02`·`ref-03`이 서로 다른 도메인에서 같은 답에 도달한 지점이다.

## Shapes

모서리는 4종이고 **역할이 겹치지 않는다.**

- **`{rounded.sm}`** — 눌리는 작은 것. 버튼·배지·체크박스·pill. 손가락 한 번에 끝나는 요소.
- **`{rounded.md}`** — 결정을 담는 것. 하단 CTA와 경고 노트. `{rounded.sm}`보다 커서 "이건 화면의 결론"이라는 신호가 된다.
- **`{rounded.lg}`** — 이 화면 세트에서는 쓰지 않는다. 카드형 컨테이너가 필요해질 때를 위한 자리이고, 지금 리스트는 **전폭 행 + 보더**라 라운드가 없다.
- **`{rounded.full}`** — 리드 점과 홈 인디케이터. 형태가 곧 의미인 것(점).

**리스트 행에 라운드를 주지 않는다.** 카드로 만들면 행 사이에 간격이 필요해지고, 그러면 한 화면에 들어오는 줄 수가 줄어든다 — 20~30건 규모에서 그건 그대로 비용이다 (`ref-04`).

## Components

- **`app-bar`** — 화면 제목과 D-day를 담는다. `{typography.title}`을 쓰고, 스크롤되지 않는 유일한 영역이라 배경이 `{colors.surface}`로 남는다(내용은 전부 `{colors.surface-container}` 위에 있다). `-contextual`은 선택 모드에서 제목 자리를 **선택 개수**로 치환하고 좌측에 해제(✕)를 둔다 — 개수와 탈출구가 같은 대역에 붙어야 갇힌 느낌이 나지 않는다 (`ref-07`).
- **`list-row`** — 이 시스템의 중심 컴포넌트다. 리딩(상태 점 또는 체크박스) / 2줄 텍스트 / 트레일링(버튼·숫자·배지) 세 슬롯이고, 슬롯이 비면 사라질 뿐 다른 것으로 채우지 않는다. 상태: **`-alert`**(행동이 필요해 원인 문구가 `{colors.primary}`) · **`-pressed`**(눌림 — 모바일에는 hover가 없으므로 이 자리가 pressed다) · **`-compact`**(64px, 트레일링 액션이 없는 조회 전용 행) · **`-empty`**(해당 섹션에 항목이 0건). `ref-01`의 규칙에 따라 **큐 섹션은 항목이 0건이면 섹션 헤더째 사라지므로**, `-empty`가 쓰이는 곳은 큐 전체가 빈 경우 하나뿐이다.
- **`checkbox`** — 상태 3종: `-selected`(전체) · `-indeterminate`(부분, `{colors.on-surface-muted}`) · 기본(빈칸). 부분 선택을 빈칸도 체크도 아닌 제3의 상태로 표시하지 않으면 "전체가 선택됐다"고 오독한다 (`ref-08`). **롱프레스로 진입하지 않고 상시 노출**한다 — 이 앱에서 선택은 예외가 아니라 주업무다.
- **`button`** — 리스트 행의 트레일링 액션. 48px. 상태: `-primary`(주 행동) · `-primary-pressed` · `-disabled`. 눌린 상태가 없으면 실기기에서 반응이 없어 `motion.missing-micro-interactions`가 확정된다.
- **`cta`** — 화면당 하나. 하단 고정. 상태: `-pressed` · `-ghost`(부차 선택지, 같은 바 안에서 폭이 좁다) · `-loading`(회신 재발송처럼 네트워크를 타는 동작). 로딩 상태를 선언만 하고 만들지 않으면 C단계에서 `판정 불가`가 되고, 판정 불가는 합격이 아니다.
- **`badge`** — 소유자(신부/신랑/양가)와 소속 개수("2개 모임"). 상태: `-alert`(보류처럼 사용자의 판단이 남아 있는 것). **색으로 그룹을 구분하지 않고 글자로 쓴다** — 모임이 20~30개면 색은 구분되지 않는다 (`ref-09`).
- **`unassigned-pill`** — 홈 헤더 우측에 상시 노출되는 미배정 인원 수. **이 제품에서 진척도는 퍼센트가 아니라 이 숫자이고, 목표는 0이다** (`core-problem.md` `D-03`). ⚠ 이 컴포넌트의 형태·배치에는 **레퍼런스 근거가 없다** — `references.md` 사각지대 1에 기록된 대로 소싱이 빈손이었고, 우리가 발명했다 (`ASSUMP-17`).
- **`alert-bar`** — 마감 시계와 날짜 충돌 경고. 화면 폭 전체를 가로지르며 스크롤과 함께 움직인다.
- **`tab-bar-item`** — 4개. 상태: `-selected`.
- **`date-cell`** — 캘린더 격자 한 칸. 48px로 잡아 터치 타깃을 만족시킨다. 상태: `-conflict`(같은 날 2건 이상) · `-outside`(앞뒤 달).

## Do's and Don'ts

- **Don't** 진척률 게이지("68% 완료")를 홈의 주 조직 원리로 삼지 않는다. 24건이 5~6개 상태에 흩어져 있을 때 퍼센트는 다음 행동을 하나도 알려주지 않는다 — 근거: `references.md` 클리셰 판정 (자도메인 `ref-05`)
- **Don't** 목록을 카테고리 탭으로 가르지 않는다. 이 제품은 카테고리가 아니라 **상태**로 갈린다 — 근거: `references.md` 클리셰 판정 (`ref-05`)
- **Don't** 리스트·보드·캘린더 뷰 토글을 주지 않는다. 정렬과 뷰 선택을 1회 수십 초 사용자에게 미루는 것이다 — 근거: `references.md` 클리셰 판정 (`ref-03` "안 가져올 것")
- **Don't** 컬러 칩으로 모임 소속을 표시하지 않는다. 모임 20~30개에서 색 어휘가 고갈된다 — 근거: `references.md` 클리셰 판정 (`ref-09`)
- **Don't** 자동 제안을 수락/거부 **이항** 버튼으로 받지 않는다. 이 제품의 핵심 어려움이 "어느 모임에 넣을지 애매하다"인데 이항 버튼은 그걸 표현할 자리를 없앤다 — 근거: `references.md` 클리셰 판정 (`ref-10`의 3지선다만 예외)
- **Don't** 선택 모드를 롱프레스로만 진입시키지 않는다. 선택이 주업무인 제품에서 발견성 낮은 진입은 관성이다 — 근거: `references.md` 클리셰 판정 (`ref-06`)
- **Don't** 그라디언트·유리질감·메시 배경·균일 발광·그라디언트 텍스트를 쓰지 않는다. 이 화면에서 "무엇이 앞인가"는 곧 "무엇을 지금 해야 하는가"이고, 이것들은 정확히 그 위계를 지운다 — 금지 슬롭 id `color.purple-blue-gradient` · `color.mesh-aurora-default` · `surface.glassmorphism-default` · `color.everywhere-glow` · `type.gradient-text`
- **Don't** 아이콘+제목+설명 3반복 블록을 쓰지 않는다. 40~100명·20~30건 규모에서 한 화면에 3건밖에 못 담는다 — 금지 슬롭 id `layout.icon-top-3-cards`
- **Don't** 문구 자리에 "간편하게 관리하세요" 같은 말을 넣지 않는다. **문구 자리에는 항상 숫자와 다음 행동이 들어간다** — "미배정 12명", "오늘 21시 마감 · 2명 미응답". 금지 슬롭 id `copy.buzzword-stack` · `copy.korean-translationese`
- **Don't** 네비게이션과 본문에 이모지를 쓰지 않는다. 축하 톤을 전면에 까는 가장 싼 수단이고, 늦은 밤 회신을 확인하는 실제 사용 순간과 어긋난다 — 금지 슬롭 id `kit.emoji-icon-navigation` · `copy.emoji-overuse`
- **Do** 비어 있는 것을 튀게 만든다. 응답 0건, 미배정 12명, 무응답 5일차 — 채워진 것보다 **비어 있는 것이 정보**다 — 근거: `ref-01`(빈 섹션은 사라진다) · `core-problem.md` `D-03`·`D-04`
- **Do** 시간을 절대 날짜가 아니라 **남은 시간**으로 쓴다. "오늘 21시 마감"·"5일째 무응답"·"D-70". 3개월 전과 2주 전 급한 모임을 같은 컴포넌트가 감당하게 하는 유일한 방법이다 — 근거: `core-problem.md` PRD §3-6
