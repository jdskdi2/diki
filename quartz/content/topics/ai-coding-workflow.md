---
title: "AI Coding Workflow (종합)"
created: 2026-09-21
updated: 2026-09-21
tags: [topic, ai, llm]
sources: [ai-native-sdlc-playbook.md, agentic-ai-scientific-computing.md, end-of-token-maxxing.md, claude-code-session-management-1m-context.md]
aliases: ["AI 코딩 워크플로우"]
---

# AI Coding Workflow (종합)

AI-native 개발의 engineering → 검증 → 비용 3축을 종합한다. "빨라진 build"가 남긴 새 병목과 측정법을 정리한다.

## 3축 요약

- **Engineering** ([[ai-native-sdlc]]): artifact chain (`intent → spec → plan → diff+tests → findings → incident → intent`)으로 loop를 돌린다. Human은 gate의 판단·승인에 집중. Plan mode, CLAUDE.md ≤1페이지, skills, hooks, parallel sessions가 실행 수단.
- **검증** ([[agentic-ai-scientific-computing]]): 8건 현장 보고. Engineering bottleneck↓ → 검증이 새 병목. 연구자 역할 = 정의·검증·조율. 작은 단위 + 중간 벤치마크, 외부 측정 기준 (exact match·ground truth) 필수. Last-mile에 최다 노력.
- **비용·측정** ([[token-maxxing]]): token ≠ 산출물·정직도, token = 공급자 매출. "그 한도로 무엇을 바꿨는지" outcome으로 평가. 토성비 관점 + [[context-engineering]] 최소 투입.

## 세션 운영 연결

[[claude-code-session-management-1m-context]]의 5수단 (Continue/Rewind/Clear/Compact/Subagents)이 일일 작업 리듬에 대응한다. New task = new session, 결론만 필요하면 subagent, 비대하면 proactive compact.

## 유지관리 과제

구현비용↓ → 유사 재구현↑ → upstream 반영 vs fork ownership 명확화. 오늘이 재구현이 내일의 방치 코드가 되지 않으려면 maintainer와 조기 협업.

## 관련 페이지

- [[ai-native-sdlc]] — 개념
- [[agent-eval]] — continuous evals
- [[context-engineering-guide]] — context 처방
- [[token-maxxing]] — 비용 비판
