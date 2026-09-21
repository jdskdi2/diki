---
title: "Prompt Engineering Best Practices for 2026"
created: 2026-09-21
updated: 2026-09-21
tags: [source, ai, llm]
sources: [Clippings/Prompt engineering best practices for 2026.md]
aliases: ["Prompt Best Practices 2026"]
---

# Prompt Engineering Best Practices for 2026

Anthropic의 2026년 기준 prompt 가이드. Claude 4.x·5세대에서는 무거운 scaffolding보다 explicit·specific·context-rich한 curation이 효과적이며, core habits로 대부분 해결하고 복잡할 때만 advanced 기법을 최소 조합하라고 권한다.

원문: https://claude.com/blog/best-practices-for-prompt-engineering (2025-11-10)

## Core habits

- **Be explicit and clear**: 추론 기대 금지, action verbs로 시작, preamble 생략.
- **Provide context and motivation**: why를 주면 관련 결정까지 일반화. 목적·청중·사용처 명시.
- **Be specific**: constraints + context + output structure + requirements.
- **Use examples**: one-shot 먼저, 부족하면 few-shot. Claude 4.x는 example 세부사항에 민감하므로 원치 않는 패턴 최소화.
- **Permission for uncertainty**: `If data is insufficient... say so`로 hallucination 감소.

## Advanced (필요할 때만)

- **Prefill**: assistant 응답 첫 토큰 고정으로 JSON/XML·preamble skip·voice 제어.
- **Chain of thought**: basic / guided / structured (`<thinking>` vs `<email>` 분리). Extended thinking이 있으면 우선, transparent reasoning 필요 시 수동 CoT.
- **Output format + chaining**: 하지 말라는 것 대신 하라는 것. Chaining은 `summarize→review→improve`처럼 단계 분리.
- **구기법 재평가**: XML tags는 극히 복잡할 때만, role prompting은 과도한 제약 금지.

## 운영 팁

- Troubleshooting: generic → specificity, format → examples/prefill, complex → chaining, hallucination → I don't know 허용.
- Long content는 token overhead 의식 + 핵심은 앞/뒤 배치 + 큰 task는 focused subtasks 분할.
- 세션 공통 지시는 `CLAUDE.md`·skills·hooks·rules·[[subagents]]로 이동.
- "The best prompt isn't the longest. Start simple and add complexity only when needed."

## 관련 페이지

- [[prompt-engineering]] — 개념 정리
- [[context-engineering]] — 상위 개념 (prompting은 building block)
- [[meta-prompt]] — OpenAI의 자동 생성 관점
- [[agent-skills]] — 세션 공통 지시의 이동처
- [[prompt-generation-openai-api]] — 동반 소스
