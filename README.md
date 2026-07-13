# 빌드그라운드 아레나 — 홈페이지

정적 사이트 (index.html 단일 파일 + assets 이미지). 빌드 도구 불필요.

## 배포 순서 (가비아 → 깃허브 → 넷리파이)

### 1. 깃허브
1. github.com 에서 새 저장소 생성 (예: `buildground-web`, Public)
2. 이 폴더의 파일 전부 업로드 (index.html, assets/, README.md)

### 2. 넷리파이
1. netlify.com 로그인 → "Add new site" → "Import an existing project" → GitHub 연결
2. 저장소 선택 → 빌드 설정은 전부 비워두고(Build command 없음, Publish directory `/`) Deploy
3. `xxxx.netlify.app` 주소로 즉시 배포됨

### 3. 가비아 도메인 연결
1. Netlify → Site settings → Domain management → Add custom domain → 구입한 도메인 입력
2. 가비아 → My가비아 → 도메인 관리 → DNS 설정:
   - A 레코드: `@` → `75.2.60.5` (Netlify 로드밸런서)
   - CNAME: `www` → `xxxx.netlify.app`
3. Netlify에서 HTTPS(Let's Encrypt) 자동 발급 확인 (몇 분 소요)

## 매주 운영 (수정은 딱 한 곳)

`index.html` 하단의 `DATA` 블록만 수정 → 깃허브에서 파일 편집·커밋하면 넷리파이가 자동 재배포.

- `week` / `missionTitle` / `missionDesc` : 이번 주 미션
- `leaderboard` : 리더보드 (이름·점수)
- `hallOfFame` : 자격증 취득자
- `videoIds` : 유튜브 쇼츠 영상 ID 3개 (주소의 `shorts/` 뒤 문자열)

이 네 가지가 갱신되는 한, 사이트는 '살아있는 기록실'로 작동한다.

## 구조

- HERO — 카테고리 라인 + 킥 카피
- TICKER — 시간·요금·장비·위치 (정보 카피)
- WEEKLY MISSION — 미션 + 포인트 규칙 + 리더보드
- THE MAGAZINE — 엄마의 마음 / 아빠의 마음 + 쇼츠 임베드
- LICENSE — 포인트→연수→자격증→대회 4단계 + 명예의 전당
- VISIT — 방문 정보 + '아이가 캐는 동안, 엄마의 시간'
