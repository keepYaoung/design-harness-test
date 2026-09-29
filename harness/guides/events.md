# 이벤트 시트 (event taxonomy)

업무 정의: `docs/work-domains/events.md` · 형식: `rules.yaml` `events.columns`

| 단계 | 누가 | 양식 | 통과 게이트 | 실패 시 |
|---|---|---|---|---|
| P1 수집 | collector + `event-tools.mjs drift` | `templates/events/scope.md` | ART | P1 |
| P2 설계 | planner | `templates/events/changes.md` | E2 키 스펙 커버리지 | P1 |
| P3 제작 | `event-tools.mjs apply` (CSV) + maker (전달 문서) | `templates/events/delivery.md` | ART | — |
| 👤 | 사람 | `templates/common/approval.md` | APPROVAL | P2 |
| P4 대조 | judge (+ 분석 도구 MCP → `analytics-live.json`) | `templates/events/analytics-live.json` | ★A1 · E1 형식 · E3 목적 · E4 개인정보 · ★A5 사용자 원문 · ★B6 ★B 값 · E7 전달 문서 · E8 코드 대조 · E9 발생량(보고만) | 대부분 P3, ★B6 는 P2 |
| P5 파생 | publisher → `{app_repo}/docs/events/` · 노션 | `templates/common/publish.json` | ART | P5 |

## 설계 원칙
- **운영 중인 이름은 바꾸지 않는다** — 분석 도구 이력이 끊긴다. 합치거나 없앨 때는 `소거` + 새 이벤트
- **화면·버튼마다 이벤트를 만들지 않는다** — `screen_name` · `tab` · `source` 같은 enum 프로퍼티로
- **목적이 없으면 제안하지 않는다** — `purpose` 한 줄 (E3)
- **값은 보내지 않는다** — 사용자 원문은 길이·타입만 (★A5). 이메일·기기명 금지 (E4)

## 자주 걸리는 곳
- **E8** — 시트와 코드가 어긋나 있으면 첫 실행은 drift 를 전부 changes.md 로 정리하는 데서 시작한다
- **E1** — 한 번 소거한 이름은 다시 쓰지 않는다
- **★B6** — `probe_event` 에 `probe_guarded_values` 값을 새로 넣는 것은 ★B 에 걸리므로 사람 판단으로 넘긴다
- changes.md 표 안에서 enum 구분자는 `\|`
