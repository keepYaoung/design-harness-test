# 업무: 이벤트 시트 (event taxonomy)

## 조건 체크
- [ ] 2회 이상 반복 — {버전마다 이벤트 추가·병합·소거}
- [ ] 품질이 들쭉날쭉 — {시트와 코드가 어긋남 · 목적 없는 이벤트 …}
- [ ] 파일로 남음 — `{앱 리포 이벤트 시트 경로}`

## 입력
- `{릴리즈 노트}` 기능 항목 = 키 스펙 (K-ID)
- 같은 버전 UX 실행의 `screens.md` (있으면)
- 현재 시트 · 앱 코드의 분석 호출 (`event-tools.mjs drift`)

## 산출물
1. `events.csv` — `rules.yaml` `events.columns` (정본, `event-tools.mjs apply` 로만 생성)
2. `events-{version}.md` — 목적 · 퍼널 · 질문 · 커버리지 (전달 문서)

## 게이트 → E1–E9 · ★A5 · ★B6 (harness/guides/events.md)
