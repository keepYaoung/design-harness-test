# 스토어 스크린샷

손작업 흐름: `docs/story-work.md`

| 단계 | 누가 | 양식 | 통과 게이트 | 실패 시 |
|---|---|---|---|---|
| P1 수집 | collector (릴리즈 노트) | `templates/screenshots/scope.md` | ART | P1 |
| P2 설계 | planner | `templates/screenshots/copy.csv` | ART | P1 |
| P3 제작 | maker — 기기 조작 도구로 캡처 `raw/` · 템플릿 렌더 `out/` | — | ART | — |
| 👤 | 사람 | `templates/common/approval.md` | APPROVAL | P2 |
| P4 대조 | judge (+ macOS Vision OCR) | — | ★A2 신뢰 신호 · ★B1 · S1 규격 · S2 언어 · S3 줄 수 · S4 폐기 기능 문구 · S5 em dash·이모지 · S6 개인정보 · S7 금지 색·시각 · S8 표기 · S9 언어 혼입 | 카피는 P2, 캡처·렌더는 P3 |
| P5 파생 | publisher → 앱 리포 (`publish_to_app_repo`) | `templates/common/publish.json` | ART | P5 |

## 자주 걸리는 곳
- **S4** — 캡처 화면 속 폐기된 기능 문구. 카피만 고쳐도 캡처 안에 남는다 → OCR 로 잡는다
- **S6** — 캡처 속 실제 기기명·이메일. 데모 데이터로 다시 캡처
- **S7** — 잠금화면·알림 캡처의 시각이 `status_time` 과 다름 · 개발용 표시 색(`forbidden_colors`)
- **S9** — 다른 언어 세트 캡처에 앱 UI 언어가 남음 (앱 언어를 세트 언어로 바꾸고 캡처)
- **S3** — 가장 긴 언어 기준으로 줄 수 확인. `headline_lines` 는 렌더러가 채운다
- 실제로 틀렸던 캡처가 있으면 `harness/tests/fixtures/` 에 넣고 실패해야 하는 게이트를 회귀 테스트로 고정한다
