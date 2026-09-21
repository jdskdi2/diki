---
title: "Context Rot"
created: 2026-09-21
updated: 2026-09-21
tags: [concept, ai, llm]
sources: [effective-context-engineering-agents.md, claude-code-session-management-1m-context.md]
aliases: ["컨텍스트 썩음", "Attention Budget"]
---

# Context Rot

Window 토큰 증가에 따라 recall 능력과 작업 정밀도가 감소하는 현상. Context engineering이 다루려는 핵심 문제다.

## 원인

- Transformer n² pairwise attention 부담.
- 학습 분포상 짧은 sequence 편향.
- Position encoding interpolation 한계.
- 오래된 irrelevant 내용이 현재 task를 방해 (attention 분산).

Hard cliff는 아니지만 gentle degradation이 아닌 정밀도 저하가 발생하며, 인간 working memory에 비유되는 유한한 attention budget을 갖는다 ([[effective-context-engineering-agents]]). Chroma research (`research.trychroma.com/context-rot`)가 개념 출처로 인용된다.

## 대응

1M window에서도 rot은 여전하므로 lean 유지 필요: [[compaction]], [[tool-result-clearing]], [[agentic-memory]], [[subagents]], new task = new session (`/clear`).

## 관련 페이지

- [[context-engineering]] — 대응 discipline
- [[compaction]] — 대응 기법
- [[token-maxxing]] — "많이 넣기"가 왜 해로운지의 비용 관점
