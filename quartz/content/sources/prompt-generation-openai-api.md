---
title: "Prompt Generation (OpenAI API)"
created: 2026-09-21
updated: 2026-09-21
tags: [source, ai, llm]
sources: [Clippings/Prompt generation  OpenAI API.md]
aliases: ["OpenAI Meta-Prompt"]
---

# Prompt Generation (OpenAI API)

OpenAI Playground의 `Generate` 버튼이 task description만으로 prompt / function / schema를 자동 생성하는 원리를 공개한 공식 가이드. Prompt는 `meta-prompt`로, Schema는 Structured Outputs용 `meta-schema` + 후처리로 생성된다.

원문: https://developers.openai.com/api/docs/guides/prompt-generation

## 핵심 내용

- **2-track**: Prompts = meta-prompts, Schemas/Functions = meta-schemas. 향후 `DSPy`, Gradient Descent 기법 통합 가능성 언급.
- **Meta-prompt 구조**: concise instruction → details → `# Steps [optional]` → `# Output Format` (필수) → `# Examples [optional]` → `# Notes [optional]`. 추가 코멘트 금지.
- **Guidelines**: Minimal Changes / Reasoning Before Conclusions (conclusion은 항상 마지막, 결론-first 예시는 순서 REVERSE) / Preserve User Content / Constants 포함 (prompt injection에 안전) / markdown 사용하되 코드블록 금지 / structured task는 JSON bias, JSON을 코드블록으로 감싸지 말 것.
- **Prompt edits용 변형**: 응답 맨 앞에 `<reasoning>` 태그로 Simple Change / Reasoning / Ordering / Structure / Examples / Complexity(1-5) / Specificity(1-5) / Prioritization / Conclusion(30 words) 분석 후 파싱해 제거.
- **Schemas**: `parameters`가 곧 schema이므로 function 생성에도 동일 meta-schema 재사용. `strict=true` dilemma — 공식 JSON Schema meta-schema가 strict 미지원 기능에 의존하므로, strict 밖에서 strict-준수 schema만 기술하는 pseudo-meta-schema로 해결.
- **Output cleaning 4단계**: 모든 object `additionalProperties=false` → 모든 properties `required` → `json_schema` object로 wrap → function은 `function` object로 wrap.
- **예시 코드**: `gpt-5.6` (prompt 생성), `gpt-5.6-terra` (schema 생성). Few-shot 포함: `math_reasoning`, `linked_list`, `ui`.

## 관련 페이지

- [[meta-prompt]] — 핵심 개념
- [[prompt-engineering]] — 근거가 되는 best practices
- [[prompt-engineering-best-practices-2026]] — Anthropic 관점의 동반 소스
- [[openai]] — 발행 주체
- [[agent-skills-eval-loop]] — 자동 생성 + eval 종합 토픽
