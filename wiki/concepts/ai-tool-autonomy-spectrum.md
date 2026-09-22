---
title: "AI Tool Autonomy Spectrum"
created: 2026-09-22
updated: 2026-09-22
tags: [concept, ai, llm, productivity]
sources: [ai-tools-study.md]
aliases: ["자율성 스펙트럼", "AI 도구 7유형", "도구 분류 3축"]
---

# AI Tool Autonomy Spectrum

AI 도구를 가르는 세 가지 기준과 자율성 순 7유형 분류 ([[ai-tools-study]]).

## 3분류축

1. **어디서 말을 거는가** (interface) — 채팅창·터미널·에디터·브라우저·메신저. 명령 입력 자리.
2. **얼마나 맡기는가** (autonomy) — 매 턴 확인 ↔ 목표만 주고 끝까지 위임. 체감 차이를 가장 크게 만드는 축.
3. **실제로 어디서 일이 벌어지는가** (execution) — 로컬 셸·클라우드 VM·로그인된 웹. 명령이 실행되는 몸체.

## 7유형 (자율성 낮은 → 높은 순)

| # | 유형 | 대표 | 인터페이스 / 실행 몸체 |
|---|------|------|----------------------|
| 01 | Chat | ChatGPT·Claude·Gemini·Grok | 채팅창 / 없음 |
| 02 | 코딩 CLI | [[claude-code]]·Codex CLI | 터미널 / 로컬 셸 |
| 03 | 코딩 IDE | [[cursor]]·[[google-antigravity]] | 에디터 / 에디터+로컬 |
| 04 | 브라우저형 | [[aside]] | 브라우저 / 로그인된 웹 |
| 05 | 데스크톱 위임형 | [[claude-cowork]] | 데스크톱 앱 / 로컬 파일+앱 |
| 06 | 메신저 상주형 | [[openclaw]] | 메신저 / 상시 프로세스 |
| 07 | 팀원형 | [[grok-bot]] | 역할 부여 / 클라우드 VM |

핵심 대비: 01→02는 **실행 권한** 유무. 02→03은 로그 vs diff 시각 확인. 04는 API 없는 웹 직접 조작. 05는 사무 업무 포장. 06은 상시 대기+모델 교체, 보안 리스크 동반. 07은 전용 VM+직접 로그인+역할별 다중 실행.

## 관련 페이지

- [[ai-harness]] — 유형 차이가 곧 하네스 차이라는 상위 프레임
- [[ai-tools-study]] — 원천 소스
- [[claude-code]] · [[cursor]] · [[aside]] · [[claude-cowork]] · [[openclaw]] · [[grok-bot]] — 유형별 대표
- [[ai-coding-workflow]] — 코딩 유형(02·03)이 속한 workflow 토픽
