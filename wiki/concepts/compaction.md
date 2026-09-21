---
title: "Compaction"
created: 2026-09-21
updated: 2026-09-21
tags: [concept, ai, llm]
sources: [effective-context-engineering-agents.md, context-engineering-memory-compaction-tool-clearing.md, claude-code-session-management-1m-context.md]
aliases: ["컴팩션", "Autocompact"]
---

# Compaction

Window limit 근처에서 대화를 high-fidelity summary로 압축한 뒤 새 window로 계속하는 기법. Lossy하지만 모든 growth 유형을 처리한다.

## 동작

- **API**: `compact_20260112` (trigger 기본 150K, knobs: trigger/instructions/pause_after_compaction).
- **실측** ([[context-engineering-memory-compaction-tool-clearing]]): turn 4에서 약 2.8K 요약으로 교체, peak 169K. High-level 사실 3/3 생존, obscure 수치 0/3 소실. Custom instructions로 quantitative figure 보존 가능 (단 default prompt 전체 대체이므로 `<summary>` 포함 full framing 필요).
- **Claude Code** ([[effective-context-engineering-agents]]): message history 요약 + 최근 5개 파일 유지. Recall 최대화부터 튜닝 후 precision 개선.
- **사용자 관점** ([[claude-code-session-management-1m-context]]): `/compact focus on X, drop Y`처럼 steer 가능. Bad autocompact 원인 = 방향 예측 불가 시 자동 요약. Compaction 시점이 rot으로 가장 least intelligent한 시점이므로 proactively 수동 compact 권장.

## 선택 기준

Extensive back-and-forth가 많은 task에 유리. 짧으면 skip.

## 관련 페이지

- [[tool-result-clearing]] — 더 가벼운 대안
- [[agentic-memory]] — 세션 초과용 대안
- [[context-rot]] — 해결 대상
- [[subagents]] — 결론만 필요할 때의 대안
