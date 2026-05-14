# 스크린샷 자리

## 폴더 구조

```
assets/screenshots/
├── alimtalk/
│   ├── 01-claude-code.png    Chapter 2 (1) AI 카피 생성·검수
│   ├── 02-solapi.png         Chapter 2 (2) 솔라피 캠페인 모달
│   └── 03-notion.png         Chapter 2 (3) 노션 자동 정리
├── hub/
│   ├── 01-claude-code.png    Chapter 2 (1) 본문·HTML 생성
│   ├── 02-reviewer.png       Chapter 2 (2) 자동 검수
│   └── 03-imweb.png          Chapter 2 (3) 아임웹 발행
├── landing/
│   ├── 01-step0.png          Chapter 2 (1) STEP 0 입력
│   ├── 02-claude-code.png    Chapter 2 (2) 섹션별 카피 3안
│   └── 03-imweb.png          Chapter 2 (3) HTML 저장·발행
├── sns/
│   ├── 01-github.png         Chapter 2 (1) GitHub Actions 자동 수집
│   ├── 02-notion.png         Chapter 2 (2) 노션 4-DB
│   └── 03-claude-code.png    Chapter 2 (3) Claude Code 인사이트
└── slide/
    ├── 01-notion.png         Chapter 2 (1) 노션 일정함 + 슬라이드 폼
    ├── 02-claude-code.png    Chapter 2 (2) 14장 자동 생성
    └── 03-notion.png         Chapter 2 (3) 슬라이드 카드 목록
```

## 파일명 규칙

`<번호>-<이름>.png`
- 번호: `01·02·03` (Chapter 2 단계와 일치)
- 이름: 도구·기능명 (영문 소문자·하이픈)
- 형식: PNG 권장 (JPG도 OK)

## 권장 크기

- 가로 **1200~1600px** (가로폭 큰 화면)
- 비율 16:9 또는 4:3
- 용량 500KB 이하 (페이지 로딩 속도)

## 사용 방법

각 case HTML의 Chapter 2 단계별 상세 안 `stage-screenshot` div가 자동으로 이미지를 찾습니다.

**파일을 위 폴더 구조대로 넣기만 하면** `<img onerror="...">` 분기가 처리해 자동 표시:
- 이미지 있음 → 이미지 표시
- 이미지 없음 → "[스크린샷 자리 — ...]" placeholder 표시

HTML 수정 불필요.

## 작업 흐름

1. 스크린샷 캡처 (Win+Shift+S / Cmd+Shift+4)
2. 위 폴더 구조의 정확한 위치에 위 파일명으로 저장
3. `git add . && git commit && git push`
4. 1~2분 후 GitHub Pages 자동 반영
