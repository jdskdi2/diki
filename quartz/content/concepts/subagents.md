---
title: "Subagents"
created: 2026-09-21
updated: 2026-09-21
tags: [concept, ai, llm]
sources: [effective-context-engineering-agents.md, claude-code-session-management-1m-context.md, ai-native-sdlc-playbook.md]
aliases: ["서브에이전트"]
---

# Subagents

깨끗한 별도 window의 전문 agent에게 탐색을 위임하고, 최종 report만 parent로 회수하는 패턴. Main agent는 synthesis에 집중한다.

## 동작

- **효과**: 각 subagent가 수만 토큰 탐색 후 1,000-2,000 토큰 요약만 반환. Multi-agent research system에서 single-agent 대비 큰 개선 ([[effective-context-engineering-agents]]).
- **판단 테스트** ([[claude-code-session-management-1m-context]]): "will I need this tool output again, or just the conclusion?" 중간 output은 버리고 결론만 필요할 때 (코드베이스 탐색, spec 기반 검증, git diff 기반 문서화). `Agent` tool로 spawn, 명시 지시 ("Spin up a subagent to…")가 유효.
- **SDLC 활용** ([[ai-native-sdlc-playbook]]): `.claude/agents/verifier.md` 같은 scoped helper. Feedback loop (task 전체 반복 self-check) vs verifier subagent (완료 시점 fresh context 1회 최종 판정).

## 선택 기준

Parallel exploration이 유리한 task에 적합.

## 관련 페이지

- [[compaction]] — 대안 (계속 vs 위임)
- [[progressive-disclosure]] — 탐색 전략과 병용
- [[context-engineering]] — 상위 개념
