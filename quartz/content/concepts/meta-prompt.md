---
title: "Meta-Prompt"
created: 2026-09-21
updated: 2026-09-21
tags: [concept, ai, llm]
sources: [prompt-generation-openai-api.md]
aliases: ["메타프롬프트", "Meta-Schema"]
---

# Meta-Prompt

Task 설명을 입력받아 system prompt를 출력하도록 지시하는 상위 프롬프트. OpenAI Playground `Generate` 버튼의 원리다.

## 구조

Concise instruction → details → `# Steps [optional]` → `# Output Format` (필수) → `# Examples [optional]` → `# Notes [optional]`. 핵심 guidelines: Minimal Changes / Reasoning Before Conclusions (결론은 항상 마지막) / Preserve User Content / Constants 포함 / JSON bias.

## Meta-schema

유효한 JSON/function schema를 출력하도록 강제하는 자기-기술적 schema. `parameters`가 곧 schema이므로 function 생성에도 재사용. `strict=true` dilemma는 pseudo-meta-schema로 해결. 후처리 4단계: `additionalProperties=false` → 전 properties `required` → `json_schema` wrap → function wrap.

## 관련 페이지

- [[prompt-engineering]] — 근거 best practices
- [[prompt-generation-openai-api]] — 소스 요약
- [[agent-skills-eval-loop]] — 자동 생성 + eval 토픽
