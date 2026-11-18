# 앱 관리실 (app-hq)

Claude로 만든 앱·게임·도구 전체를 한곳에서 관리하는 페이지입니다.

- 실제로 쓰는 곳: https://claude.ai/artifact/136PLKwuEmMuERjrcoybpC (claude.ai 아티팩트)
- 이 저장소: 코드 백업과 버전 기록용

## 주요 기능

- **보드 / 전체 목록**: 진행 중 · 멈춤 · 아이디어 · 완성 · 삭제 예정, 끌어서 상태 변경
- **중복 확인**: 새로 만들기 전에 비슷한 앱이 있는지 검사
- **잠든 앱**: 진행 중인데 14일 넘게 손 안 댄 앱 알림
- **공통 규칙**: 분석버튼·시안 5개 먼저·포탈 등록·모바일 터치·GitHub 백업 적용 현황
- **정리함**: 지울 아티팩트 모아서 삭제 요청
- **하위 앱**: 다른 앱 아래로 묶기 (예: 스터디룸 ← English Daily, Japanese Daily)
- **GitHub·Netlify 주소, 7일 방문 수**
- **새 앱 자동 발견**: Claude가 훑은 발견 목록을 받아 기존 앱에 붙이거나 새 앱으로 배치
- **버전 표시**: 제목 옆 버전을 누르면 업데이트 기록 · 작동 원리 · 내부 흐름

## 구조

```
index.html      앱 전체 (HTML/CSS/JS 한 파일)
CHANGELOG.md    버전별 변경 기록
CLAUDE.md       작업 규칙
```

## 데이터

앱 목록은 코드 안이 아니라 claude.ai 아티팩트 저장소에 있습니다.

| 문서 | 내용 | 쓰는 쪽 |
|---|---|---|
| `manager/apps` | 앱 목록 | 페이지, Claude |
| `manager/rules` | 공통 규칙 | 페이지 |
| `manager/scan` | 발견 목록 (아티팩트·GitHub·Netlify) | Claude |
| `manager/seen` | 이미 본 것·되돌린 것·자동 배치 기록 | 페이지 |

그래서 이 `index.html`을 claude.ai 밖(로컬 파일, Netlify 등)에서 열면 저장소에 연결되지 않고
그 브라우저에만 임시로 저장됩니다. Netlify로 옮기려면 저장 공간을 따로 붙여야 합니다.

## 페이지가 쓰는 기능

- `db` — 위 문서 저장
- `mcp` (Netlify) — 🔄 새로고침 때 Netlify 프로젝트 목록과 7일 방문 수 조회
