---
title: "Claude Code"
created: 2026-09-21
updated: 2026-09-22
tags: [entity, tool, ai, llm]
sources: [effective-context-engineering-agents.md, claude-code-session-management-1m-context.md, ai-native-sdlc-playbook.md, ai-tools-study.md]
aliases: ["클로드 코드"]
---

# Claude Code

Anthropic의 agentic coding 도구 (CLI·desktop·mobile). Context engineering 글들의 공통 예시이자 SDLC playbook의 실행 도구다.

## 특징

- **Hybrid retrieval 예시**: targeted queries + Bash head/tail로 전체 로드 회피 ([[effective-context-engineering-agents]]).
- **Compaction + memory 병용**: window 요약 + 최근 5개 파일 유지, CLAUDE.md + auto memory 두 memory 시스템 ([[context-engineering-memory-compaction-tool-clearing]]).
- **1M context + session 관리**: Continue / Rewind / Clear / Compact / Subagents 다섯 수단 ([[claude-code-session-management-1m-context]]).
- **SDLC 실행**: plan mode, CLAUDE.md, skills, hooks, parallel sessions, `claude -p` headless 실행 ([[ai-native-sdlc-playbook]]).
- **Token-maxxing 논란의 중심**: 2025년 Claude Code 확산이 token-maxxing 기폭제였다는 분석 ([[end-of-token-maxxing]]).
- **Harness 대비 예시**: 같은 Claude라도 Chat·Cowork와 prompt·tool·context·환경·loop가 다르다는 스펙트럼 글의 대표 사례. Chat과의 차이는 **실행 권한** (파일 변경·명령 실행) ([[ai-tools-study]]).

## 관련 페이지

- [[anthropic]] — 개발사
- [[claude-cowork]] — 같은 엔진, 다른 하네스 (사무 업무용)
- [[ai-harness]] — 하네스 프레임
- [[ai-tool-autonomy-spectrum]] — 코딩 CLI가 속한 분류
- [[compaction]] — 핵심 메커니즘
- [[subagents]] — 위임 패턴
- [[context-engineering-guide]] — 종합 토픽
