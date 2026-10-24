# Video Team Sunday Checklist — 배포 가이드

모바일용 정적 웹앱입니다. 서버나 빌드 과정 없이 이 폴더를 그대로 올리면 됩니다.
홈 화면에 추가하면 앱처럼 열리고, 오프라인에서도 동작합니다 (PWA).

## 파일
- `index.html` — 앱 전체 (체크리스트 데이터 포함)
- `manifest.webmanifest`, `sw.js`, `icon*.png`, `icon.svg` — 홈 화면 설치·오프라인용

## 체크리스트 수정
`index.html`에서 `const ROLES = [` 를 찾아 항목을 고치면 됩니다.
- 항목 하나: `{ id:"고유-id", tag:"라벨", text:"할 일", note:"보조 설명(선택)" }`
- `id`는 바꾸지 마세요 (체크 저장에 쓰입니다). 새 항목은 새 id를 주세요.
- 메뉴얼(2단계): 항목에 `manual:{ summary:"…", steps:["…","…"], tips:["…"] }` 를 추가하면 📖 버튼에 표시됩니다.
- 수정 후 `sw.js`의 `videoland-v1` 을 `v2`로 올리면 캐시가 갱신됩니다.

## 배포 방법 (택1)

### A. Netlify Drop (가장 쉬움, 2분)
1. https://app.netlify.com/drop 접속 (무료 계정)
2. 이 폴더(`deploy`)를 통째로 끌어다 놓기
3. 생성된 주소를 봉사자에게 공유. Site settings에서 이름 변경 가능 (예: villagevideoland.netlify.app)

### B. GitHub Pages
1. GitHub에서 새 저장소 생성 (예: `videoland-checklist`)
2. 이 폴더의 파일을 저장소 루트에 업로드
3. Settings → Pages → Branch: `main` / `(root)` → Save
4. 주소: `https://<계정>.github.io/videoland-checklist/`

### C. 교회 도메인
`checklist.교회도메인` 같은 서브도메인을 Netlify/GitHub Pages에 연결하면 됩니다 (HTTPS 필수 — 오프라인 기능에 필요).

## 동작 방식
- 체크 상태는 각 휴대폰에 저장되고, 날짜가 바뀌면 자동으로 초기화됩니다.
- 역할별 바로가기 링크: `#setup`, `#camera`, `#switcher`, `#teardown` (예: `…/index.html#camera`)
