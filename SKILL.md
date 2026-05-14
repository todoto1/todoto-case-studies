# todoto case studies — 제작 가이드

todoto 운영 도구 5개(alimtalk·hub·landing·sns·slide)의 케이스 스터디를 동일한 톤·구조·디자인으로 유지하기 위한 가이드. flow 패턴(세로 플로우차트 + 가로 3단계 + 단계별 상세 + 결과 카드 + 인터뷰) 기준.

새 case 추가·기존 case 수정 시 이 문서를 먼저 읽고 작성한다.

## 디렉토리

```
case-studies/
├── style.css          공통 디자인 토큰 + 모든 CSS 클래스
├── index.html         대시보드 (4 카드)
├── alimtalk.html      각 case 페이지
├── hub.html
├── landing.html
├── sns.html
├── SKILL.md           이 문서
├── .nojekyll          GitHub Pages 설정
└── assets/icons/      도구 로고 (claude-code·solapi·notion·imweb·github·instagram)
```

배포: GitHub Pages → `https://todoto1.github.io/todoto-case-studies/`

## 디자인 토큰 (style.css `:root`)

| 토큰 | 값 | 용도 |
|---|---|---|
| `--brand` | `#000cfe` | 메인 강조 (번호·라벨·강조 단어·AFTER 박스·CTA) |
| `--brand-bright` | `#4D6FFF` | 다크 배경 위 강조 (체크·화살표) |
| `--brand-soft` | `#EFF1FF` | 「바꿨더니」 박스·AFTER 시간 박스 |
| `--ink` | `#0F0F0F` | Hero·AFTER 검정 배경 |
| `--ink-2` | `#1A1A1A` | CTA-band 배경 |
| `--bg-soft` | `#F7F7F5` | 인용 카드·플로우 board·인터뷰 박스 |
| `--gray` | `#555` | 본문 보조 |
| `--line` | `#E5E5E5` | 구분선·테두리 |
| 빨강 강조 | `#E74C3C` | 루프 박스·페인 정량 숫자 |
| 보충 todo | `#FFF4B8` / `#946400` | 노란 경고 마크 |

**규칙**:
- 메인 컬러(`--brand`)는 **본문 강조에만** — 큰 배경면 X (눈 피로 방지)
- Hero·CTA·AFTER 큰 배경은 검정(`--ink`)
- 빨강 강조는 「문제·반복·페인」 의미일 때만

## 페이지 구조 (모든 case 공통)

```
1. case-nav                       🏠 대시보드 + 4 case 링크
2. hero (검정)                    한 줄 메시지 + 4 불릿 + CTA
3. intro                         "BEFORE → AFTER" 짧은 요약
4. Chapter 1 — 문제              세로 일자형 플로우차트 + 빨간 루프 배지 + 정량 박스 4개
5. Chapter 2 — 솔루션            가로 3단계 도구 카드 + 단계별 상세 3
6. Chapter 2.5 — 시행착오        「처음에는 → 바꿨더니」 카드 5개
7. Chapter 3 — 결과              도구별 시간 절약 카드 3개 + 인터뷰 Q&A 4개
8. after-section (검정)          BEFORE/AFTER 좌우 비교 + CTA-band
9. footer                       짧은 메타
```

## 섹션별 작성 원칙

### Hero
- `<h1>` 2줄, 핵심 변화. `<em>`로 키워드 강조 (`--brand-bright` 자동)
- 예: `1인 브랜드의 카카오 알림톡을<br><em>카피·검수·발송</em> 한 흐름으로`
- 불릿 4개 — 핵심 기능·차별점
- CTA: `전체 스토리 보기 →`

### Chapter 1 — 문제 (세로 플로우차트)
- `flow-board.with-total` 컨테이너:
  - 시작 캡슐 (`flow-cap` "시작")
  - flow-box 8개 (번호·내용·시간) + flow-link 점선 사이
  - 종료 캡슐
  - `flow-total` 우측 빨간 배지 (border-radius 10px, 「N마다 반복」 + 부제)
- 그 다음 `pain-stats` 4 카드 (빨간 숫자 + 라벨)

### Chapter 2 — 솔루션 (가로 3단계 + 단계별 상세)
- 가로 3단계 (`flow-horizontal`):
  - 각 카드 (`flow-h-step`): 검정 배지(✦ N단계) + 도구 아이콘 img + 도구 이름 + 기능 박스 2개
  - 카드 사이 → 화살표
- 단계별 상세 (`stage-detail`) 3개:
  - 라벨 + 헤드라인 + 본문 + placeholder 이미지 + 「핵심 동작」 체크리스트

### Chapter 2.5 — 시행착오
- `trial-card` 5개
- 좌(`tbox` 회색) = 「처음에는」: 구체적 문제
- 우(`tbox.fix` 파랑) = 「바꿨더니」: `<strong>` 해결 + 효과
- 가운데 → 화살표

### Chapter 3 — 결과 (시간 절약 카드 + 인터뷰)
- `result-cards` 3 카드:
  - 단계 배지 + 도구 아이콘 + 도구 이름 + BEFORE 시간 회색 + ▼ + AFTER 시간 파랑 강조
- `interview` (`iv-item` 4개):
  - 파란 Q + 답변 자리 (todo 마크 + 예시)

### after-section (마무리)
- BEFORE/AFTER 좌우 비교 카드 (`ba-grid`)
- `cta-band` 검정 + 파랑 버튼

## 카피 톤 규칙

**일반인 친화가 최우선**. 비기술자도 이해해야.

| 기술 용어 | 일상 표현 |
|---|---|
| dispatcher / msgType 분기 | 용도별 AI 분리 |
| SSE 스트리밍 | 글이 흘러나오듯 점진 표시 |
| REST API 직접 호출 | 공식 안내 말고 내부 주소 찾아서 |
| catch-up 로직 | "X시간 지났으면 자동 보정" |
| multi-source DB | 노션 새 형식 |
| rich_text 속성 | 짧은 메모 자리 |
| page body blocks | 노션 카드 본문 |

**금지**: 영문 약어 그대로 노출·"최적화/효율적인/강력한" 마케팅 형용사·기술 프레임워크 이름.
**필수**: 비유·일상 단어·구체 수치 (시간·건수·비용).

## 도구 아이콘 자산

`assets/icons/`에 위치. 모두 PNG/JPG.

| 파일 | 도구 |
|---|---|
| `claude-code.png` | Claude Code |
| `solapi.png` | 솔라피 (알림톡 발송) |
| `notion.png` | Notion |
| `imweb.jpg` | 아임웹 (블로그·랜딩 발행) |
| `github.png` | GitHub Actions (sns 데이터 수집) |
| `instagram.png` | Instagram (sns 분석 대상) |

**사용 위치**: `flow-h-step .h-tool-mark img` (Chapter 2) + `result-card .rc-tool-img` (Chapter 3)

**자체 도구**(외부 로고 X): 큰 텍스트·이모지로 표시 (예: STEP 0의 "0", Reviewer의 ✓)

## case별 도구 카드 (Chapter 2 가로 3단계)

| Case | 1단계 | 2단계 | 3단계 |
|---|---|---|---|
| **alimtalk** | Claude Code (카피 생성) | 솔라피 (등록·발송) | Notion (결과 정리) |
| **hub** | Claude Code (본문·HTML) | Reviewer ✓ (검수) | 아임웹 (발행) |
| **landing** | STEP 0 (기본 정보) | Claude Code (섹션 카피) | 아임웹 (발행) |
| **sns** | GitHub Actions (수집) | Notion (저장) | Claude Code (분석) |
| **slide** | Notion (자료·일정) | Claude Code (14장 생성) | Notion (자동 정리) |

## 모바일 반응

`style.css` `@media (max-width: 640px)` 블록.

원칙:
- 폰트 다운스케일 (h1 36→26 · h2 28~32→22~24 · 본문 16→14)
- `container` padding 24→16px
- 가로 그리드(trial·BEFORE·BA-grid·flow-horizontal·result-cards·pain-stats) → 1열
- 화살표 → 90도 회전
- 도구 아이콘 56→44px

## 보충 필요 (todo) 마크

`<span class="todo">보충 필요</span>` + 예시 텍스트.

사용 시점:
- 사용자만 알 수 있는 정보 (시작 계기·시기·정량 수치·외주 비용)
- 인터뷰 답변 자리
- 스크린샷 placeholder는 `placeholder-img` 또는 `stage-screenshot` 클래스로 별도

## 새 case 추가 체크리스트

1. `<case>.html` 새 파일 (기존 case 복사 후 콘텐츠 교체)
2. case-nav에 새 링크 추가 (모든 기존 case의 nav도 동일 업데이트)
3. `index.html` `case-grid`에 새 카드 추가
4. 도구 아이콘 필요 시 `assets/icons/`에 추가
5. SKILL.md의 「case별 도구 카드」 표 갱신
6. commit + push

## 새 디자인 토큰·패턴 추가 시

1. `style.css` `:root`에 토큰 정의
2. 데스크톱 + 모바일 미디어 쿼리 둘 다 작성
3. SKILL.md 디자인 토큰 표 갱신
4. 1개 case에 먼저 적용 후 검증 → 나머지 case 일괄

## 푸시·배포

```powershell
git -C "C:\Users\USER\Desktop\클로드 코드\case-studies" add .
git -C "..." commit -m "..."
git -C "..." push
```

GitHub Pages가 1~2분 후 자동 재배포.

## 외부 공유 워크플로우 (GitHub Pages + 아임웹)

### 1. GitHub Pages — 메인 호스팅

URL: `https://todoto1.github.io/todoto-case-studies/`

- 코드 push만 하면 1~2분 후 자동 재배포
- 외부 사람에게 URL만 보내면 됨
- 카톡·DM·메일 공유에 그대로 사용

### 2. 카톡·SNS 미리보기 — OG meta tags

각 HTML head에 `<meta property="og:...">` 박힘 (적용 완료).

활성화 조건:
- `assets/og-default.png` (1200×630px 이미지) 추가 필요 — 사용자 액션
- 추가 후 카톡에 URL 붙이면 자동 미리보기 카드 표시
- 파비콘은 `assets/icons/favicon.png` 추가하면 브라우저 탭에 표시

case별 다른 이미지 원하면 `og-alimtalk.png` 등 분리 + 각 HTML의 `og:image` 경로 갱신.

### 3. 아임웹 임베드 — iframe 방식 (권장)

아임웹 본문에서 외부 CSS·JS는 작동 안 함. 가장 깔끔한 방법은 iframe:

```html
<iframe src="https://todoto1.github.io/todoto-case-studies/alimtalk.html"
        width="100%"
        height="3000"
        frameborder="0"
        style="border:0;"></iframe>
```

- 한 줄로 GitHub 페이지 그대로 임베드
- GitHub에서 수정하면 아임웹 자동 반영
- height는 페이지 길이에 맞춰 조정 (각 case 2500~3500px 권장)

### 4. 아임웹 인라인 — 통합 디자인 원할 때 (선택)

iframe 안 쓰고 아임웹 페이지에 완전 흡수하고 싶으면:

1. style.css 전체 내용을 HTML `<style>` 블록으로 인라인화
2. 모든 img·assets 경로를 절대 URL로 변경 (예: `https://todoto1.github.io/todoto-case-studies/assets/icons/claude-code.png`)
3. 아임웹 본문 인라인 HTML에 붙여넣기

작업량: 1편당 약 10분. 추후 GitHub 갱신해도 아임웹은 별도 수정 필요.

### 5. 표준 작업 흐름

```
콘텐츠 수정 (각 HTML)
    ↓
git push → GitHub Pages 자동 재배포 (1~2분)
    ↓
[외부 공유] URL 그대로 보냄 (카톡·DM·메일)
    ↓
[아임웹] iframe만 그대로 유지 — 자동 반영
```

수정·배포 분리: GitHub에서 수정 → 아임웹은 건드릴 일 없음.

## 향후 보강 영역

- 실제 스크린샷 첨부 (placeholder 자리)
- 정량 수치 보충 (todo 마크된 곳)
- 영상 임베드
- 영문 버전 (글로벌 노출 시)
- 5번째 case 추가 시 case-grid 레이아웃 재검토
