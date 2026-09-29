# design.md — {서비스명}

> 값의 출처: {코드 토큰 파일 경로 · Figma 라이브러리}. 수치는 harness/rules.yaml `design_tokens` 로 옮겨 게이트가 검사한다.

## Overview
{서비스의 시각 성격 한 단락 — 무엇이 주인공이고 UI 는 어떤 태도인지}

## Colors
| Token | Value | 용도 |
|---|---|---|
| `{colors.bg}` | {#RRGGBB} | {화면 배경} |
| `{colors.text-primary}` | {#RRGGBB} | {본문·제목} |
| `{colors.action-primary}` | {#RRGGBB} | {주요 CTA} |
| `{colors.forbidden}` | {#RRGGBB} | {산출물에 나오면 안 되는 색 — 예: 개발용 리본} |

## Typography
| Token | Size | Weight | 용도 |
|---|---|---|---|
| `{typography.title}` | {N} | {굵기} | {화면 제목} |
| `{typography.body}` | {N} | {굵기} | {본문} |
| `{typography.caption}` | {N} | {굵기} | {보조} |

규칙: {크기 단계 수 · 쓰지 않을 값}

## Layout
- **간격 토큰**: {값 목록}
- **화면 여백**: {값}

## Shapes
| Token | Value | 용도 |
|---|---|---|
| `{rounded.sm}` | {N} | {…} |
| `{rounded.panel}` | {N} | {패널} |
| `{rounded.pill}` | {N–M} | {캡슐} |

## Components
- **{Primary CTA 이름}** — 높이 {N}, {모양 · 색 규칙}
- **{카드}** — {…}

## Voice & Copy
- 브랜드 표기: **{표기}** (옛 표기 "{옛 표기}" 사용 금지)
- {언어별 문장 부호 · 이모지 규칙}
- 현재 기능만 말한다 — 폐기된 기능 문구: {목록}

## Marketing Imagery (스토어·웹)
- {배경 · 헤드라인 위치 · 목업 규칙}
- 화면 속 데이터는 연출용 가짜 데이터 — 실제 이메일·기기명·개인정보 금지
- 상태바 {시각} · {그 밖의 캡처 규칙}
- 규격: {스토어별 픽셀 크기}

## Accessibility
- {대비 · 터치 영역 · 색만으로 상태 전달하지 않기}

## Do / Don't
- **Do** {…}
- **Don't** {…}
