<!--
4단계 산출물. 값 열은 ../references/design-rules.md의 기본값에서 시작한다.
덮어쓴 항목은 출처 열에 단계와 원문을 적는다. figma-builder는 status: confirmed 가 없으면 시작하지 않는다.
근거: decisions.md (허브 저장값: 축3 B·축4 B·축5 A / 나머지 추천값), brief.md, icons.md
-->

status: confirmed
confirmed_at: 2026-09-05 (사용자 지시 "선택된 것들 피그마로 보내도록" — 허브 저장값 + 스킬 추천값으로 확정. 규칙 미리보기 탭은 사후 확인용)
preview: design/probes/rules-preview.html

# Design Rules

## A. 토큰

| 키 | 값 | 출처 |
|---|---|---|
| color.bg | #FDFBF7 | 축 1: B 라이트·따뜻함 (추천 수락) |
| color.surface-1 | #F5F0E8 | 축 1 |
| color.surface-2 | #EDE6DA | 축 1 (surface-1보다 한 단계 진한 미색) |
| color.text | #1F1B16 | 축 1 |
| color.text-muted | #6B6560 | 축 1 (따뜻한 회색) |
| color.border | #E7E0D4 | 축 1 |
| color.accent | #EA580C | 축 4: B 선명한 단일 강조 — 허브 저장값 best:"B". 흰 글자 대비 확보를 위해 한 단계 진하게(사용자 "b로 ㄱㄱ", 2026-09-05) |
| color.accent-pressed | accent를 12% 어둡게 (#C2410C) | 자동 |
| color.accent-soft | accent 10% 불투명 (rgba(234,88,12,.10) → #FDF0E7) | 자동 |
| color.danger | #DC2626 | 고정 |
| color.overlay | rgba(0,0,0,.5) 하나만. 바텀시트·다이얼로그·로딩 동일 | 고정 |
| space.scale | 4 / 8 / 12 / 16 / 24 / 32 / 48 | 축 2: B comfortable |
| space.screen-padding | 좌우 16 | 축 2 |
| space.section | 24 | 축 2 |
| space.card-padding | 16 | 축 2 |
| radius | sm 4 / md 8 / lg 12 / xl 16 / full 9999 — 버튼 md, 카드·표·시트 lg | 축 3: B soft (추천) |
| shadow | sm 0 1px 2px rgba(31,27,22,.06) / md 0 4px 12px rgba(31,27,22,.08) — 카드 sm, 시트 md | 축 3 (따뜻한 배경에 맞춘 그림자 색) |
| font.family | "Pretendard", -apple-system, "Apple SD Gothic Neo", sans-serif | 축 5: A 균일 산세리프 (추천) |
| type.roles | display 28/700 · h1 24/600 · h2 18/600 · h3 17/600 · body 15/400 · body-sm 14/400 · caption 12/400 · label 13/500 (line-height 1.5, 제목 1.3). 본문 최소 14 | 축 5 |
| z.scale | base 0 · sticky 100 · app-bar 200 · tab-bar 200 · overlay 300 · sheet 400 · dialog 500 · snackbar 600 | 고정 |
| motion | 200ms ease-out. 시트 열림 250ms. 상태 전환(회신 O/X 채움) 150ms | 고정 |
| device.frame | 390×844 기준. 검증 폭 360 / 390 / 430 | 1단계 플랫폼: iOS만 |
| safe-area | 상단 상태바 44(노치 47) · 하단 홈 인디케이터 34 | 고정 |
| tap.min | 44×44. 인접 탭 영역 간격 최소 8 | 고정 |
| platform | iOS 단일. Android 미고려 | 1단계 플랫폼: "iOS만" |

## B. 컴포넌트 규칙

| 키 | 값 | 출처 | 사용 여부 |
|---|---|---|---|
| button.sizes | sm 36h / px12 / text14 · md 44h / px16 / text15 · lg 52h / px20 / text16 (풀폭 CTA) | 기본값 | 사용 |
| button.radius | radius.md (8) | 축 3 | 사용 |
| button.variants | primary(accent bg, 흰 글자) · secondary(surface-1 bg, text) · ghost(투명, accent 글자) · danger | 기본값 | 사용 |
| button.states | default · pressed(accent-pressed, 글자색 유지) · selected(accent-soft bg + accent 1px border) · disabled(opacity .4) · loading(스피너 20, 라벨 숨김, 폭 유지) | 2단계: "버튼을 눌렀을 때 나와야 할 상태값별로" | 사용 |
| button.row-rule | 같은 줄 버튼은 같은 size·radius. 두 개면 secondary 왼쪽, primary 오른쪽 (게스트 가능/불가능은 selected 토글 쌍) | 기본값 | 사용 |
| button.text | 한 줄. 진행 수 표기 허용 "보내기 (2개 답함)" | 레퍼런스: Doodle-③ | 사용 |
| button.primary-per-screen | 화면당 primary 1개, **하단 고정 바** | 2단계: "배치 일관되게, 시선 흐름" — 투어 화면 전부 하단 CTA | 사용 |
| button.duplicate | 같은 동작 버튼을 앱바와 본문에 이중 배치하지 않는다 | 기본값 | 사용 |
| icon.set | lucide-react 단일. design/icons.md 허용 목록만 | 기본값 | 사용 |
| icon.sizes | 16 / 20 / 24 | 기본값 | 사용 |
| icon.stroke | 16→1.5 / 20→1.75 / 24→2 | 기본값 | 사용 |
| icon.gap | 텍스트와 8, 수직 중앙 | 기본값 | 사용 |
| icon-button.hit | 44×44, 그림 24(앱바)·20(행) | 기본값 | 사용 |
| icon-button.name | 아이콘만 있는 버튼은 접근성 라벨. 탭바는 텍스트 라벨 동반 | 기본값 | 사용 |
| icon.state | 버튼 상태 색을 아이콘도 따른다 | 기본값 | 사용 |
| icon.overflow-menu | 앱바 액션 최대 1개 노출 + 더보기(⋯)에 모임 취소·다녀옴 처리 | 2단계 투어 ⑤⑧ 상단 바 | 사용 |
| icon.proximity | 행 액션(다시 알림)은 그 사람 행 우측 끝 | 2단계 투어 ⑧ | 사용 |
| tap.feedback | 탭 가능한 모든 요소에 pressed 반응 | 기본값 | 사용 |
| tap.long-press | 보조 액션에만 | 기본값 | 사용 |
| image.fit-by-purpose | 프로필 아바타만 사용: 32 원형 cover, 이니셜 폴백(surface-2 + label) | 레퍼런스: 이때-③ 아바타 스택 | 사용 |
| image.aspect | 아바타 1:1 고정 | 기본값 | 사용 |
| thumbnail.spec | — | 기본값 | (미사용) |
| thumbnail.strip | — | 기본값 | (미사용) |
| thumbnail.title | — | 기본값 | (미사용) |
| thumbnail.pressed | — | 기본값 | (미사용) |
| thumbnail.selected | — | 기본값 | (미사용) |
| thumbnail.selected-visible | — | 기본값 | (미사용) |
| image.transition | 아바타 로딩 전 이니셜 유지 | 기본값 | 사용 |
| image.placeholder | 로딩 = surface-2, 실패 = 이니셜 | 기본값 | 사용 |
| text.role-lock | 같은 역할 = 같은 type.role | 기본값 | 사용 |
| text.truncate | 모임 이름·지인 이름 1줄 말줄임, 안내문 3줄 | 1단계 가정: 실데이터 범위 | 사용 |
| text.short-copy | 버튼·칩 한 줄 | 기본값 | 사용 |
| text.long-copy | 긴 안내는 body-sm 별도 행 | 기본값 | 사용 |
| text.scale | 글자 확대 120%에서 버튼·탭바·회신 표 높이 auto | 기본값 | 사용 |
| copy.user-language | "확정 임박" 대신 "답 다 모였어요"처럼 사용자 언어. 투어 문구 기준 | 2단계 투어 원문 | 사용 |
| copy.error | 이유 + 다시 할 수 있는 조건 ("연락처가 이미 있어요 · 기존 지인 보기") | 2단계 투어 상태 세그먼트 | 사용 |
| copy.i18n | 한국어 단일 | 1단계: 다국어 아니오 | (미사용) |
| layout.left-edge | 모든 섹션 좌측 시작선 = 16 | 기본값 | 사용 |
| layout.section-gap | 24 | 축 2 | 사용 |
| layout.surface-tiers | bg → surface-1(카드) → surface-2(칩·표 헤더). 3단 이상 금지 | 기본값 | 사용 |
| layout.device-widths | 360 / 390 / 430 같은 레이아웃, 달력 7열 폭만 늘어남 | 기본값 | 사용 |
| layout.tablet | 미지원 | 1단계 가정 | (미사용) |
| layout.thumb-zone | primary CTA 하단 고정, 앱바 우측 액션은 보조에만 | 2단계 | 사용 |
| layout.template | 상태바 44 → 상단 바 56 → 본문 → 하단 CTA 52(+34) / 루트 4화면만 탭바. 게스트 화면은 상단 바 아래 주소창 띠 | 2단계: "배치 일관되게, 시선 흐름" | 사용 |
| scroll.single | 세로 스크롤 화면당 1개 | 기본값 | 사용 |
| scroll.last-item | 하단 여백 = 고정 바 + 34 + 16 | 기본값 | 사용 |
| fixed.bottom-cta | 버튼 52 + 상하 8 = 68 + safe-area 34, 배경 bg, 상단 border | 2단계 투어 템플릿 | 사용 |
| fixed.tab-bar | 높이 49 + 34. 4탭(홈·모임·지인풀·설정), 아이콘 24 + caption | 1단계: 4탭 | 사용 |
| fixed.no-clip | 고정 바가 회신 표 마지막 행·달력 마지막 주를 가리지 않음 | 기본값 | 사용 |
| keyboard | 지인 등록·확정 입력 화면은 CTA가 키보드 위에 붙는다 | 기본값 | 사용 |
| sheet.sizes | half(모임 이름·공유·겹침) / full 미사용. 그랩바 36×4 | 2단계 투어 ④⑦⑪ | 사용 |
| sheet.structure | 헤더 56(제목 + 닫기) · 본문 · 푸터 CTA 52 + safe-area | 기본값 | 사용 |
| sheet.use | 이름 입력·공유 방법·겹침 해결은 바텀시트. 모임 생성·후보 등록은 풀스크린 푸시 | 2단계 | 사용 |
| dialog | 모임 취소·연결 해제 확인만. 폭 화면-48, 버튼 2개(취소 왼쪽) | 기본값 | 사용 |
| dialog.dismiss | 시트는 오버레이 탭·드래그, 다이얼로그는 버튼만 | 기본값 | 사용 |
| app-bar | 높이 56. 뒤로(24) · 제목 h3 · 우측 액션 최대 1개 | 2단계 투어 템플릿 | 사용 |
| help.inline | 툴팁 없음. 안내는 필드 아래 caption | 기본값 | 사용 |
| snackbar | 하단 고정 바 위 16. 높이 48, 4초 ("은비를 추가했어요") | 2단계 투어 성공 상태 | 사용 |
| layer.order | z.scale 준수. 시트 위 시트 금지 | 기본값 | 사용 |
| state.required | 모든 화면에 초기·빈·로딩·성공·실패·비활성 6상태 | 1단계 brief §1 + 2단계 상태 세그먼트 | 사용 |
| state.empty | 아이콘 48(inbox) + 안내 1줄 + primary 버튼 1개, 세로 중앙 | 1단계 가정 | 사용 |
| state.loading | 스켈레톤(surface-2). 회신 표는 셀 단위 스켈레톤 | 기본값 | 사용 |
| state.error | 이유 + 재시도. 전송 실패는 인라인 카드 + "다시 보내기" | 2단계 투어 ⑥⑩ 실패 상태 | 사용 |
| state.offline | 앱바 아래 배너 1줄 | 기본값 | 사용 |
| data.range | 지인 0/1/100+, 모임 구성원 1(1:1)/3/6, 후보 1~5, 회신 0/일부/전원, 글자 120% | 1단계 PRD §3 | 사용 |
| data.ownership | 모임 상세·시트는 현재 모임 정보만 | 기본값 | 사용 |
| change.scope | 요청된 결함만 고친다 | 고정 | 사용 |
| change.relation | 위치 요청은 대상·기준·순서 확인 후 | 고정 | 사용 |
| change.propagate | 컴포넌트 수정 시 인스턴스 화면 전부 재스크린샷 | 고정 | 사용 |
| change.no-dup | 새 공통 요소 전 중복 확인 | 고정 | 사용 |

## C. 프로젝트 전용 규칙

| 키 | 값 | 출처 |
|---|---|---|
| color.side-groom | #4F7BE0 (신랑측 구분색, 파랑 — 주황 accent와 대비) | 축 6: 달력 색 바 (추천) + PRD 요구사항 5 양측 구분 |
| color.side-bride | #D95F8C (신부측 구분색, 로즈 — 주황 accent와 구분) | 축 6 + 레퍼런스: 시그널링 사람별 색 |
| color.side-both | 두 색 바 나란히 (양가 공동 모임) | 1단계 PRD §3 양가 공동 |
| calendar.cell | 390 폭 7열, 셀 높이 52, 날짜 숫자 body, 셀 아래 색 바 4h(신랑측·신부측 최대 2줄), 오늘 = accent 원 | 축 6: B 색 바 (추천) + 레퍼런스: 이때-① |
| calendar.conflict | 같은 시간대 모임 2개 이상 → 셀 우상단 빨간 배지 "겹침"(danger bg, 흰 caption) + 당일 목록 상단 경고 카드 | 1단계 PRD §3 겹침 + 2단계 투어 ① |
| status.chips | 회신 대기(surface-2/text) · 확정 임박(accent-soft/accent) · 확정(#DCFCE7/#166534) · 완료(surface-2/text-muted, 카드 opacity .7) | 1단계 요구사항 6 + 2단계 투어 ② |
| reply.matrix | 후보 × 구성원 표. 셀 44×44: 가능 = accent 원 + check 20 흰색, 불가능 = surface-2 원 + x 20 text-muted, 미응답 = circle-dashed 20 text-muted. 행 우측 "다시 알림" ghost sm | 2단계 투어 ⑧ + 레퍼런스: Doodle-① |
| reply.recommend | "답한 n명 모두 가능한 날" 카드: accent-soft bg, accent 1px border, h3 날짜 | 2단계 투어 ⑧ |
| guest.page | 링크 페이지: 상단 바 대신 주소창 띠(surface-2, globe 16). 후보별 가능/불가능 selected 토글 쌍(md), 하단 CTA "보내기 (n개 답함)" | 1단계: 게스트 링크 접속 + 레퍼런스: Doodle-①③ |
| member.badge | 중복 소속 = layers 16 + "동네 모임에도 있음" caption 칩 / 1:1 = user 16 칩 | 1단계 PRD §3 중복 소속·1:1 |
| coach.overlay | 안내·코치마크는 콘텐츠를 덮지 않는다. 프레임 밖 또는 여백에만 | 2단계: "여기를 눌러보세요가 UI를 가리면 안 된다" |
