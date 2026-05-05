# RE:FEEEL Viewer App — 유저 페이지 와이어프레임

RE:FEEEL 하이브리드 앱의 유저 페이지 와이어프레임 HTML입니다.
각 파일은 CSS/JS 인라인으로 독립 실행 가능하며, 로컬에서 브라우저로 열면 페이지 간 네비게이션이 동작합니다.

---

## 파일 구조

```
refeeel-viewer/
├── README.md
├── mypage.html          마이페이지
├── rekit.html            RE:KIT 목록 (큐레이션 + 탐색)
├── rekit-detail.html     RE:KIT 상세 읽기 (RE:KIT 64 샘플)
└── classes.html          클래스 목록 + 챕터 상세
```

---

## 페이지별 상세

### 1. mypage.html — 마이페이지

| 영역 | 설명 |
|---|---|
| GNB | 모바일 전용 "MY PAGE" 중앙 텍스트 (데스크탑 숨김) |
| 히어로 | 프로필 이미지 + 이름 + 이메일 + 뱃지(구독중/Gold) + 스탯 3칸(하이라이트/저장된RE:KIT/클래스진행률) |
| 탭 | RE:KIT / 클래스 / 하이라이트 / 계정 (sticky) |
| RE:KIT 탭 | 서브카테고리(읽는중/완독/저장) + 이미지 카드 그리드 |
| 클래스 탭 | 상품 카드 → 클릭 시 `classes.html?detail=brand` 또는 `?detail=content`로 이동 |
| 하이라이트 탭 | 콘텐츠별 하이라이트 목록 → 상세 → 해당 위치 이동 |
| 계정 탭 | 구매이력/회원정보 → refeeel.com 이동, 로그아웃 |
| 하단 네비 | RE:KIT / CLASS / NAKTA AI / MY (MY active) |

### 2. rekit.html — RE:KIT 목록

| 영역 | 설명 |
|---|---|
| GNB | RE:FEEEL 로고 + 데스크탑 네비(RE:KIT active) + 햄버거 메뉴. `position:absolute` (스크롤 시 안 따라옴). 모바일에서 로고 클릭 비활성 |
| 히어로 | 다크 배경. "RE:Content Marketing" / "RE:KIT" / 카피 |
| 탭 네비 | 큐레이션 / 탐색 (sticky top:0). 스크롤로 브라우저 top 도달 시 배경 흰색 + 텍스트 다크 전환 (`.rk-tabs-light`) |
| 큐레이션 탭 | 히어로 카드(가로 슬라이더) + 17개 블록 (card/bigcard/thumbrow/grid 레이아웃) |
| 탐색 탭 | 검색 + 토픽 필터 슬라이더 + Filters 모달(Category/주제/실행조건) + 전체 리스트 |
| 하단 네비 | RE:KIT active |

**모바일 특이사항:**
- 슬라이더 카드(hero/card/bigcard)는 오른쪽이 브라우저 끝까지 확장 (숨겨져 있는 효과)
- 리스트형(thumbrow)/그리드형은 양쪽 패딩 유지
- 토픽 버튼 슬라이더도 오른쪽 숨김 효과 적용

**카드 링크:** RE:KIT 64 카드 클릭 → `rekit-detail.html`로 이동. 나머지는 `#`

### 3. rekit-detail.html — RE:KIT 상세 읽기

| 영역 | 설명 |
|---|---|
| 읽기 GNB | `position:fixed` (항상 상단 고정). ← 뒤로가기 + 진행률 바 + % 표시 + 저장 버튼 + 하이라이트 버튼 |
| 히어로 | 다크 배경 + SVG 비주얼(Content 카테고리 #f5ca43) + RE:KIT 64 타이틀/설명/태그 |
| 본문 | Chapter 01~06. 작가 카드(3열), 비교 패널(정돈된 글 vs 정돈 안 한 글), 크로스레퍼런스 카드, 방식 카드 |
| 하단 네비 | RE:KIT active |

**기능 상세:**

| 기능 | 동작 |
|---|---|
| 진행률 | 스크롤 기반 %. 최대값만 업데이트 (뒤로 스크롤해도 감소 안 함). 95% 이상 시 초록색 |
| 저장 | 클릭 → 아이콘 오렌지 채움 + "✓ 저장되었습니다." 토스트 모달. 재클릭 → "저장이 해제되었습니다." |
| 하이라이트 (데스크탑) | 버튼 클릭 → 모드 ON + 커서가 펜 아이콘 변경 → 본문 드래그 → "하이라이트 추가" 플로팅 버튼 → 클릭 시 오렌지 음영 + "✓ 하이라이트에 저장되었습니다." 토스트 |
| 하이라이트 (모바일) | 본문 드래그 → "하이라이트 추가" 플로팅 버튼 → 클릭 시 오렌지 음영 + 토스트 |

### 4. classes.html — 클래스 페이지

| 영역 | 설명 |
|---|---|
| GNB | RE:FEEEL 로고 + PROGRAM active + 햄버거 메뉴. `gnb-dark` 클래스 (다크 히어로 위) |
| 히어로 | "RE:CLASS" / "CLASS" / "실행은 하고 있는데, 기준을 모르겠다면." |
| 클래스 목록 | 상품 카드(제목 + 진행률 바 + 읽는 중 챕터 블록). 클릭 시 챕터 상세 진입 |
| 챕터 상세 | ← 목록으로 + 진행률 바 + 챕터 블록 리스트(라벨/제목/본문/태그/완독상태) |
| URL 파라미터 | `?detail=brand` 또는 `?detail=content`로 직접 상세 진입 가능 |
| 하단 네비 | CLASS active |

**브랜드 전략 클래스 (10개 챕터):**

| # | 라벨 | 제목 | 상태 |
|---|---|---|---|
| 00 | PROLOGUE | 이 클래스를 시작하기 전에 | 완독 |
| 01 | INTRO | 브랜딩이 사업이 되는 순간 | 완독 |
| 02 | IDENTITY | 정체성: 당신의 브랜드는 누구인가 | 완독 |
| 03 | WORLDVIEW | Why: 왜 굳이 이 사업을 하는가 | 완독 |
| 04 | POSITIONING | 포지셔닝: 당신의 브랜드의 위치는? | 완독 |
| 05 | TARGET | 타겟: 돈이 되는 사람은 누구인가 | 완독 |
| 06 | COMPETITION | 경쟁: 왜 꼭 당신이어야 할까? | 읽는중 45% |
| 07 | DIFFERENCE | 차별화: 당신만의 무기를 찾는 법 | 미시작 |
| 08 | MESSAGE | 원칙: 어떻게 말하고 드러낼 것인가 | 미시작 |
| 09 | COMPLETE | 브랜드를 완성하다 | 미시작 |

---

## 하단 네비게이션 (공통)

| 탭 | 파일 경로 | 아이콘 |
|---|---|---|
| RE:KIT | `rekit.html` | 육각형 |
| CLASS | `classes.html` | 책 |
| NAKTA AI | `#` (미구현) | 말풍선 |
| MY | `mypage.html` | 사람 |

768px 이하에서만 표시. `safe-area-inset-bottom` 적용.

---

## 디자인 토큰

| 항목 | 값 |
|---|---|
| 브랜드 컬러 | `#E75519` (오렌지) |
| GNB 활성 메뉴 | `#CF7F5E` |
| 본문 텍스트 | `#1a1a1a` |
| 보조 텍스트 | `#999` |
| 비활성 텍스트 | `#bbb` |
| 보더 | `#e5e5e5` |
| 카테고리 닷 | Marketing `#6465F5` / Branding `#e75519` / Content `#f5ca43` |
| 폰트 | Pretendard Variable (본문) + SUIT Variable (숫자/라벨) |
| max-width | 1200px (목록), 720px (읽기) |
| 반응형 BP | 767px (카드/탭), 768px (하단 네비), 640px (GNB 모바일) |

---

## CSS 네임스페이스

| 페이지 | 접두사 | 예시 |
|---|---|---|
| 마이페이지 | `my-` | `.my-hero`, `.my-tabs`, `.my-class-product` |
| RE:KIT 목록 | `rk-` | `.rk-hd`, `.rk-tabs-nav`, `.rk-cur-block` |
| RE:KIT 읽기 | `read-` / `digest-` | `.read-gnb`, `.digest-content`, `.digest-body` |
| 클래스 | `cl-` | `.cl-hd`, `.cl-class-product`, `.cl-chapter-block` |
| 공용 | `rf-` | `.rf-bottom-nav`, `.rf-active` |
| GNB | `digest-gnb` / `gnb-` | `.gnb-header`, `.gnb-desktop-nav`, `.gnb-menu-panel` |

---

## 페이지 간 연결 구조

```
mypage.html
├── 하단 RE:KIT → rekit.html
├── 하단 CLASS → classes.html
├── 하단 MY → mypage.html (현재)
├── 클래스탭 브랜드전략 카드 → classes.html?detail=brand
└── 클래스탭 콘텐츠마케팅 카드 → classes.html?detail=content

rekit.html
├── 하단 네비 → 각 페이지
├── RE:KIT 64 카드 → rekit-detail.html
├── GNB 햄버거 → 슬라이드 메뉴
└── 탭 전환 → 큐레이션 ↔ 탐색

rekit-detail.html
├── ← 뒤로가기 → rekit.html
├── 하단 네비 → 각 페이지
├── 하단 CTA → rekit.html
└── 저장/하이라이트 → 토스트 모달

classes.html
├── 하단 네비 → 각 페이지
├── 클래스 카드 클릭 → 챕터 상세 (인페이지 토글)
├── ← 목록으로 → 목록 복귀
├── ?detail=brand → 브랜드 상세 자동 진입
└── ?detail=content → 콘텐츠 상세 자동 진입
```

---

## 개발 시 참고사항

1. **로컬 실행**: 4개 HTML 파일을 같은 폴더에 두고 브라우저로 열면 네비게이션 동작
2. **실제 배포 시**: 링크를 `rekit.html` → `/rekit` 등 실제 라우팅 경로로 변경 필요
3. **아임웹 연동**: GNB 햄버거 메뉴의 링크(`/about`, `/brandingclassmain` 등)는 아임웹 URL
4. **데이터**: 현재 모든 데이터는 HTML 내 하드코딩. 실제 개발 시 Supabase API로 대체
5. **RE:KIT ITEMS 배열**: `rekit.html` 내 `window.__RK.ITEMS`에 64개 리킷 데이터 포함
6. **클래스 CLASSES 데이터**: `classes.html` 내 HTML로 직접 작성 (브랜드 10챕터, 콘텐츠 6챕터)
