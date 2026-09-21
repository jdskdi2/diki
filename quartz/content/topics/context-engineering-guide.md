---
title: "Context Engineering Guide (종합)"
created: 2026-09-21
updated: 2026-09-21
tags: [topic, ai, llm]
sources: [effective-context-engineering-agents.md, context-engineering-memory-compaction-tool-clearing.md, context-engineering-claude-5-rules.md, claude-code-session-management-1m-context.md]
aliases: ["컨텍스트 엔지니어링 가이드"]
---

# Context Engineering Guide (종합)

5개 context engineering 소스를 종합한 실전 가이드. 이론 → 실측 → 신모델 규칙 → 사용자操作 순서로 읽으면 전체가 연결된다.

## 읽기 순서

1. **이론** ([[effective-context-engineering-agents]]): smallest high-signal set. Right altitude prompt, minimal tools, canonical examples, just-in-time retrieval, 3기법 (compaction / memory / subagents).
2. **실측** ([[context-engineering-memory-compaction-tool-clearing]]): 세 growth에 세 primitive. Baseline 335K → 조합 170K peak. Lossiness spectrum (clearing lossless — compaction controlled lossy — memory 판단의존). "Which of the three problems does my workload actually have?"
3. **신모델 규칙** ([[context-engineering-claude-5-rules]]): 80% 삭제 실험. Rules→judgement, examples→interfaces, upfront→progressive disclosure.
4. **사용자操作** ([[claude-code-session-management-1m-context]]): Continue / Rewind / Clear / Compact+hint / Subagents. New task = new session. Bad autocompact 방지용 proactive compact.

## 의사결정 표

| 증상 | 처방 |
|------|------|
| 대화 전체 비대화 | [[compaction]] |
| 재조회 가능한 tool 결과 누적 | [[tool-result-clearing]] |
| 세션 초과 지식 필요 | [[agentic-memory]] |
| 결론만 필요 | [[subagents]] |
| 잘못된 경로 | rewind 후 재프롬프트 |
| 새 task | `/clear` fresh start |

## 한 줄 원칙

"쓸 필요 없으면 쓰지 마라 + 적게 쓰고 잘 쓰기." 1M window도 stale이 같은 속도로 쌓이므로 lean 유지. 자세한 이론은 [[context-engineering]], 문제는 [[context-rot]] 참조.

## 관련 페이지

- [[context-engineering]] — 개념
- [[compaction]] / [[tool-result-clearing]] / [[agentic-memory]] / [[subagents]] — 기법
- [[prompt-engineering]] — building block
- [[token-maxxing]] — 비용 관점
