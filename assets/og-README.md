# 외부 공유용 이미지 자리

## og-default.png (필수)

카톡·페북·트위터 등에 링크 공유 시 미리보기 카드에 표시될 이미지.

- 위치: `assets/og-default.png`
- 권장 크기: **1200×630px** (가장 안전, 모든 SNS 표준)
- 형식: PNG (또는 JPG)
- 내용: todoto 로고 + "case studies" 또는 비주얼

여기에 파일 하나 넣으면 6 case 페이지 모두 같은 미리보기 사용.

## icons/favicon.png (선택)

브라우저 탭 아이콘.

- 위치: `assets/icons/favicon.png`
- 권장 크기: 32×32 또는 64×64px (정사각)
- 형식: PNG

## case별 OG 이미지 (선택 — 추후 분리)

추후 case별로 다른 이미지를 쓰고 싶으면:

| 파일명 | 사용 case |
|---|---|
| `og-alimtalk.png` | alimtalk |
| `og-hub.png` | hub |
| `og-landing.png` | landing |
| `og-sns.png` | sns |
| `og-slide.png` | slide |

분리할 때 각 HTML의 `<meta property="og:image">` 경로 갱신 필요.
