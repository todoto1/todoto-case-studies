# 도구 아이콘

각 case study의 Chapter 2 도구 마크에 사용할 로고 파일.

## 권장 파일 (alimtalk-flow 기준)

| 파일명 | 도구 | 비고 |
|---|---|---|
| `claude-code.svg` | Claude Code (Anthropic) | 별 모양 로고 |
| `solapi.svg` | 솔라피 | 솔라피 공식 로고 |
| `notion.svg` | Notion | 검정 N |

## 추후 case별 추가 예정

| 파일명 | 도구 | 사용처 |
|---|---|---|
| `aimweb.svg` | 아임웹 | hub·landing |
| `instagram.svg` | Instagram | sns |
| `github.svg` | GitHub | sns (Actions cron) |

## 권장 형식

- **SVG 우선** (벡터, 색·크기 자유)
- PNG fallback 시: 128×128px 이상
- 정사각형 비율 (1:1)
- SVG viewBox: `0 0 24 24` 또는 `0 0 32 32`

## 색상

- 단색 SVG 권장 — 박스 배경에 흰색 stroke/fill로 보이게
- 박스 배경 색은 HTML 인라인 style에서 지정:
  - Claude Code: `#D97757` (Anthropic Sunset)
  - 솔라피: `#6B5BFF` (보라, 또는 솔라피 공식 색)
  - Notion: `#000` (검정)

## 적용 방식

파일을 이 폴더에 넣은 후, `alimtalk-flow.html`의 `<svg>` 인라인을 `<img>`로 교체:

```html
<div class="h-tool-mark" style="background:#D97757;">
  <img src="assets/icons/claude-code.svg" alt="Claude Code" width="32" height="32">
</div>
```

## 출처 추천

- Simple Icons: https://simpleicons.org/ (대부분 공식 로고 SVG 무료)
- 각 도구 공식 브랜드 가이드 페이지
