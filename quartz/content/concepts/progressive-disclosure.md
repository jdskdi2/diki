---
title: "Progressive Disclosure"
created: 2026-09-21
updated: 2026-09-21
tags: [concept, ai, llm]
sources: [effective-context-engineering-agents.md, context-engineering-claude-5-rules.md, agent-skill-eval.md]
aliases: ["점진적 공개"]
---

# Progressive Disclosure

필요한 정보를 필요 시점에 layer-by-layer로 로드하는 전략. Working memory는 최소로 유지하고 탐색을 통해 이해를 조립한다.

## 등장 맥락

- **Retrieval** ([[effective-context-engineering-agents]]): file paths·queries 같은 lightweight identifier를 tools로 runtime에 load.
- **Claude 5 전환** ([[context-engineering-claude-5-rules]]): CLAUDE.md·Skill·Tool을 중앙 저장소가 아닌 load-at-right-time 트리로. Tool도 deferred loading (ToolSearch).
- **Skill 구조** ([[agent-skill-eval]]): title+description → SKILL.md 본문 → 참조 파일 3겹. Description은 매 호출 100~200 token 비용이므로 얇게.
- **Warp 운영 팁** ([[warp-self-improving-agents]]): skill 본문 대신 resource files·scripts 참조.

## 원칙

"Do the simplest thing that works." Upfront에 다 넣지 말고, 탐색 실패 가능성과 속도의 trade-off를 감안해 hybrid로.

## 관련 페이지

- [[context-engineering]] — 상위 개념
- [[agent-skills]] — 적용처
- [[subagents]] — 탐색 위임과 병용
