---
title: "Effective Context Engineering for AI Agents"
created: 2026-09-21
updated: 2026-09-21
tags: [source, ai, llm]
sources: [Clippings/Effective context engineering for AI agents.md]
aliases: ["Anthropic Context Engineering"]
---

# Effective Context Engineering for AI Agents

Anthropic Applied AI팀의 **context engineering** 정의 글. Prompt engineering의 확장으로, 매 inference 시점의 전체 context state를 최적화하는 discipline을 제시한다.

원문: https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents

## 핵심 주장

원하는 결과를 낼 가능성을 최대화하는 `smallest possible set of high-signal tokens`을 찾는 것이 목표. Context는 diminishing returns를 갖는 finite resource이며, long-horizon task에는 compaction, structured note-taking, sub-agent가 필요하다.

## 주요 내용

- **Prompt vs Context**: Prompt는 단발성 지시문 작성, Context는 매 턴 curation하는 반복 작업. Agent loop가 생성하는 데이터를 cyclically refine해야 함.
- **왜 중요한가**: Token 증가 → recall 정확도 감소 ([[context-rot]]). Transformer n² attention, 짧은 sequence 편향, position encoding 한계 때문.
- **System prompt — right altitude**: Brittle한 if-else와 vague한 지침 사이의 Goldilocks zone. Minimal하게 시작해 failure mode 기반으로 추가. XML 태깅·Markdown 헤더로 섹션 구분.
- **Tools — minimal·self-contained**: Token-efficient한 반환, 기능 overlap 최소화. Bloated tool set이 대표 failure mode.
- **Examples**: Edge case 나열 금지. Diverse하고 canonical한 few-shot이 "pictures worth a thousand words".
- **Retrieval — just-in-time + [[progressive-disclosure]]**: Embedding 기반 사전 검색에서, file path·query 같은 lightweight identifier를 runtime에 로드하는 방식으로 이동. Claude Code 예: targeted queries + Bash head/tail. Hybrid(CLAUDE.md upfront + glob/grep just-in-time)가 현실적.
- **Long-horizon 3기법**: [[compaction]] / [[agentic-memory]] (structured note-taking) / [[subagents]]. Task별 선택 기준: back-and-forth가 많으면 compaction, 반복 milestone이면 note-taking, 병렬 탐색이면 multi-agent.

## 관련 페이지

- [[context-engineering]] — 핵심 개념 정리
- [[context-rot]] — context 증가에 따른 성능 저하
- [[compaction]] — 요약 압축 기법
- [[agentic-memory]] — 구조적 메모와 memory tool
- [[subagents]] — sub-agent 아키텍처
- [[progressive-disclosure]] — 점진적 공개 전략
- [[context-engineering-memory-compaction-tool-clearing]] — 세 기법의 실측 비교
- [[context-engineering-claude-5-rules]] — Claude 5 세대의 규칙 전환
- [[claude-code]] — 예시로 등장하는 agentic coding 도구
