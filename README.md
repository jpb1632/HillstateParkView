# HillstateParkView

힐스테이트 회룡역 파크뷰 분양 랜딩페이지 프로젝트입니다.
전체 브랜딩, 메인/상세 구조, 반응형 동선, 상담 전환 흐름, 공유 메타데이터까지 회룡역 파크뷰에 맞게 정리한 완료 버전입니다.

- 라이브 URL: `https://jpb1632.github.io/HillstateParkView/`
- 저장소: `https://github.com/jpb1632/HillstateParkView`
- 배포 방식: GitHub Pages

## 프로젝트 개요

이 프로젝트는 단순 이미지 교체 수준이 아니라, 실제 분양 랜딩페이지 운영 기준에 맞춰 다음 영역을 전반적으로 손본 버전입니다.

- 메인 히어로 영역 전체 리브랜딩
- PC/모바일 각각 다른 섹션 구성과 인터랙션 최적화
- 팝업, 프리미엄 슬라이더, 랜드스케이프 슬라이더, 유튜브 영상 동작 보강
- 상세 메뉴 페이지 구조 재설계
- 상담신청 이동/입력/전송 흐름 안정화
- 공유용 썸네일, 파비콘, 웹앱 메타데이터 정리
- 기본적인 콘텐츠 보호 로직 및 운영용 분석 스크립트 연결

## 사용 기술

### Frontend

- HTML5
- CSS3
- Vanilla JavaScript
- jQuery
- Swiper.js

### Tooling

- Node.js
- Gulp 4
- BrowserSync
- PostCSS

### External Integration

- Google Apps Script Webhook 기반 상담 폼 전송
- Google Analytics
- Microsoft Clarity
- Statcounter
- GitHub Pages 배포

## 핵심 구현 사항

### 1. 메인 랜딩페이지 커스터마이징

- 히어로 메인 슬라이드 이미지를 회룡역 파크뷰용 비주얼로 전면 교체
- 슬라이드별로 다른 텍스트 컬러, 테두리, 배지 스타일 적용
- 반응형 환경에서도 메인 카피가 과하게 밀리지 않도록 위치 로직 보정
- PC와 모바일에서 각각 다른 비율과 배치로 자연스럽게 보이도록 세부 조정

### 2. 팝업 UX 개선

- 메인 진입 팝업을 모바일 기준 무한 루프 구조로 개선
- 팝업 카드 양끝 복제 클론을 활용해 마지막에서 첫 장으로 넘어갈 때 끊김을 줄임
- 팝업 오버레이를 `body`로 hoist 해서 stacking/overflow 이슈 완화
- 오늘 하루 보지 않기 상태를 `localStorage`로 저장
- 상담 바로 진입 시 팝업이 흐름을 막지 않도록 예외 처리

### 3. 프리미엄/홍보 섹션 인터랙션

- PREMIUM 8 섹션을 Swiper 기반 자동 슬라이더로 구성
- 모바일에서는 프리미엄 이미지를 탭하면 라이트박스가 열리고, 확대/축소와 좌우 넘김이 가능하도록 구성
- 랜드스케이프 섹션은 단일 카드 중심의 고급스러운 슬라이드 흐름으로 재구성
- 스페셜, 기브어웨이, 프로모션 배너에 각각 다른 성격의 모션 효과 적용
- 기브어웨이 하단 일부 영역을 클릭하면 바로 상담신청 섹션으로 이동하도록 CTA 동선 추가

### 4. 섹션별 시각 효과

- `IntersectionObserver` 기반으로 섹션 진입 시 자연스럽게 올라오는 reveal 애니메이션 적용
- 입지환경 섹션에는 PC 전용 돋보기 확대 인터랙션 적용
- 특정 섹션만 돋보기를 유지하고, 나머지는 과한 효과를 제거해 가독성 중심으로 정리
- hover 시 카드가 떠오르는 느낌, 광택, 강조 모션 등을 섹션 성격에 맞게 차등 적용

### 5. 유튜브 영상 섹션 보강

- 유튜브 iframe을 API 방식으로 제어
- 화면에 일정 비율 이상 노출되면 자동 재생, 벗어나면 자동 일시정지
- 음소거/음소거 해제 토글 버튼 제공
- 섹션 reveal과 영상 재생 타이밍이 자연스럽게 이어지도록 구성

### 6. 상담 전환 흐름 안정화

- 상단 `방문예약` 버튼 클릭 시 상담신청 섹션으로 정확히 이동하도록 스크롤 로직 재설계
- 이미지/폰트/레이아웃이 안정된 뒤 스크롤하도록 preload + layout stable 로직 추가
- 메인 상담 폼과 하단 고정 빠른 상담 바 모두 입력 검증 적용
- 이름/휴대폰 번호 자동 정규화, 개인정보 동의 체크, 목적 선택 검증 포함
- Google Apps Script Webhook으로 실제 상담 데이터 전송

### 7. 상세페이지(menu-page) 재구성

- `group`, `tab`, `variant` 쿼리 파라미터 기반으로 상세 페이지를 동적으로 렌더링
- 사업안내 / 단지안내 / 타입안내 구조를 회룡역 파크뷰 기준으로 재편성
- 타입안내는 59㎡A, 59㎡B, 59㎡C, 84㎡A, 84㎡B, 84㎡C 버튼 구조로 정리
- 인테리어는 54㎡, 84㎡ 기준으로 별도 구성
- 커뮤니티, 마이힐스, H-시스템, 동호수배치도 등 상세 탭 콘텐츠를 실 운영 구조에 맞게 교체

### 8. 모바일 대응

- 모바일 메인 텍스트 위치 및 크기를 별도 보정
- 모바일 프리미엄, 입지환경, 커뮤니티, 포레스트, 타입안내 섹션을 모바일 전용 자산 기준으로 재구성
- 모바일 팝업 크기와 프리미엄 라이트박스 흐름을 터치 중심으로 개선
- 모바일에서는 불필요한 좌우 버튼을 줄이고 스와이프 중심 UX로 정리

### 9. 공유/브랜딩 메타데이터 정리

- 루트 `index.html`에서 Open Graph, Twitter Card, description, preview image 구성
- 공유 썸네일 이미지를 별도 관리
- favicon, apple-touch-icon, android icon, manifest, theme color 정리
- GitHub Pages와 공유 링크에서 회룡역 파크뷰 브랜딩이 유지되도록 메타 보강

### 10. 기본 콘텐츠 보호 로직

- 우클릭 방지
- 텍스트 선택 방지
- 이미지 드래그 방지
- 복사/잘라내기 방지
- `F12`, `Ctrl/Cmd + Shift + I/J/C`, `Ctrl/Cmd + U`, `Ctrl/Cmd + S` 등 일부 단축키 차단

참고:
브라우저 개발자도구를 완전히 막는 것은 불가능하므로, 이 로직은 일반 사용자의 무단 복사 난이도를 높이는 수준의 기본 보호 장치입니다.

## 폴더 구조

```text
HillstateParkView/
├─ index.html
├─ gulpfile.mjs
├─ package.json
├─ new-assets/
│  ├─ menu/
│  └─ mobile/
├─ resources-common/
├─ static/
│  └─ 프로젝트/
│     └─ 부동산 (oLWSmCRkmlw6kEpt)/
│        └─ 첫페이지 (AdKpMlw6KePt)/
│           ├─ 첫페이지 (AdKpMlw6KePt).html
│           ├─ style.css
│           ├─ style.js
│           ├─ menu-page.html
│           ├─ menu-page.css
│           ├─ menu-page.js
│           └─ lead-submit.js
├─ favicon.ico
├─ favicon.png
├─ robots.txt
└─ site.webmanifest
```

## 주요 파일 설명

- `index.html`
  - GitHub Pages 진입점
  - OG 메타데이터, 파비콘, iframe shell, 루트 단축키 보호 로직 담당

- `static/.../첫페이지 (AdKpMlw6KePt).html`
  - 실제 메인 랜딩페이지 마크업

- `static/.../style.css`
  - 메인/모바일 섹션 스타일
  - 슬라이더, 배너, 호버, reveal, 팝업 스타일 포함

- `static/.../style.js`
  - 메인 페이지 인터랙션 핵심 로직
  - 팝업, 히어로 슬라이더, 상담 스크롤, reveal, 유튜브 제어, 프리미엄 라이트박스, 돋보기, 콘텐츠 보호 처리

- `static/.../menu-page.js`
  - 상세페이지 탭 구성, 타입/인테리어 variant, 콘텐츠 렌더링 담당

- `static/.../lead-submit.js`
  - 상담 폼 검증 및 Google Apps Script Webhook 전송 담당

- `new-assets/`
  - 교체형 운영 자산 모음
  - 메인 배너, 팝업, 프로모션, 프리미엄, 모바일 전용 이미지 등 관리

## 로컬 실행 방법

### 1. 의존성 설치

```bash
npm install
```

### 2. 미리보기 실행

```bash
npm run preview
```

기본적으로 현재 저장소의 `static/` 결과물을 그대로 서빙하는 standalone 방식으로 동작합니다.

### 3. Temha 워크스페이스 기반 작업이 필요할 경우

```bash
npm run login
npm run pull
npm run serve
```

## 자산 교체 가이드

- 메인/공통 이미지: `new-assets/`
- 상세 메뉴 이미지: `new-assets/menu/`
- 모바일 전용 이미지: `new-assets/mobile/`

운영 방식상 이미지 파일명만 맞춰 교체하면 빠르게 리브랜딩할 수 있도록 구성되어 있습니다.

## 이 프로젝트에서 특히 신경 쓴 부분

- 분양 랜딩페이지 특유의 “과한 느낌”을 줄이고, 세련되고 고급스럽게 보이는 움직임으로 다듬은 점
- PC와 모바일을 같은 화면 축소판으로 처리하지 않고, 각각 다른 사용 흐름에 맞춰 구조를 조정한 점
- 상담신청으로 이어지는 CTA 동선을 여러 위치에서 자연스럽게 연결한 점
- 공유 링크, 파비콘, 메타 설명, 팝업, 하단 고정 상담 바까지 실제 운영 기준으로 마무리한 점

## 비고

이 저장소는 회룡역 파크뷰 완성본을 기준으로 정리된 프로젝트입니다.
이후 유사한 신규 프로젝트를 만들 때에는 이 저장소를 베이스 템플릿으로 복제한 뒤, `new-assets`와 메타데이터만 교체하는 방식으로 재사용할 수 있습니다.
