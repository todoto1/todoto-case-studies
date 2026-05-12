# todoto case studies — 제작 가이드

todoto 운영 도구 4개(alimtalk·hub·landing·sns)의 케이스 스터디를 동일한 톤·구조·디자인으로 유지하기 위한 가이드.

새 case 추가·기존 case 수정 시 이 문서를 먼저 읽고 작성한다.

## 디렉토리

```
case-studies/
├── style.css          공통 디자인 토큰 + 모든 CSS 클래스
├── index.html         대시보드 (4 카드 + 인덱스 헤더·푸터)
├── <case>.html × 4    각 case 페이지
├── SKILL.md           이 문서
└── .nojekyll          GitHub Pages 설정
```

배포: GitHub Pages → `https://todoto1.github.io/todoto-case-studies/`

## 디자인 토큰 (style.css `:root`)

| 토큰 | 값 | 용도 |
|---|---|---|
| `--brand` | `#000cfe` | 메인 강조 (번호·라벨·강조 단어) |
| `--brand-bright` | `#4D6FFF` | 다크 배경 위 강조 (체크·화살표) |
| `--brand-soft` | `#EFF1FF` | 시행착오 「바꿨더니」 박스 |
| `--ink` | `#0F0F0F` | Hero·AFTER 검정 배경 |
| `--ink-2` | `#1A1A1A` | CTA-band 배경 |
| `--bg-soft` | `#F7F7F5` | 인용 카드·BEFORE 다이어그램 배경 |
| `--gray` | `#555` | 본문 보조 |
| `--line` | `#E5E5E5` | 구분선·테두리 |
| 보충 필요 (todo) | `#FFF4B8` / `#946400` | 노란 경고 마크 |

**규칙**:
- 메인 컬러(`--brand`)는 **본문 강조에만** 사용 — 큰 배경면엔 절대 X (눈 피로 이슈)
- Hero·CTA·AFTER 같은 큰 배경은 검정(`--ink`)
- 강조 파랑은 번호·라벨·핵심 단어에만

## 페이지 구조 (모든 case 공통)

```
1. case-nav                       🏠 대시보드 + 4 case 링크
2. hero (검정)                    한 줄 메시지 + 4 불릿 + CTA
3. intro                         "BEFORE → AFTER" 짧은 요약
4. step 01 — 왜 만들었나          인용 카드 + 페인 포인트 5
5. step 02 — 어떻게 풀었나        시행착오 카드 5~6
6. step 03 — 실제 동작            핵심 화면 1~2개
7. before-section (회색)         BEFORE 3박스 다이어그램
8. after-section (검정)          BEFORE/AFTER 좌우 비교 + CTA
9. footer                       짧은 메타
```

## 섹션 작성 원칙

### Hero
- `<h1>` 2줄, 핵심 변화. `<em>`로 키워드 강조 (`--brand-bright` 색 자동)
- 예: `1인 브랜드의 카카오 알림톡을<br><em>카피·검수·발송</em> 한 흐름으로`
- 불릿 4개 — 핵심 기능·차별점
- CTA: `전체 스토리 보기 →`

### Intro
- `<h2>`: BEFORE → AFTER 한 줄 변환. `<em>` AFTER 부분 강조
- 예: `디자이너 1주 → <em>30분 셀프</em>`
- `<p>` 2~3 문장 도입

### Step 01 — 왜 만들었나
- `case-card` 인용: 실제 운영자 시점 1~2 문단. `<strong>`로 핵심 수치 강조
- `pain-list` 5개. 각 항목 첫 부분 `<strong>`
- 끝에 `<span class="todo">보충 필요</span>` — 구체 계기·시기 자리

### Step 02 — 어떻게 풀었나
- `trial-card` 5~6개
- 카드 제목은 한 줄 (실패 패턴 요약)
- 좌(`tbox` 회색) = 「처음에는」: 구체적 문제 상황 + 결과
- 우(`tbox.fix` 파랑) = 「바꿨더니」: `<strong>` 해결 방식 + 효과
- 박스 본문 2~3 문장, **일반인 친화 언어 필수**

### Step 03 — 실제 동작
- `screen-card` 1~2개 (3개 이상 X — 인지 부담)
- `placeholder-img` 큰 자리 (320px)
- 구조: label + h4 + p (기능 설명 2~3 문장)

### BEFORE 다이어그램
- 3박스 가로 (모바일 1열)
- 각 박스: 번호 + 도구명 + 짧은 설명
- 하단 `before-summary-bar`: `총 X단계 · 툴 옮기고 복붙하고…` 패턴

### AFTER 섹션
- `ba-grid` 좌우: BEFORE 카드(회색 박스) + AFTER 카드(파랑 박스)
- 각 카드에 단계 리스트(`<ol>`)
- 카드 하단 `summary`: 단계 수·도구 수 비교
- `cta-band` 검정 배경 + 파랑 버튼

## 카피 톤 규칙

**일반인 친화가 최우선**. 비기술자도 이해해야 한다.

| 기술 용어 | 일상 표현 |
|---|---|
| dispatcher / msgType 분기 | 용도별 AI 분리 |
| SSE 스트리밍 | 글이 흘러나오듯 점진 표시 |
| REST API 직접 호출 | 공식 안내 말고 내부 주소 찾아서 |
| catch-up 로직 | "X시간 지났으면 자동 보정" |
| multi-source DB | 노션 새 형식 |
| rich_text 속성 | 짧은 메모 자리 |
| page body blocks | 노션 카드 본문 |
| Prompt caching | (이런 건 안 노출) |

**금지**:
- 영문 약어 그대로 노출 (CTX_FIELDS·AGENT.md 같은 식별자)
- "최적화", "효율적인", "강력한" 같은 마케팅 형용사
- 기술 라이브러리·프레임워크 이름 (Flask·Express 등)

**필수**:
- 비유·일상 단어
- 구체 수치 (시간·건수·비용)

## 시행착오 카드 패턴

```html
<div class="trial-card">
  <div class="ti">
    <div class="tn">번호</div>
    <div class="tt">한 줄 요약 — 어떤 문제였나</div>
  </div>
  <div class="tarrow">
    <div class="tbox">
      <span class="tlabel">처음에는</span>
      구체적 문제 상황 + 결과
    </div>
    <div class="arrow-mid">→</div>
    <div class="tbox fix">
      <span class="tlabel">바꿨더니</span>
      <strong>해결 방식</strong> + 효과
    </div>
  </div>
</div>
```

원칙:
- 카드 제목은 **결과 중심** (X 안 됨·시간 낭비·톤 흔들림 등)
- 「처음에는」은 **왜 시도했나·뭐가 잘못됐나**
- 「바꿨더니」는 **무엇을·어떻게·결과**

## 모바일 반응

`style.css` `@media (max-width: 640px)` 블록 + `index.html` 안 inline `<style>` 블록.

원칙:
- 폰트 다운스케일 (h1 36→26 · h2 28~32→22~24 · 본문 16→14)
- `container` padding 24→16px
- 가로 그리드(trial·BEFORE·BA-grid) → 세로 1열
- 화살표 → 90도 회전
- placeholder 320→180px

**새 폰트·여백 추가 시 모바일 대응 동시 작성** (잊기 쉬움).

## 보충 필요 (todo) 마크

`<span class="todo">보충 필요</span>` + 예시 텍스트로 표시.

사용 시점:
- 사용자만 알 수 있는 정보 (시작 계기·시기·정량 수치·외주 비용)
- 시행착오 추가 자리
- 운영 효과 정량 수치

색: 노란 배경 (메인 파랑과 별개 — 「경고·미완」 의미)

## 새 case 추가 체크리스트

1. `<case>.html` 새 파일 (기존 case 복사 후 콘텐츠 교체)
2. `case-nav`에 새 링크 추가 (모든 기존 case의 nav도 동일하게 업데이트)
3. `index.html` `case-grid`에 새 카드 추가 (이모지·tag CASE 0N·h3·BEFORE/AFTER 한 줄)
4. SKILL.md 갱신 (디자인 토큰·섹션 추가했으면)
5. commit + push

## 새 디자인 토큰·패턴 추가 시

1. `style.css` `:root`에 토큰 정의
2. 데스크톱 + 모바일 미디어 쿼리 둘 다 작성
3. SKILL.md 디자인 토큰 표 갱신
4. 1개 case에 먼저 적용 후 검증 → 나머지 case 일괄

## 푸시·배포

```powershell
git -C "C:\Users\USER\Desktop\클로드 코드\case-studies" add .
git -C "C:\Users\USER\Desktop\클로드 코드\case-studies" commit -m "..."
git -C "C:\Users\USER\Desktop\클로드 코드\case-studies" push
```

GitHub Pages가 1~2분 후 자동 재배포.

## 향후 보강 영역

- 영상 임베드 (현재 placeholder-img만)
- 실제 스크린샷 첨부 (todo 마크된 placeholder 자리)
- 정량 수치 보충 (todo 마크된 곳)
- 영문 버전 (글로벌 노출 시)
- 5번째 case 추가 시 case-grid 레이아웃 재검토 (2x2 → 2x3 또는 3x2)
