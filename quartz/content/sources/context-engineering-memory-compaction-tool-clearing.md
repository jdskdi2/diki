---
title: "Context Engineering — Memory, Compaction, and Tool Clearing"
created: 2026-09-21
updated: 2026-09-21
tags: [source, ai, llm]
sources: [Clippings/Context engineering memory, compaction, and tool clearing.md]
aliases: ["Claude Cookbook Context Engineering"]
---

# Context Engineering — Memory, Compaction, and Tool Clearing

Claude Developer Platform Cookbook 글. Long-running agent의 context 문제를 세 가지 growth 유형으로 나누고, 각각에 맞는 first-party primitive를 실측 비교한다.

원문: https://platform.claude.com/cookbook/tool-use-context-engineering-context-engineering-tools

## 핵심 주장

Context 문제는 하나가 아니라 셋이다: 대화 전체 비대화 → [[compaction]], 재조회 가능한 tool 결과 누적 → [[tool-result-clearing]], 세션 초과 지식 → [[agentic-memory]]. 8개 문서·약 329K 토큰 synthetic research agent로 효과·비용·조합을 측정했다.

## 주요 내용

- **세 기법 정의**: Compaction은 고충실도 요약으로 계속 (lossy하지만 모든 growth 처리). Clearing은 `tool_result` 블록만 placeholder로 교체하고 `tool_use` 기록은 유지 (inference 비용 없음). Memory는 window 밖 file 기반 지속 기록 (cross-session 유일 해법).
- **API 매핑**: `compact_20260112` (trigger 기본 150K) / `clear_tool_uses_20250919` (기본 trigger 100K, keep 3) / `memory_20250818` (client가 view/create/str_replace 등 구현).
- **Baseline**: 1M window에서 5턴 만에 peak 335K tokens, file-read가 96.3%. 200K 모델 관점에서는 turn 3 이후 hard-stop.
- **Compaction run**: Turn 4에서 약 2.8K 요약으로 교체, peak 169K. High-level 사실 3/3 생존, obscure 수치 0/3 소실. Custom instructions로 quantitative figure 보존 가능.
- **Clearing run**: 4회 firing, 매회 약 163K freed, peak 173K. Notes가 부실하면 synthesis 손실. `clear_at_least`로 충분히 지워야 cache invalidation을 상쇄.
- **Memory run**: S1이 약 3K 비교 문서 작성 → S2는 memory 덕에 8 reads에서 4 reads로, peak 334K에서 173K로 감소.
- **조합**: 세 기법 병용 시 peak 170K (baseline 335K 대비), final 13.7K. Lossiness spectrum: clearing (재호출 가능하면 lossless) — compaction (controlled lossy) — memory (저장 판단 의존).
- **교훈**: "쓸 필요 없는 경우"가 있다. Fresh-start면 memory skip, 짧으면 compaction skip, side-by-side 비교면 clearing skip. 1M window도 stale 결과가 같은 속도로 쌓이므로 lean 유지 필요.

## 관련 페이지

- [[context-engineering]] — 상위 개념
- [[compaction]] — 전체 요약 압축
- [[tool-result-clearing]] — 부분 surgical 삭제
- [[agentic-memory]] — 세션 외부 저장
- [[effective-context-engineering-agents]] — 이론 정의 글
- [[claude-code-session-management-1m-context]] — 사용자 관점의 세션 관리
- [[context-engineering-guide]] — 종합 토픽
