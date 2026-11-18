# 작업 규칙 — 앱 관리실

- 원본은 이 저장소의 `index.html`. 실제 사용은 claude.ai 아티팩트
  (slug `004ace63-0401-44e3-aa5b-cf7aec92d539`).
- 고칠 때마다:
  1. `index.html`의 `VERSION`을 한 단계 올리고 `CHANGELOG` 배열에 기록 추가
  2. 같은 내용을 `CHANGELOG.md`에도 추가
  3. 아티팩트에 배포하고, 이 저장소에도 커밋·푸시 (둘이 어긋나지 않게)
- 앱 데이터(`manager/apps` 등)는 아티팩트 저장소에 있음. 코드를 바꿔도 데이터는 그대로.
  데이터를 고칠 땐 먼저 읽고 `ifVersion`으로 쓰기.
- "앱 관리실 스캔해줘" 요청이 오면: 아티팩트 목록·GitHub 저장소(2026-10-01 이후)·Netlify 프로젝트를
  모아 `manager/scan`에만 쓴다. 배치는 페이지가 한다. `apps`·`rules`·`seen`은 건드리지 않는다.
- 배포 전 `node --check`로 스크립트 문법 확인.
