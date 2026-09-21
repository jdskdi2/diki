---
title: "Agentic Memory"
created: 2026-09-21
updated: 2026-09-21
tags: [concept, ai, llm]
sources: [effective-context-engineering-agents.md, context-engineering-memory-compaction-tool-clearing.md]
aliases: ["Agent Memory", "Structured Note-taking"]
---

# Agentic Memory

Window 밖에 지속 메모를 유지했다가 나중에 pull-back하는 기법. Cross-session 지식이 필요할 때 유일한 해법이다.

## 동작

- **형태**: NOTES.md, to-do list, file-based memory (`/memories` 디렉토리, `memory_20250818` tool로 view/create/str_replace/insert/delete/rename).
- **사례**: Claude의 Pokémon 플레이 — 1,234 steps tally, maps·전략 유지 ([[effective-context-engineering-agents]]).
- **실측** ([[context-engineering-memory-compaction-tool-clearing]]): S1이 약 3K 비교 문서 작성 → S2는 memory 덕에 8 reads → 4 reads, peak 334K → 173K.
- **운영**: auto-injected protocol ("ALWAYS VIEW YOUR MEMORY…", assume-interruption mindset). Topical guidance, 조직화 지시, initializer-session, storage hygiene (사이즈 cap, path traversal 방어).
- **Claude 5 전환**: 수동 `#` 저장 → auto-memory (관련 memory 자동 저장·공유).

## 한계

In-session growth에는 무력 + read/write overhead. Fresh-start면 skip.

## 관련 페이지

- [[compaction]] — 세션 내 대안
- [[tool-result-clearing]] — 세션 내 경량 대안
- [[agent-skills]] — skills vs memory 구분 (procedural·stable vs auto-written)
