<!--
AI 슬롭 게이트 참조 문서. 0 · B-3 · B-4 · A · C 단계에서 Read한다.

이 파일은 `usability-heuristics.md`와 같이 **처음부터 채워져 있다.** 참가자의 암묵지가 아니라
외부에서 공개된 목록을 이식한 것이라, 미리 주어도 안목 수집이 오염되지 않는다.

출처: groovelb/sunshine-starter-kit — `.claude/agents/ai-slop-fixer.md` 및 그 에이전트가
유일한 판단 근거로 삼는 `src/data/aiSlopTaxonomyData.js` (AI-Slop Taxonomy v0.1, 51항목).
v0.2 부록 2항목은 원본 51개의 sev/cause를 바꾸지 않고 추가된 것이다.
-->

# AI Slop (SL) — 슬롭 게이트

**AI가 만든 티가 나는 디자인 클리셰.** 개별로 보면 다 멀쩡하다. 문제는 **결정이 없다는 것**이다.
원본 목록의 최상위 진단이 이걸 한 줄로 정리한다 — *"디자인은 결정의 축적인데, 이건 결정이 0개이고 중앙값 출력만 있다."*

## 이 문서가 다른 context/ 문서와 다른 점

### 1. 5번째 단계가 아니라, 네 단계에 나눠 심는 필터다

sunshine 원본은 전담 에이전트가 다 만들어진 화면을 나중에 전수 검사한다. 그대로 가져와 `S단계`로
붙이면 **제일 비싼 방법으로 제일 늦게** 잡게 된다. 이 하네스는 Figma 노드 속성을 직접 조회하므로
53개 중 42개가 "봐야 아는 것"에서 "조회하면 아는 것"으로 내려온다.

| 게이트 | 붙는 단계 | 항목 | 매체 | 상대 비용 |
|---|---|---|---|---|
| `SL0` | B-4 — 화면이 **0장**일 때 | 4 | `문서` (`DESIGN.md` 자체) | 거의 0 |
| `SL-A` | A단계 — `SC`와 같은 노드 덤프 재사용 | 38 | `노드` | 낮음 |
| `SL-C` | C단계 — `VC`와 같은 스크린샷 재사용 | 11 | `화면` | 높음 |

- **예방이 검출보다 싸다.** `underspec`·`no-constraint` 항목은 B-4에서 `DESIGN.md`를 제대로 쓰는 것만으로 발생하지 않는다.
- **`SL0`의 "0"은 단계 번호가 아니라 *화면이 0장*이라는 뜻이다.** 이 4항목이 검사하는 것(팔레트·서체·UI 킷 기본값·막연한 취향어)은 전부 **B단계가 고른 해**라서, 값이 아직 없는 0단계에서는 판정 자체가 성립하지 않는다. 그래서 실행 시점은 `DESIGN.md`가 완성되고 Figma에는 아직 아무것도 없는 B-4 종료 직후다 — 비용 이점은 그대로다.
- 0단계 종료 시에는 슬롭 id를 확정하지 않고 **전제조건만 본다** — `brief.md`의 "안티슬롭 제약"이 비었거나 역추출한 판단기준이 라벨 단어뿐이면 B단계로 넘어가지 않는다.
- **38개는 눈이 필요 없다.** A단계가 이미 뜨는 노드 정보를 그대로 재사용한다. 새로 조회하지 않는다.
- **스크린샷은 `SL-A`를 통과한 화면에만 쓴다.** `SL-A`에서 `strong`이 하나라도 나오면 거기서 멈추고 고친다. 렌더하지 않는다. **이게 비용 절감의 핵심이다.**

> **ID 주의** — 이 하네스에서 `SC`는 이미 **A단계 구조 체크**를 뜻한다(`usability-heuristics.md` 참조).
> 슬롭 게이트는 `SL0` / `SL-A` / `SL-C`로 쓰고, 원본 문서의 `S0/SA/SC` 표기는 쓰지 않는다.

### 2. 기준값을 하드코딩한다 — 단, 그것은 **금지값**이다

다른 `context/` 문서는 기준값을 하드코딩하지 않는다. 이 문서는 예외다. 여기 박힌 `#6366F1`,
`hue 240~290`, `H 30–55 / S≤0.2 / L≥0.9` 같은 값은 *프로젝트가 지켜야 할 값*이 아니라
**AI 기본값의 지문(anti-value)**이다. 판단기준 3계층 중 "완전 고정"에 속한다.

**토큰 오버라이드** — 판정 전에 반드시 **`DESIGN.md`의 front matter 토큰**과 `brief.md`의
"안티슬롭 제약"을 먼저 읽는다. 같은 값이 **근거와 함께** `DESIGN.md`에 등재돼 있거나
`brief.md`에서 명시적으로 허용됐으면 그 항목은 발동하지 않는다. 브랜드색이 실제로 인디고라면 `color.indigo-500-accent`는 발동하지 않는다.
남의 기본 팔레트로 판정하면 그 프로젝트가 **의도해서 고른 색**을 슬롭으로 오인한다.

**예외 1개** — `surface.low-contrast-body`(대비율 4.5:1)는 오버라이드 불가다. 접근성 하한선은
프로젝트가 협상할 수 있는 값이 아니다.

### 3. `유형` 열 — 산출물이 랜딩이 아니면 아예 적용하지 않는다

원본 목록은 마케팅 랜딩페이지를 전제로 만들어졌다. 히어로도 헤드라인도 없는 프로덕트 툴 화면에
`copy.vague-aspirational-headline`을 들이대면 오탐이다.

`brief.md`의 `산출물 유형`(`랜딩` / `툴` / `혼합`)을 읽고 아래 표의 `유형` 열로 거른다.

| 유형 값 | 뜻 |
|---|---|
| `공통` | 항상 적용 |
| `랜딩` | 산출물 유형이 `랜딩` 또는 `혼합`일 때만 적용. `툴`이면 **미적용** |

**모바일 매핑** — 이 하네스의 산출물은 모바일 화면이므로 유형 값을 이렇게 읽는다.
`툴` = 앱의 기능 화면(목록·상세·입력·설정). `랜딩` = 온보딩·프로모션·스토어 소개처럼 설득이 목적인 화면.
한 앱 안에 둘 다 있으면 `혼합`으로 두고 **프레임 단위로** 유형을 갈라 판정한다.

**모바일에서는 형태가 아니라 성질로 본다.** 원본 판정식 중 데스크톱 랜딩을 전제한 것
(`layout.icon-top-3-cards`의 3열, `layout.stat-banner-row`의 한 줄 3쌍 등)은 모바일에서
**세로로 쌓인 형태**로 나타난다. 가로 배치가 아니라는 이유로 `미적용` 처리하지 않는다 —
"구조가 같은 형제 블록의 기계적 반복"이라는 진단 자체는 그대로 성립한다.

**`미적용`과 `판정 불가`를 구분한다.** 미적용은 이 산출물에 해당 개념이 없다는 뜻이고,
판정 불가는 봐야 하는데 못 봤다는 뜻이다. 후자는 `VC`·`UH`와 같이 **합격으로 처리하지 않는다.**

### 4. 근거가 실측이 아니라 이식이다

`VC` 작성 규칙 4번(근거 태그)에 따라 구분한다. 이 문서의 모든 항목은 `외부:sunshine v0.1`
또는 `외부:v0.2 부록`이며, **이 하네스의 실측이 아니다.** 실제로 발동한 항목이 쌓이면
그때 실측 근거를 항목에 덧붙인다.

---

## 판정 규칙

원본의 severity clustering을 그대로 쓴다. `strong` 20 / `weak` 33.

1. **`strong` 1건이라도 확정 → 게이트 실패.** 혼자서도 "AI가 만들었네"가 즉시 보이는 것들.
2. **`weak` 단독 → 실패 아님, 경고만.** 혼자서는 정당한 선택일 수 있다.
3. **같은 프레임 안에서 `weak` 2건 이상 → `strong` 1건으로 승격, 게이트 실패.**

3번이 핵심이다. 이게 없으면 유리 질감 카드 하나 썼다고 오탐이 나고, 반대로 "하나하나는 애매한데
다 모이니 딱 AI 티"인 화면이 그냥 통과한다. **`VC`·`UH`와 달리 슬롭 항목은 독립 판정이 아니다** —
뭉침 판정을 위해 `weak` 확정 건수를 프레임 단위로 센다.

**추가로 지킬 것:**

- **처방 없는 지적 금지.** 모든 항목에 `escape`(대체 패턴)가 있다. "빼라"고만 하면 안 되고 무엇으로 바꿀지 지정한다. `escape`가 비어 있는 항목(주로 카피)은 대체 문안을 직접 써 준다.
- **기본은 리포트 전용.** 자동으로 고치지 않는다. 사용자가 "고쳐줘"라고 명시할 때만 수정한다.
- **이 문서에 없는 id를 짓지 않는다.** 아래 세 표가 SSOT다. 프로젝트별 클리셰는 `references.md`의 "클리셰 후보" 목록으로 따로 관리하고, 여기 id로 위장시키지 않는다.

## 리포트 형식

`VC`·`UH`와 같은 형식이다. **별도 리포트 파일을 만들지 않고** A·C 판정 리포트에 같은 형식의 줄로 섞어 쓴다.

```
[color.purple-blue-gradient] 불합격 (strong) — 히어로 배경 fill이 GRADIENT_LINEAR, hue 262→218. 처방: Monochromatic. 라우팅: 방향
[type.gradient-text] 경고 (weak) — 헤드라인 텍스트 fill이 그라디언트
[surface.glassmorphism-default] 경고 (weak) — 카드에 BACKGROUND_BLUR + fill opacity 0.6
  → 프레임 "Hero"에서 weak 2건 뭉침, strong 승격. 라우팅: 방향
[kit.pill-eyebrow-badge] 미적용 — 산출물 유형 `툴`
[motion.generic-fade-in] 판정 불가 — 프로토타입 reaction 미작성
```

상태 저장이 필요한 것은 셋뿐이다 — **weak 뭉침 판정 / 게이트별 시도 회차 / 3회 연속 재발 id**.
`decisions.md` 말미의 "슬롭 게이트 상태"에 남긴다.

## 실패 시 라우팅

C단계는 원래 "원인을 진단해 셋 중 하나로 분기"하지만, **슬롭이 원인일 때는 진단할 필요가 없다** —
항목의 `cause` 태그가 갈 곳을 이미 정해 놓았다.

| cause | 뜻 | 라우팅 |
|---|---|---|
| `no-verify` | 만든 뒤 사람이 확인 안 함. **예방 불가** | **① 국소** — 그 속성만 고치고 같은 게이트 재검 |
| `median` | 학습데이터 중앙값. 제약 없는 지시가 코퍼스 평균을 뱉음 | **② 방향(B 회귀)** — 축을 다시 나누거나 다른 후보 선택 |
| `no-constraint` | 가드레일 부재. 브랜드/접근성 제약이 없음 | **② 방향(B 회귀)** |
| `underspec` | 지시가 막연함. 구체 스펙 없는 브리프 | **③ 0단계 에스컬레이션** — 브리프의 토큰·판단기준부터 |

- cause가 둘 이상이면 **더 상류로** 간다 (`underspec` > `median`/`no-constraint` > `no-verify`).
- `meta.`로 시작하는 항목이 확정되면 표면 수정으로 못 고친다. 무조건 ② 또는 ③이다.
- 재시도 상한은 **게이트당 3회.** 같은 슬롭 id가 후보를 바꿔도 3회 연속 나오면 → 0단계 에스컬레이션(반복 실패 신호).

---

# SL0 — 0단계에서 예방 (4개, 매체 `문서`)

Figma에 그리기 전에 막는다. `DESIGN.md`가 아래 조건을 못 채우면 **아직 화면이 없어도 확정 발생**으로 처리한다.

| id | sev | cause | 유형 | `DESIGN.md`에서 검사하는 것 | escape |
|---|---|---|---|---|---|
| `meta.no-brand-constraint` | strong | no-constraint | 공통 | front matter의 `colors`·`typography`·`spacing`·`rounded`·`mobile`에 TODO가 하나도 없어야 함 (`DS-07`: `mobile:` 여섯 값은 특히) | — |
| `meta.vague-taste-word-prompting` | strong | underspec | 공통 | `## Overview` 첫 문단이 **구체적인 하나의 대상**을 지목하는가(`DS-02`). 형용사 나열("모던·깔끔·프리미엄")뿐이면 확정. 그 대상은 한 손에 쥔 물건이어야 한다 | — |
| `type.inter-for-everything` | weak | median | 공통 | `## Typography` 산문에 **왜 골랐는지**가 있는가. 기본값 폰트(Inter/Geist/Poppins) 또는 디스플레이 세리프(Playfair/Fraunces/Georgia/Instrument Serif)를 이유 없이 전면 적용하면 확정 | High-Contrast Serif, Variable Fonts |
| `kit.shadcn-default-look` | strong | no-constraint | 공통 | **모바일 번역**: `DESIGN.md` 토큰이 플랫폼 기본 UI 킷(Material 3 baseline / iOS 시스템 기본)의 값과 그대로 일치하는가. Figma에서는 라이브러리 컴포넌트를 override 없이 인스턴스로만 쌓았는가 | Padding Scale, FilledCard |

> `meta.vague-taste-word-prompting`은 0단계 1막의 **판별력 테스트**와 같은 것을 다른 각도에서 본다.
> 판별력 테스트가 `core-problem.md`의 줄을 거른다면, 이 항목은 `DESIGN.md`의 `## Overview`를 거른다.
> `DS-02`와 같은 규칙을 슬롭 쪽 ID로 부른 것이므로, 둘 중 하나만 리포트에 쓴다.

---

# SL-A — A단계에서 구조 검출 (38개, 매체 `노드`)

`SC` 9개 체크와 **같은 노드 덤프를 재사용한다.** 다시 조회하지 않는다.
**싼 것부터** 아래 ①→②→③→④ 순서로 돌고, `strong`이 확정되면 즉시 멈춘다.

## ① 텍스트 문자열만 훑으면 되는 것 (11개) — 제일 쌈

| id | sev | cause | 유형 | 판정식 | escape |
|---|---|---|---|---|---|
| `copy.buzzword-stack` | strong | median, underspec | 공통 | unleash / elevate / seamless / robust / cutting-edge / delve / harness / revolutionize / empower 중 2개 이상 | — |
| `copy.vague-aspirational-headline` | strong | median, underspec | 랜딩 | 히어로 헤드라인에 제품 고유명사·구체 동작이 하나도 없음 | — |
| `copy.korean-translationese` | strong | median, underspec | 공통 | "오늘날", "빠르게 변화하는", "~을 통해 ~를 제공합니다", 무생물 주어 | — |
| `copy.em-dash-overuse` | weak | median | 공통 | 한 문단에 em-dash 2회 이상 | Caption |
| `copy.rule-of-three` | weak | median | 공통 | 쉼표 3항 나열이 2개 섹션 이상에서 반복 | — |
| `copy.not-just-x-but-y` | weak | median | 공통 | "not just", "뿐만 아니라", "아니라 ~입니다" 대조 구문 반복 | — |
| `copy.bold-header-colon-list` | weak | median | 공통 | 불릿 3개 이상이 "굵은 라벨 + 콜론" 구조 | — |
| `copy.emoji-overuse` | weak | median | 공통 | 본문 이모지 3개 이상 | — |
| `copy.hedging-language` | weak | median | 공통 | "may help", "can potentially", "~수 있습니다" 반복 | — |
| `kit.emoji-icon-navigation` | weak | underspec | 공통 | 네비 텍스트에 이모지 코드포인트 포함 | NavigationMenu |
| `layout.stat-banner-row` | weak | no-constraint | 랜딩 | 한 줄에 숫자+단위 쌍 3개 이상 + 출처·맥락 없음 | Statistic |

## ② 색·폰트 값 비교 (10개)

| id | sev | cause | 유형 | 판정식 | escape |
|---|---|---|---|---|---|
| `color.purple-blue-gradient` | strong | median | 공통 | 배경/히어로 노드의 fill이 `GRADIENT_*`이고 `gradientStops` hue 240~290 | Monochromatic, 60% Dominant |
| `surface.low-contrast-body` | strong | no-verify | 공통 | 본문 글자와 뒤 배경의 대비율 4.5:1 미만. **오버라이드 불가** | Weight Contrast |
| `type.italic-serif-accent-word` | strong | median | 공통 | 헤드라인 안에 이탤릭 세리프 구간이 1~2단어 (2025 AI 스타트업 클리셰) | Exaggerated Hierarchy |
| `color.indigo-500-accent` | weak | median, no-constraint | 공통 | fill이 #6366F1 / #818CF8 / #4F46E5 이고 `DESIGN.md`의 `colors`에 없음 | 10% Accent, Complementary |
| `color.mesh-aurora-default` | weak | median | 공통 | 히어로 배경에 `LAYER_BLUR`/`BACKGROUND_BLUR` 걸린 그라디언트 덩어리 | Negative Space, Swiss / Editorial |
| `surface.glassmorphism-default` | weak | median | 공통 | 카드에 `BACKGROUND_BLUR` + fill opacity 1 미만 | Swiss / Editorial, OutlinedCard |
| `surface.permanent-dark-mode` | weak | no-verify | 공통 | 색 변수 모드가 1개뿐이거나 라이트 화면이 파일에 없음. **모바일은 OS 설정을 따르므로 한 모드만 있는 것이 곧 미구현이다** | DarkModeTransition |
| `type.repeated-font-combos` | weak | median | 공통 | 폰트 조합이 알려진 세트(Space Grotesk + Instrument Serif 등)와 일치 + `DESIGN.md`의 `## Typography` 산문에 선택 이유 없음 | Neo-Grotesque Sans |
| `type.gradient-text` | weak | no-constraint | 공통 | 텍스트 노드의 fill이 그라디언트 | Scale Contrast |
| `surface.cream-beige-default` | weak | median | 공통 | 페이지/히어로 단색 fill이 H 30–55, S≤0.2, L≥0.9 이고 `DESIGN.md`의 `colors`에 없음 · `외부:v0.2 부록` | Monochromatic, 60% Dominant |

## ③ 구조 패턴 — 형제 노드 비교 필요 (16개)

| id | sev | cause | 유형 | 판정식 | escape |
|---|---|---|---|---|---|
| `layout.centered-hero` | strong | median | 랜딩 | 히어로 자식이 전부 중앙정렬이고 버튼이 정확히 2개 | Asymmetric Balance, Asymmetric Split |
| `layout.fixed-section-stack` | strong | median | 랜딩 | 섹션 순서가 히어로→3카드→후기→가격→푸터와 일치 | Hierarchical Grid, Sectioned Stack |
| `layout.icon-top-3-cards` | strong | median | 공통 | 형제 프레임 3개의 가로·세로가 동일하고 자식 구조도 같음 | Bento Grid, Asymmetric Balance |
| `kit.pill-eyebrow-badge` | strong | median | 랜딩 | 헤드라인 직전 형제가 `cornerRadius ≥ height/2`인 알약 + 대문자 텍스트 | Focal Point |
| `kit.dead-cta` | strong | no-verify | 공통 | 버튼에 `reaction`이 없거나 목적지가 자기 자신. 히트 영역이 `mobile.minTouchTarget` 미만인 것도 실질적으로 죽은 CTA다 | Button |
| `meta.no-verification` | strong | no-verify | 공통 | 폰트 로드 실패 / 이동 없는 CTA / 빈 상태 미구현 / 세이프에어리어 침범 중 하나라도 | Aspect-ratio Discipline |
| `type.allcaps-eyebrow` | weak | median | 공통 | `textCase: UPPER` + 13px 이하 텍스트가 섹션마다 반복 | Weight Contrast |
| `type.extreme-hierarchy-cliche` | weak | underspec | 공통 | 글자 크기 최대/최소 비율 8 초과 + 서로 다른 크기가 `harness.scaleFloor.fontSize` 미만. 최소 크기가 `mobile.minBodyFontSize` 아래면 그것만으로 확정 | Modular Scale |
| `layout.numbered-123-steps` | weak | median | 공통 | 형제 노드 텍스트가 1, 2, 3으로 시작하는 반복 블록 | Steps |
| `layout.uniform-rounding` | weak | no-constraint | 공통 | `cornerRadius` 종류가 1개이고 여백 값 종류도 1개. **`DESIGN.md`의 `harness.scaleFloor`로 판정** | Scale Contrast, Spatial Grouping |
| `kit.lucide-only-icons` | weak | underspec | 공통 | **Figma 번역**: 아이콘이 전부 한 라이브러리의 인스턴스이고 `references.md`에 선택 근거가 없음 | SVGMorphing |
| `kit.colored-left-border-cards` | weak | no-constraint | 공통 | 왼쪽 stroke 두께만 0 초과인 카드가 3개 이상 | Figure-Ground |
| `motion.missing-micro-interactions` | weak | no-verify | 공통 | 인터랙티브 컴포넌트에 pressed 상태 없음. **모바일에는 hover가 없으므로 hover variant만 있고 pressed가 없으면 확정이다** — 실기기에서 눌러도 반응이 없다 | HoverCard, SpringPhysics |
| `motion.generic-fade-in` | weak | median | 공통 | 프로토타입 전환 설정이 전부 동일. **reaction 미작성이면 `판정 불가`** | StaggeredReveal, ScrollReveal |
| `motion.parallax-marquee-overuse` | weak | median | 랜딩 | 무한 흐름 프레임 + 로고 이미지 나열. **reaction 미작성이면 `판정 불가`** | Parallax, Marquee |
| `layout.nested-cards` | weak | median | 공통 | 카드형 프레임(radius>0 그리고 stroke 또는 shadow 또는 불투명 fill) 안에 같은 조건의 프레임이 중첩 · `외부:v0.2 부록` | Spatial Grouping, Figure-Ground |

## ④ 누적 판정 (①~③이 끝난 뒤 1개)

| id | sev | cause | 유형 | 판정식 | escape |
|---|---|---|---|---|---|
| `meta.mean-best-aesthetic` | strong | median | 공통 | ①~③ 확정이 5건 이상이거나, `decisions.md`의 축별 "선택 이유"가 비어 있음. `DS-04`에서 어느 섹션에도 안 걸린 축이 있어도 같은 신호다 | Asymmetric Balance |

> 원본에서 이 항목은 눈으로 보는 것이지만, **확정 건수를 세면 되는 일이라** 스크린샷이 필요 없고
> 더 일찍 잡힌다. 그래서 `SL-A`로 올렸다 (원본 기준 SA 35 / SC 12 → 이 하네스 38 / 11).

## `SC`·`UH`와의 겹침

같은 노드를 두 ID로 이중 지적하지 않기 위한 정리다. **겹치면 둘 다 판정하되, 라우팅은 상류 쪽을 따른다.**

| 슬롭 id | 겹치는 것 | 분업 |
|---|---|---|
| `kit.dead-cta` | `UH-03`(비상구) | 슬롭은 `reaction` **존재**, `UH-03`은 되돌리기 경로의 **타당성** |
| `motion.missing-micro-interactions` | `SC` variant 커버리지 | 같은 조회로 끝난다. `SC`는 목록 충족, 슬롭은 hover/pressed 부재 자체 |
| `meta.no-verification` | `SC` 전체 | `SC` 9개 중 하나라도 불합격이면 이 항목도 확정된다. 별도 조회 없음 |
| `surface.low-contrast-body` | `UH-08`·`VC` 없음 | 접근성 하한선. 이 하네스에서 유일하게 오버라이드 불가한 수치 |
| `layout.uniform-rounding` | `SC` 재사용률 | **방향이 반대다.** `SC`는 토큰을 *지켰는가*(상), 슬롭은 토큰에 *단계가 있는가*(벌). `DESIGN.md`의 `harness.scaleFloor`가 둘을 같은 값으로 판정한다 |
| `type.repeated-font-combos` / `type.inter-for-everything` | `VC-02` | 슬롭은 **선택 이유의 부재**(노드+문서), `VC-02`는 실제 가독성 붕괴(화면) |
| `meta.vague-taste-word-prompting` | `DS-02` | **같은 규칙의 두 이름이다.** `SL0` 리포트에 쓰면 `DS-02`는 다시 쓰지 않는다 |
| `kit.dead-cta` · `meta.no-verification` | `SC` 모바일 3항목 | 터치 타깃·세이프에어리어는 `SC`가 수치로 판정하고, 슬롭은 그 결과를 확정 신호로만 받는다. 노드를 다시 조회하지 않는다 |

---

# SL-C — C단계에서 지각 검출 (11개, 매체 `화면`)

C단계가 이미 렌더한 **같은 스크린샷**으로 `VC`·`UH`와 함께 판정한다. 렌더를 두 번 하지 않는다.
`visual-criteria.md`의 렌더 요건(전체 1장 + 밀집 영역 3배 크롭)을 그대로 따른다.
이미지가 없는 화면은 `img.*` 4개를 **미적용**으로 건너뛴다.

| id | sev | cause | 유형 | 무엇을 보나 | escape |
|---|---|---|---|---|---|
| `img.corporate-memphis` | strong | median | 공통 | 작은 머리, 길게 꺾인 팔다리, 얼굴 없는 인물, 과채도 플랫 (페이스북 Alegria 계열) | Linocut, Risograph |
| `img.plastic-ai-illustration` | strong | median | 공통 | 지나치게 매끈·대칭·플라스틱 질감·완벽한 조명 → 손으로 그린 적 없음이 드러남 | Etching, Woodcut |
| `img.ai-stock-anatomy-glitch` | strong | no-verify | 공통 | 이미지를 확대해 손·글자·눈을 본다. 부서진 손가락, 깨진 글자, 틀린 비례 | Image |
| `meta.differentiation-failure` | strong | median | 공통 | **로고와 문구를 가려도 이 제품이라고 알아볼 근거가 남는가** | Anti-AI Humantouch Type |
| `img.octane-3d-blob` | weak | median | 공통 | 발광 네온·광택 3D 덩어리를 장식으로 사용 (Midjourney 서명) | Flat Fill |
| `img.generic-ai-logo` | weak | median | 공통 | 육각형·소용돌이·뇌·회로 모티프 + 그라디언트 + 산세리프 워드마크 | Negative Space |
| `color.everywhere-glow` | weak | median | 공통 | 무엇이 앞이고 뒤인지 구분되는가. 균일한 발광이 위계를 지웠는가 | Figure-Ground, Z-axis Layering |
| `color.iridescent-computational` | weak | median | 공통 | 색이 조화롭기보다 "계산해서 뽑은 티"가 나는가 | Analogous, Split-Complementary |
| `layout.bento-overuse` | weak | median | 공통 | 큰 칸이 실제로 더 중요한 내용을 담고 있는가 | Bento Grid, Hierarchical Grid |
| `motion.without-meaning` | weak | no-constraint | 공통 | 튀는 버튼·떨리는 아이콘·떠다니는 배지에 기능적 의도가 있는가 | LayoutAnimation |
| `meta.cargo-cult-2020-web` | weak | median | 공통 | 2018~2022 트렌드가 "모던"으로 굳어 있는가 | Swiss / Editorial |

## `VC`와의 겹침

- **`VC-06`(클리셰 / AI 슬롭)은 이 게이트로 위임한다.** `VC-06` 자리에 별도 5필드를 쓰지 않는다 — 같은 대상을 두 ID로 판정하면 리포트가 이중장부가 된다. `references.md`의 **프로젝트별 클리셰 후보**만 `VC-06`으로 남는다.
- `color.everywhere-glow` ↔ `VC-03`(시각적 위계): 슬롭은 *발광이 원인일 때*만. 위계 붕괴 일반은 `VC-03`.
- `layout.bento-overuse` ↔ `VC-05`(정보 밀도): 슬롭은 *격자 크기와 중요도의 불일치*, `VC-05`는 밀도 자체.

---

## 항목을 추가할 때 (v0.3~)

`context/`의 다른 문서와 달리 여기는 **자유롭게 늘리지 않는다.** 원본이 자기 목록 파일을 유일한
근거로 삼으라고 못박은 것을 그대로 따른다. 추가하려면 네 조건을 **모두** 만족해야 한다.

1. 기존 표에 같은 원자가 없다
2. Figma 노드 속성으로 판정식이 선다 (또는 스크린샷에서 증상이 보인다)
3. 단독으로는 `weak`이다
4. 토큰 오버라이드가 오탐을 막는다

기존 항목의 `sev`/`cause`는 바꾸지 않는다. ID는 재사용하지 않는다.
이 조건을 못 넘는 것은 **`references.md`의 클리셰 후보**로 남기고, 이 표에 올리지 않는다.
