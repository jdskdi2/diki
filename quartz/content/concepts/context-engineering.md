---
title: "Context Engineering"
created: 2026-09-21
updated: 2026-09-21
tags: [concept, ai, llm]
sources: [effective-context-engineering-agents.md, context-engineering-memory-compaction-tool-clearing.md, context-engineering-claude-5-rules.md]
aliases: ["컨텍스트 엔지니어링"]
---

# Context Engineering

Inference 시점에 원하는 행동을 낳을 최적의 context state를 curate·maintain하는 전략 총칭. [[prompt-engineering]]의 상위 개념이자 자연스러운 확장이다.

## 정의

"find the smallest possible set of high-signal tokens that maximize the likelihood of some desired outcome." Context는 system prompts, tools, MCP, external data, message history를 아우르는 holistic state이며, 매 턴 최적화 대상이다 ([[effective-context-engineering-agents]]).

## 하위 기법

- **Just-in-time + [[progressive-disclosure]]**: 필요한 것만 runtime에 로드. Hybrid (CLAUDE.md upfront + glob/grep just-in-time)가 현실적.
- **[[compaction]]**: 전체 대화 요약 압축. 가장 가벼운 형태는 [[tool-result-clearing]].
- **[[agentic-memory]]**: window 밖 file 기반 지속 기록.
- **[[subagents]]**: 깨끗한 window의 전문 agent가 탐색 후 1-2K 요약만 반환.
- **Claude 5 전환** ([[context-engineering-claude-5-rules]]): rules → judgement, examples → interfaces, upfront → progressive disclosure, repeat → simple descriptions, manual memory → auto-memory, simple specs → rich references.

## [[prompt-engineering]]과의 관계

| | Prompt engineering | Context engineering |
|---|---|---|
| 대상 | 단일 지시문 | 전체 context state |
| 시점 | 작성 시 1회 | 매 inference마다 반복 |
| 작업 | discrete 작성 | iterative curation |

## 관련 페이지

- [[context-rot]] — 다루려는 문제
- [[context-engineering-guide]] — 실전 종합 토픽
- [[end-of-token-maxxing]] — "적게 쓰고 잘 쓰기"의 이론 근거
- [[rag]] — 이전 세대의 검색 방식과 비교
