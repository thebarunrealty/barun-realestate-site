# 바른부동산 — 브랜드 사이트 시안

서울 실거래 리포트를 챕터 5개로 보여 주는 한 페이지 사이트. 정적 파일만 쓴다(빌드 없음).
배포는 Nestify 정적 호스팅 전제라 GitHub Actions 워크플로를 두지 않는다.

## 파일

- `index.html` — 사이트 전부. CSS·JS 인라인
- `assets/report/*.png` — 리포트 이미지 5장. seoul-property-dashboard 의
  `npm run report` 산출물을 복사한 것(2026-08-15 렌더, 2026-08-13 수집분)
- `assets/fonts/plex-mono-*.woff2` — 숫자용 IBM Plex Mono. 한글 Pretendard 는 CDN

## 색

| 역할 | 값 |
|---|---|
| 바탕 | `#14181F` 잉크 네이비 |
| 글자 | `#E8ECF2` 페이퍼 그레이 |
| 구분선·카드 | `#3E4756` 슬레이트 |
| 포인트 | `#FF6B5E` 코랄 레드 — 하나만 |
| 하락 | `#6BA8FF` — **데이터 영역 안에서만** 쓰는 예외 |

## 아직 안 된 것

- **로고** — 파일을 못 받아 헤더가 텍스트 워드마크다. `assets/logo.png` 를 넣고
  `index.html` 의 `.brand-mark` + `.wordmark` 두 요소를 `<img>` 하나로 바꾸면 된다
- **히어로 배경 영상** — 그라데이션 자리표시. `.hero-media` 를 `<video>` 로 교체
- **자치구 필터** — 자치구별 데이터를 싣지 않아 선택값이 표시와 대시보드 링크에만 반영된다
