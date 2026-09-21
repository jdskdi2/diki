---
title: "Prompt Engineering"
created: 2026-09-21
updated: 2026-09-21
tags: [concept, ai, llm]
sources: [prompt-engineering-best-practices-2026.md, prompt-generation-openai-api.md]
aliases: ["프롬프트 엔지니어링"]
---

# Prompt Engineering

원하는 출력을 얻기 위해 지시를 구조화하는 craft. [[context-engineering]]의 building block이다.

## Core habits (2026 기준)

Explicit하고 specific하게, context와 motivation을 함께. one-shot 먼저, 부족하면 few-shot. 불확실하면 "모른다" 허용으로 hallucination 감소 ([[prompt-engineering-best-practices-2026]]).

## Advanced (필요할 때만 최소 조합)

- **Prefill**: assistant 첫 토큰 고정으로 형식 강제.
- **Chain of thought**: basic / guided / structured. Extended thinking과 상호보완.
- **Chaining**: `summarize→review→improve`처럼 단계 분리.
- **구기법 재평가**: XML tags·role prompting은 과도한 제약 금지, 극히 복잡할 때만.

## 자동 생성 관점

OpenAI [[meta-prompt]]는 best practice를 담은 상위 프롬프트로 system prompt를 생성한다: concise instruction → details → Steps → Output Format (필수) → Examples → Notes. Reasoning은 conclusion 앞에 ([[prompt-generation-openai-api]]).

## 관련 페이지

- [[context-engineering]] — 상위 개념
- [[meta-prompt]] — 자동 생성 패턴
- [[agent-skills]] — 세션 공통 지시의 이동처
