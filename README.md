# mock-design-harness

반복되는 디자인·프로덕트 작업(화면 설계 · 스토어 스크린샷 · 릴리즈 QA 시트 · 이벤트 시트)을
Claude Code · Codex 같은 에이전트가 **같은 품질 기준으로** 수행하게 만드는 하네스 뼈대.

- 판정은 에이전트 의견이 아니라 **스크립트 종료 코드**로 한다 (`harness/scripts/verify.mjs`)
- 규칙 수치는 **파일 하나**(`harness/rules.yaml`)에만 둔다
- 사람 승인은 **파일 하나**(`runs/<slug>/approval.md`)로 받고, 입력이 바뀌면 자동으로 무효가 된다
- 에이전트는 파일을 직접 쓰지 않고 블록으로 돌려주며, 저장 범위는 hook 이 강제한다

이 저장소의 서비스 내용은 전부 `{자리표시}` 다. 자기 서비스로 채워서 쓴다.

## 구조

| 경로 | 역할 |
|---|---|
| `docs/PRD.md` · `docs/design.md` | 서비스 · 디자인 기준 문서 (자리표시) |
| `docs/story-service.md` · `docs/story-work.md` | 유저스토리 · ★ 어기면 안 되는 것 / 손작업 흐름 (인터뷰 R1 산출물) |
| `docs/work-domains*` | 하네스로 만들 반복 업무 정의 |
| `CLAUDE.md` · `AGENTS.md` | 하네스 입구 — Claude 전용 / 모든 에이전트 공용 |
| `harness/rules.yaml` | 규칙 SSOT — 파이프라인 · 게이트 36개 · 사전 · 토큰 (자리표시) |
| `harness/scripts/` | 판정 `verify.mjs` · 저장 `save-blocks.mjs` · QA/이벤트 도구 · Figma 지문 `figma-export.figma.js` · 점수 `score.mjs` · guard hook 3개 · OCR `ocr.swift` |
| `harness/templates/` · `harness/guides/` | 단계별 산출물 양식 · 업무별 가이드 |
| `harness/tests/` | 게이트별 통과·실패 테스트 — 중립 예시 규칙 `tests/fixtures/rules.test.yaml` 로 돈다 |
| `.claude/` | 에이전트 5개(collector · planner · maker · publisher · judge) · `run-harness` 스킬 · hook 설정 |

## 시작하기

```bash
cd harness && npm ci && cd ..
node --test harness/tests/*.test.mjs   # 게이트 동작 확인 (예시 규칙)
node harness/scripts/score.mjs         # 하네스 점수 (100점)
```

1. `docs/` 의 `{…}` 를 자기 서비스로 채운다 — PRD → story-service(★A·★B) → story-work(손작업 흐름)
2. `harness/rules.yaml` 의 `{…}` 를 셀 수 있는 값으로 채우고, `sources` 에 출처(인터뷰 · 문서 · 임의)를 적는다
3. `harness/defaults.yaml` 의 `app_repo` 를 앱 리포 경로로
4. Claude Code 에서 "1.2.0 QA 시트 하네스 돌려줘" 처럼 말하면 `run-harness` 스킬이 단계를 돌린다

## 필요 환경
- Node 20+ · macOS (스크린샷 OCR 은 Vision 프레임워크 — 다른 OS 에서는 S4·S6·S7·S9 OCR 부분만 빠진다)
- 선택: Figma MCP (ux U7 지문 대조) · UI Bowl · Mobbin MCP (레퍼런스) · 노션 MCP (파생본 동기화) · 분석 도구 MCP (events E9)
