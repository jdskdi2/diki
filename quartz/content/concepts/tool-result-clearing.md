---
title: "Tool Result Clearing"
created: 2026-09-21
updated: 2026-09-21
tags: [concept, ai, llm]
sources: [context-engineering-memory-compaction-tool-clearing.md]
aliases: ["Context Editing", "Clear Tool Uses"]
---

# Tool Result Clearing

`tool_use` 기록은 남기고 `tool_result` payload만 placeholder로 교체하는 sub-transcript op. 가장 가벼운 compaction이다.

## 동작

- **API**: `clear_tool_uses_20250919` (beta `context-management-2025-06-27`, 기본 trigger 100K, keep 3, knobs: trigger/keep/clear_at_least/exclude_tools/clear_tool_inputs). Inference 비용 없음.
- **실측**: 3 results keep=1 데모에서 129K → 43K (67%↓). 본 run에서는 4회 firing, 매회 약 163K freed.
- **주의**: Notes가 부실하면 synthesis 손실. 재조회(re-read) 비용은 tool 성격에 의존. Cache invalidation 상쇄 위해 `clear_at_least`로 충분히 지울 것. `applied_edits`로 효과 관측.
- **병용**: clearing + memory 병용 시 `exclude_tools: ["memory"]`로 memory ops 소실 방지.
- **Lossiness**: 재호출 가능하면 lossless. Side-by-side 비교가 필요하면 skip (원문 병렬 비교 불가).

## 관련 페이지

- [[compaction]] — 전체 요약 대안
- [[agentic-memory]] — 세션 외부 대안
- [[context-engineering-guide]] — 조합 전략
