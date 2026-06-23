# RE:WAVE · KiiiKiii 컴백 era 디자인 시스템

> **적용 범위**: KiiiKiii 컴백 *RE:WAVE era* 한정. *시즌제 era 스타일* — 다른 era 로 갈아끼울 땐 새 번호(#3, #4…)로 분기한다.
> **BASE 상속**: radius/spacing/shadow/font-scale/transition/layout/border/컴포넌트/접근성/코드룰은 **스타일 #1 Crowny Class §3~§17, §19** 의 캐논을 *그대로* 상속한다. 본 파일은 그 위 **브랜드 컬러 + era 신규 토큰(레트로 질감·미니홈피 골격·깨짐 상태·모노 패밀리)** 만 정의한다.
> **PC·모바일 동일 스타일** (브레이크포인트로만 분기).
> **출처 잠금**: docs/06 §3-3(미니홈피 스킨 파스텔 + 비디오 신호색), docs/14 §4(시안 ③ Lilac/Mint Y2K — CEO 확정 2026-06-23).

---

## 1. 브랜드 아이덴티티

- 서비스명: **RE:WAVE** (KiiiKiii 컴백 era — 발굴 → 복원 → 공동운영 흐름의 시각 시스템)
- 슬로건/정서: "그 시절 미니홈피 *스킨샵*의 무광 파스텔" · 복원·왕복(RIDE/티키타카) · **anemoia**(겪지 않은 향수)
- 핵심 컬러 한 쌍:
  - **라일락(골격)** — 미니홈피 스킨판/방·종이톤. 싸이 *특유 배색은 회피*, *통상 형태* 안에서 추상화.
  - **매리골드(KEY = `--primary`)** — 열쇠/언락 연료. 클린한 노랑쪽 → 싸이 시그니처(주황-빨강) *직격 회피*. 따뜻한 손이 가는 CTA 색.
  - **Y2K 민트(RIDE = `--secondary`)** — 물결/왕복 점프. 라일락 골격과 청량 한난(寒暖) 대비.
- 분위기: 발랄하되 *무광 평면* — Aero/Y2K 글로시 베벨·소프트 글로우 절대 금지. ⚠ docs/14 §4 가드(파스텔 글로우 금지선과 *아슬한 경계* — 솔리드 면 + 하드 대비로만 운용).

---

## 2. 색상 팔레트 (Color Tokens)

> §2.2~§2.6 (다크/라이트/텍스트/상태/분류) 은 **BASE 캐논(스타일 #1 §15)을 그대로 상속한다.** era 색은 §2.1 + §2.7~§2.9 (레트로 질감·미니홈피 골격·깨짐 상태) 에 한정.

### 2.1 브랜드 컬러 (era 핵심)

| 토큰 | HEX | 용도 |
|---|---|---|
| `--primary` | `#FFB52E` | **KEY** 메인 — 클린 매리골드. CTA·"복원하기"·언락 강조. 싸이 회피선 통과(노랑쪽) |
| `--primary-dark` | `#E89412` | 호버·active·눌림 |
| `--primary-light` | `#FFCF6B` | 배지·보조 강조 |
| `--primary-rgb` | `255, 181, 46` | shadow·rgba 계산용 |
| `--secondary` | `#3CCFB4` | **RIDE** 메인 — Y2K 민트-아쿠아. 왕복 점프·물결·복원 처리 중 |
| `--secondary-light` | `#7FE3D0` | 디인터레이스 복원 하이라이트·부드러운 민트 강조 |

**메인 그라데이션** (CTA·로고·배지 등):

```css
--gradient: linear-gradient(135deg, #FFB52E 0%, #3CCFB4 100%);
```

> ⛔ **무광 가드**: 그라데이션은 *솔리드 우선·하드 평면*으로 사용. 글로시 베벨·소프트 글로우·발광·inner-shadow 금지(docs/14 §4 ⚠가드, docs/06 §3-3).

**CTA 그림자** (1종 한정 — 발광 아님, 일반 드롭 섀도):

```css
--shadow-primary: 0 4px 14px rgba(255, 181, 46, 0.35);
```

### 2.2 다크 영역 (사이드바·우측 미니홈피 메뉴 프레임)

→ BASE 캐논 그대로 (`--dark-bg #1B1D21`, `--dark-secondary #1A1C22`, `--dark-tertiary #2B2D35`, `--dark-border #3D3D54`). 자세한 표는 스타일 #1 §2.2.

> **다크 모드 주의 (era 특수)**: 라일락 골격은 다크 배경에서 탁해진다 → 다크 모드 시 골격을 **딥플럼**(`#26222E` 계열) 으로 치환 권장(BASE `--dark-*` 는 그대로 두고 era `--minihome-skin` 만 다크 변형 별도 정의). 매리골드/민트 채도만 유지.

### 2.3 라이트 영역 (콘텐츠)

→ BASE 캐논 그대로 (`--light-bg #F3F4F6`, `--light-card #FFFFFF`, `--light-border #E5E7EB`, `--light-hover #F9FAFB`). 자세한 표는 스타일 #1 §2.3.

> era 화면 본령은 *라이트*. 미니홈피 종이톤(§2.8) 위에 콘텐츠가 올라간다.

### 2.4 텍스트

→ BASE 캐논 그대로 (`--text-primary #FFFFFF`, `--text-dark #1F2937`, `--text-secondary #9CA3AF`, `--text-muted #6B7280`).

> **파스텔 위 텍스트 주의**: 라일락 골격면 위 본문은 `--text-dark` 로 잠금. 연한 회색 텍스트는 WCAG AA 미달 위험 → 금지.

### 2.5 상태(Semantic) 컬러

→ BASE 캐논 그대로:

| 상태 | 메인 | 배경(연한) | 용도 |
|---|---|---|---|
| 성공 | `#22C55E` | `#DCFCE7` | 완료·정상 |
| 경고 | `#F59E0B` | `#FEF3C7` | 주의 |
| 에러 | `#EF4444` | `#FEE2E2` | 실패·복원 실패 ("또 끊겼다" 세계관 카피) |
| 정보 | `#3B82F6` | `#DBEAFE` | 안내·중립 알림 |

### 2.6 분류용 컬러 (Chip · 카테고리 라벨)

→ BASE 캐논 그대로 (10~12% opacity 배경 + 진한 텍스트 패턴). 단 era 색을 칩으로 쓸 땐:

| 분류 예 | 배경 | 텍스트 |
|---|---|---|
| 매리골드 (KEY) | `rgba(255, 181, 46, 0.12)` | `#A66608` |
| 민트 (RIDE) | `rgba(60, 207, 180, 0.12)` | `#107F6E` |
| 라일락 (골격) | `rgba(40, 30, 48, 0.06)` | `#5C4F73` |

### 2.7 레트로 질감 (era 신규 · 네이밍 `--retro-*`)

> *질감 레이어 전용*. 콘텐츠 본문에 직접 칠하지 않는다. **적목 레드는 사물·화면에만, 인물 얼굴 금지** (docs/06 §3-6).

| 토큰 | HEX | 용도 |
|---|---|---|
| `--retro-redeye` | `#FF5C7A` | 캔디 레드 — 사물/화면 한정 강조 (적목 모티프). ⛔ 인물 얼굴 금지 |
| `--retro-green` | `#5BE6A8` | 파스텔 인터레이스 그린 — 저화질 비디오 신호 |
| `--retro-cyan` | `#5BD6E8` | 캔디 시안 — 디인터레이스 복원 하이라이트 |
| `--retro-scanline` | `rgba(40, 30, 48, 0.10)` | 플럼 틴트 스캔라인 오버레이 (콘텐츠 위 *별도 레이어*) |
| `--retro-static` | `rgba(40, 30, 48, 0.06)` | 플럼 틴트 지직/노이즈 베이스 |

### 2.8 미니홈피 골격 (era 신규 · 네이밍 `--minihome-*`)

> 라일락(연보라) 파스텔 — 미니홈피 스킨샵 *공통문법* 추상화. 싸이 특유 배색 복제 금지(docs/09 §b).

| 토큰 | HEX | 용도 |
|---|---|---|
| `--minihome-skin` | `#E8E2F2` | 라일락 스킨판/프레임 면 (대시보드 패널 배경) |
| `--minihome-paper` | `#FBF7FF` | 라일락-화이트 다이어리·방명록 종이톤 |
| `--minihome-line` | `#DCD2EC` | 미니홈피 프레임 구분선 |

### 2.9 깨짐 / 복원 상태 토큰 (era 신규 · 네이밍 `--state-*`)

> docs/06 §4-1 "깨짐=디폴트, 복원=보상" 원리의 토큰화. ③ 주의 — 파스텔에 깨짐이 묻히지 않게 `--state-broken` 라일락 그레이 대비를 또렷이.

| 토큰 | 값 | 용도 |
|---|---|---|
| `--state-broken` | `#ADA8B8` | 라일락 그레이 — 미복원 스캔라인/텍스트 |
| `--state-broken-bg` | `#E6E1EE` | 미복원 영역 면 |
| `--state-restoring` | `var(--secondary)` (#3CCFB4) | 복원 처리 중 (민트 = RIDE) |
| `--state-restored` | `var(--primary)` (#FFB52E) | 복원 완료 (매리골드 = KEY) |

---

## 3. 타이포그래피

### 3.1 폰트 패밀리

- **본문/UI**: BASE 그대로 → `'Pretendard Variable', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif`
  - CDN: `https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/variable/pretendardvariable.min.css`
- **로고/장식 텍스트**: BASE 그대로 → `'Agbalumo', cursive` (로고 한정, 본문 X)
- **모노 패밀리 (era 신규)** — `--font-family-mono`:
  ```css
  --font-family-mono: ui-monospace, 'SFMono-Regular', Consolas, 'Liberation Mono', Menlo, monospace;
  ```
  - **새 웹폰트 CDN 도입 아님** (시스템 폰트 스택 — 금기 §19 비저촉).
  - **용도 한정**: today/total 카운터 · 파일명 · 복원 진행률 — *"기계가 복구 중"* 질감 (docs/06 §3-2). 장식 아닌 *기능*.
  - 본문·헤딩에 사용 금지.

### 3.2 폰트 사이즈 토큰

→ **BASE 캐논 그대로** (스타일 #1 §3.2). 최소 폰트 = 16px (`--font-md`). 캡션·뱃지·라벨 모두 16px 아래로 안 내림. era 의 질감/노이즈 레이어가 가독성 침범하지 않게 *별도 레이어*로 분리.

### 3.3 굵기 / 3.4 줄간격

→ BASE 캐논 그대로.

---

## 4. 간격 (Spacing)

→ **BASE 캐논 그대로** (스타일 #1 §4). 8px 그리드.

## 5. 모서리 (Border Radius)

→ **BASE 캐논 그대로** (스타일 #1 §5). 버튼 10px · 카드/모달/미니홈피 패널 16px.

## 6. 그림자 (Shadow)

→ **BASE 캐논 그대로** (스타일 #1 §6) + era 오버라이드:
- `--shadow-primary: 0 4px 14px rgba(255, 181, 46, 0.35)` (매리골드 KEY CTA 호버).

> ⛔ **글로우/소프트 섀도 토큰을 *추가하지 않는다*** — 무광 가드(§2.1). 글로시 inner-shadow·발광형 box-shadow blur 금지.

## 7. 테두리 (Border)

→ **BASE 캐논 그대로**. 활성/포커스는 era `--primary`(매리골드).

## 8. 트랜지션

→ **BASE 캐논 그대로** (스타일 #1 §8).

## 9. 레이아웃 / 반응형

→ **BASE 캐논 그대로** (스타일 #1 §9). 사이드바 260px · 헤더 64px · 콘텐츠 max 1280px · 브레이크포인트 Tailwind 호환.

---

## 10. 컴포넌트

→ **BASE 캐논 컴포넌트 카탈로그 그대로 상속** (스타일 #1 §10: 버튼·카드·입력·모달·칩·토스트·탭바·네비게이션). era 색을 단순 치환만:

- **Primary 버튼** = `linear-gradient(135deg, var(--primary), var(--secondary))` (매리골드 → 민트, **무광 평면**). 호버 `translateY(-2px)` + `--shadow-primary`. *글로시 베벨·발광 금지*.
- **카드** = `--light-card` 위 `--radius-xl` (16px) — 미니홈피 패널 면은 `--minihome-skin` 사용 가능.
- **포커스 보더** = `var(--primary)` + `box-shadow: 0 0 0 3px rgba(255, 181, 46, 0.12)`.

### 10.x era 추가 컴포넌트 (BASE 위에 얹음)

- **RESTORE METER** (복원 진행률 바) — 2겹 게이지: (a) 내 기여 즉시 `--state-restored`(매리골드) · (b) 전체 누적 `--secondary`(민트). today/total 카운터 = `--font-family-mono` + `--font-md`. 5상태 (loading/error/empty/disabled/focus) — docs/06 §2-1 참조.
- **DECAY→RESTORE 전환** — broken→restoring→restored 상태머신. 디인터레이스/프로그레시브 디코딩 모션. 실패 시 broken 롤백 (데이터 손실 없이).
- **미니홈피 dashboard 패널** — `--minihome-skin` 면 + `--minihome-line` 구분선 + `--radius-xl`. 우측 메뉴 프레임은 BASE `--dark-bg` 가능. **싸이 미니미·도토리 *형상* 절대 회피** (KEY 아이콘 = Lucide `key` 도트화, RIDE = `waves`+`arrow-right`).

---

## 11. 아이콘

→ **BASE 캐논 그대로** (Lucide Icons). 자주 쓰는 era 아이콘: `key`(KEY 언락), `waves`/`arrow-right`/`refresh-cw`(RIDE 왕복), `image`(사진첩), `book-open`(다이어리), `message-square`(방명록), `music`(BGM 플레이어).

> ⛔ 새 아이콘 라이브러리(Material/Heroicons 등) 도입 금지. CEO 승인 필요.

---

## 12. 로고 사용 규칙

- **RE:WAVE 로고** — Agbalumo 폰트 또는 CEO 디자인 자유. era 한정.
- **OG 이미지** — 1200×630, 라일락 골격 + 매리골드 KEY 강조 + 민트 RIDE 액센트 + 캠코더 스캔라인 *별도 레이어* (글로우 금지).
- **Favicon** — 32×32, KEY 모티프(매리골드 도트 열쇠) 권장.

---

## 13. 작성 규칙 (Voice & Tone)

→ **BASE 캐논 그대로** (존댓말, 짧고 명확, 동사 라벨, 이모지 절제).

**era 카피 추가 규칙** (docs/06 §6-1):
- "도토리" ❌ → "**KEY**" ✅
- "파도타기" ❌ → "**RIDE / 물결타기**" ✅
- "미니미" ❌ → "**PIXEL SELF / 도트 분신**" ✅
- "미니홈피" ❌ → "**RECOVERED DASHBOARD / 복원 홈**" ✅
- "일촌평" ❌ → "**RE:(리)**" ✅
- 에러 카피도 세계관 언어로 — "또 끊겼다" / "복원 신호 끊김 / 다시 시도".

---

## 14. 접근성

→ **BASE 캐논 그대로** (WCAG AA, 포커스 링, alt 텍스트, 키보드 탭).

**era 추가**:
- `prefers-reduced-motion` 시 지직/스캔라인/디인터레이스/점프 애니메이션 정지 → 정적 복원 단계로 대체.
- 노이즈 강도 상한 — 광과민(PSE, WCAG 2.3 — 3회/초 이하).
- 적목 레드(`--retro-redeye`) 인물 얼굴 적용 금지 (docs/06 §3-6).
- 파스텔 면 위 텍스트는 `--text-dark` 잠금 — 연한 회색 텍스트 금지.

---

## 15. 전체 CSS 변수 한 번에 (복붙용)

> **BASE 토큰 전체는 스타일 #1 §15 그대로 상속.** 아래는 era 오버라이드/신규 토큰만 발췌. 실제 `styles/tokens.css` 는 [A] BASE + [B] THEME 두 블록 구조.

```css
:root {
  /* ===== era 브랜드 (BASE 오버라이드) ===== */
  --primary: #FFB52E;             /* KEY 매리골드 */
  --primary-dark: #E89412;
  --primary-light: #FFCF6B;
  --primary-rgb: 255, 181, 46;
  --secondary: #3CCFB4;           /* RIDE Y2K 민트 */
  --secondary-light: #7FE3D0;
  --gradient: linear-gradient(135deg, #FFB52E 0%, #3CCFB4 100%); /* 무광 솔리드 */
  --shadow-primary: 0 4px 14px rgba(255, 181, 46, 0.35);

  /* ===== era 신규: 레트로 질감 ===== */
  --retro-redeye:   #FF5C7A;
  --retro-green:    #5BE6A8;
  --retro-cyan:     #5BD6E8;
  --retro-scanline: rgba(40, 30, 48, 0.10);
  --retro-static:   rgba(40, 30, 48, 0.06);

  /* ===== era 신규: 미니홈피 골격 ===== */
  --minihome-skin:  #E8E2F2;
  --minihome-paper: #FBF7FF;
  --minihome-line:  #DCD2EC;

  /* ===== era 신규: 깨짐/복원 상태 ===== */
  --state-broken:    #ADA8B8;
  --state-broken-bg: #E6E1EE;
  --state-restoring: var(--secondary);
  --state-restored:  var(--primary);

  /* ===== era 신규: 모노 패밀리 (카운터·파일명·진행률 한정) ===== */
  --font-family-mono: ui-monospace, 'SFMono-Regular', Consolas, 'Liberation Mono', Menlo, monospace;
}

/* 카운터·파일명·복원률 등 "기계가 복구 중" 텍스트에만 적용 (장식 아닌 기능) */
.mono { font-family: var(--font-family-mono); }
```

---

## 16. 신규 페이지/컴포넌트 만들 때 체크리스트

- [ ] 색상은 **본 파일 §2 토큰 안에서만** (임의 HEX X, 시안 ①·② HEX 섞기 X)
- [ ] CTA = 매리골드 → 민트 그라데이션, **무광 솔리드** (글로시 베벨·발광 금지)
- [ ] 라일락 골격면 위 본문은 `--text-dark` 잠금
- [ ] 16px 본문 하한 — 카운터·진행률도 16px (`--font-md`) + `--font-family-mono`
- [ ] 적목 레드(`--retro-redeye`) **사물·화면에만**, 인물 얼굴 금지
- [ ] 노이즈/스캔라인은 콘텐츠 위 *별도 레이어* (가독성 분리)
- [ ] `prefers-reduced-motion` 폴백 (지직/스캔라인/점프 정지)
- [ ] era 카피 규칙 — "도토리/파도타기/미니미" 금지, "KEY/RIDE/PIXEL SELF" 사용
- [ ] 모바일에서 사이드바 → 하단 탭바, 모달 → 바닥 시트 (BASE 룰 유지)
- [ ] 터치 타겟 44px 이상

---

## 17. 디자인 시작 시 프롬프트 예시

> "RE:WAVE era 디자인 시스템(첨부 02-rewave.md)을 따라 [페이지/컴포넌트명] 을 만들어줘.
> - 메인 컬러: 매리골드 KEY(#FFB52E) → Y2K 민트 RIDE(#3CCFB4)
> - 골격: 라일락 미니홈피 스킨(#E8E2F2) / 종이톤(#FBF7FF)
> - 폰트: Pretendard (본문) + 시스템 모노(카운터·파일명·복원률)
> - 카드 radius 16px, 버튼 radius 10px
> - **무광 평면 + 하드 대비** — 글로시 베벨·발광·글로우 금지
> - 적목 레드는 사물/화면만, 인물 얼굴 금지
> - 아이콘 Lucide, 한국어 존댓말
> - era 카피: KEY / RIDE / PIXEL SELF / RECOVERED DASHBOARD / RE:"

---

## 18. 테마 컬러 오버라이드 룰

RE:WAVE 는 **시즌제 era 스타일**이다. 향후 다른 era 가 오면 또 새 번호(#3, #4…)로 분기한다.

같은 era *안에서* Primary/Secondary 두 값만 바꾸는 건 *테마 오버라이드*로 본 스타일에 머문다 (스타일 #1 §18 표현 미러). era 신규 토큰(`--retro-*`/`--minihome-*`/`--state-*`/`--font-family-mono`) 까지 바꾸려면 새 스타일 번호로 분기.

```css
:root {
  /* 본 era 안의 Primary/Secondary 미세 조정 예 (구조·신규 토큰 그대로) */
  --primary: #FFB52E;
  --primary-dark: #E89412;
  --primary-light: #FFCF6B;
  --primary-rgb: 255, 181, 46;
  --secondary: #3CCFB4;
  --secondary-light: #7FE3D0;
  --gradient: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
  --shadow-primary: 0 4px 14px rgba(var(--primary-rgb), 0.35);
}
```

**CEO 가 "다른 era로" 라고 하면 → 강디가 새 번호 파일(03-xxx.md) 생성 + active.txt 갱신.**

---

## 19. 코드 적용 컨벤션 (강개발 룰)

→ **스타일 #1 §19 그대로 상속**:

1. **CSS 라이브러리·UI 프레임워크 금지** — Tailwind / Bootstrap / Material UI / styled-components / Chakra 등 도입 금지. **순수 CSS만**.
2. **모든 디자인 값은 `:root`의 CSS 변수로** — `styles/tokens.css` 한 파일에 [A] BASE + [B] THEME 으로 두고, 모든 페이지에서 `var(--...)`로 참조.
3. **임의 HEX / 임의 px / 임의 폰트 금지** — 새 값 필요하면 본 파일 §2/§15 에 *변수 먼저 추가*하고 사용.
4. **아이콘 = Lucide만**, **폰트 = Pretendard + Agbalumo + 시스템 모노만**. 추가 라이브러리·새 웹폰트 CDN 도입은 *CEO 승인* 필요.
5. **변수 네이밍 일관성** — era 신규 토큰은 `--retro-*` / `--minihome-*` / `--state-*` 네임스페이스 유지.
6. **개별 간격은 변수 늘리지 말고 기존 토큰으로** — 한 섹션만 다른 간격이 필요하면 *기존 토큰*을 인라인으로.

---

## §출처 잠금 (변경 시 강체크 reference)

- **docs/06 §3-2** — 모노 질감 = "기계가 복구 중" 자질. `--font-family-mono` 의 *기능적 정당성*.
- **docs/06 §3-3** — 미니홈피 스킨 파스텔 + 캠코더 비디오 신호색 출처 잠금. **매끈 글로우 금지선**. 본 스타일 §2.1 무광 가드의 뿌리.
- **docs/06 §3-6** — 적목 인물 금지 / 퇴폐 코드 시각 가드레일. `--retro-redeye` 사용 규칙.
- **docs/06 §4-1** — "깨짐=디폴트, 복원=보상" 원리 → `--state-broken*` / `--state-restoring` / `--state-restored` 토큰화.
- **docs/06 §6-1** — 자체 명칭 치환 (도토리→KEY, 파도타기→RIDE, 미니미→PIXEL SELF…). §13 카피 규칙.
- **docs/06 §6-2** — KEY 아이콘 / RIDE 아이콘 / PIXEL SELF UX 역할과 시각 스펙.
- **docs/06 §6-3, §6-4** — 색 레이어·토큰 매핑 표.
- **docs/14 §4** — 시안 ③ Lilac/Mint Y2K 13개 HEX (CEO 확정 2026-06-23). 본 스타일 §2.1/§2.7~§2.9 의 진실 소스.
- **docs/14 §0** — 싸이 회피 가드 (주황-빨강 직격 회피 → 매리골드 노랑쪽).
- **docs/09 §b·c** — 룩앤필 추상화선 (복제 금지 / 통상 형태 OK). 미니미·도토리 *형상* 절대 회피, 카운터·BGM·메뉴 *레이아웃 골격*만 통상 형태 안에서 추상화.
- **스타일 #1 §15·§18·§19** — BASE 캐논 토큰 / 테마 오버라이드 룰 / 코드 컨벤션. RE:WAVE 는 #1 의 구조 토큰을 *그대로 상속*.
