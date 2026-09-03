# 바른부동산 — 브랜드 사이트 시안

서울 실거래 리포트를 챕터 5개로 보여 주는 한 페이지 사이트. 정적 파일만 쓴다(빌드 없음).
배포는 Nestify 정적 호스팅 전제라 GitHub Actions 워크플로를 두지 않는다.

## 파일

- `index.html` — 사이트 전부. CSS·JS 인라인
- `assets/report/*.png` — 리포트 이미지 5장. seoul-property-dashboard 의
  `npm run report` 산출물을 복사한 것(2026-09-03 수집분).
  "최근 신고분"은 직전 수집(8/31) 대비 새로 들어온 824건이다
- `assets/fonts/plex-mono-*.woff2` — 숫자용 IBM Plex Mono. 한글 Pretendard 는 CDN
- `assets/hero-seoul.png` — 히어로 배경 원본(2752×1536, Nano Banana Pro 생성).
  **지우지 말 것** — 영상화할 때 첫 장면으로 쓴다
- `assets/hero-seoul.webp` / `.jpg` — 웹용 축소본(2400×1340). 화면은 webp 를 쓰고
  `image-set` 을 모르는 브라우저는 jpg 로 떨어진다. jpg 는 영상의 poster 도 겸한다
- `assets/hero-seoul.mp4` — 히어로 배경 영상(1920×1080, 8.04초, 무음, 6.1MB).
  Seedance 2.0 에 위 PNG 를 start_image·end_image 로 함께 넣어 만들었다 —
  끝 프레임이 첫 프레임으로 돌아와야 `loop` 이음새가 안 보인다.
  **데스크톱에서만 재생된다.** 휴대폰(≤720px)과 모션 최소화 설정에서는 `display:none`
  이고 그 아래 `.hero-media` 이미지가 그대로 보인다

## 색

| 역할 | 값 |
|---|---|
| 바탕 | `#14181F` 잉크 네이비 |
| 글자 | `#E8ECF2` 페이퍼 그레이 |
| 구분선·카드 | `#3E4756` 슬레이트 |
| 포인트 | `#FF6B5E` 코랄 레드 — 하나만 |
| 하락 | `#6BA8FF` — **데이터 영역 안에서만** 쓰는 예외 |

## 로고

원본 `로고.png` 는 이미 알파 채널이 있어 흰 바탕이 없었다(뷰어 배경이 희게 보인 것).
다만 마크가 alpha 166, 글자가 alpha 140 인 반투명이고 글자가 검정이라 잉크 네이비 위에서
색이 죽고 글자가 사라진다. 그래서 세 벌을 둔다.

- `assets/logo.png` — 원본 그대로
- `assets/logo-light.png` — 알파를 불투명으로 올리고 검정 글자를 페이퍼 그레이로. 푸터에서 쓴다
- `assets/logo-mark.png` — 마크만 잘라낸 것. 헤더에서 쓴다

원본은 마크 위 / 글자 아래로 세로로 쌓인 형태라, 가로 헤더에서 통째로 34px 로 줄이면
"공인중개사사무소" 가 읽히지 않는다. 헤더는 마크만 쓰고 글자는 옆에 텍스트로 세웠다.

## 아직 안 된 것

- **영상 파일 최적화** — mp4 가 6.1MB 이고 `moov` 가 파일 끝에 있다(faststart 아님).
  이 맥에 ffmpeg 이 없어 손대지 않았다. 깔면
  `ffmpeg -i hero-seoul.mp4 -c:v libx264 -crf 26 -movflags +faststart -an out.mp4`
  로 용량과 첫 재생 지연을 함께 줄일 수 있다
- **자치구 필터** — 자치구별 데이터를 싣지 않아 선택값이 표시와 대시보드 링크에만 반영된다
