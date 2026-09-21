---
title: "Claude Opus 5 System Prompts"
created: 2026-09-21
updated: 2026-09-21
tags: [source, ai, llm]
sources: [Clippings/Claude Opus 5 system prompts.md]
aliases: ["Opus 5 System Prompt"]
---

# Claude Opus 5 System Prompts

Anthropic이 공개한 Claude Opus 5의 core system prompt 전문. 제품 정보, 안전·거절 정책, 말투, wellbeing, 중립성, knowledge cutoff를 코드화한 문서다.

원문: https://platform.claude.com/docs/en/release-notes/system-prompts/claude-opus-5

## 핵심 내용

- **제품 라인업**: `claude-fable-5`, `claude-opus-5`, `claude-sonnet-5`, `claude-haiku-4-5-20251001`. Mythos tier (Mythos Preview / Mythos 5 / Fable 5) 도입. Fable 5는 Mythos와 동일 기반 + biology·cybersecurity·LLM R&D 추가 안전조치.
- **Safeguards routing**: Fable 5 질의 중 일부는 Opus 5가 대신 응답. 평균 5% 미만 sessions에서 trigger, 보수적 튜닝으로 false positive 존재.
- **Default stance**: 돕는 것이 기본. 구체적·심각한 위해(concrete, specific risk of serious harm) 있을 때만 거절. Edgy/hypothetical/playful은 거절 사유 아님.
- **Refusal handling**: 무기(CBRN 포함), malware/exploit/spoof/ransomware는 목적 불문 거절. Child safety 최우선.
- **Tone**: warm tone, 간결·집중. Lists는 요청받거나 복잡할 때만.
- **Wellbeing**: 위기 시 task 완성보다 wellbeing 우선. 자살·자해 수단 구체적 명명 금지, pain-based coping 제안 금지.
- **Evenhandedness**: 정치·윤리·정책 설득 요청은 defenders의 best case framing + 반대 관점 병기.
- **Knowledge cutoff**: 2026-05말. 이후 사건은 모른다고 말하고 web search 권장.

## [[model-spec]]과의 비교 관점

OpenAI [[model-spec]]이 interface로서의 행동 명세라면, 이 문서는 실제 production system prompt의 구현 예시로 읽을 수 있다. Instruction hierarchy, hard rules vs defaults, refusal handling 구조가 대응된다.

## 관련 페이지

- [[anthropic]] — 배포 주체
- [[model-spec]] — OpenAI의 행동 명세 프레임워크
- [[openai-model-spec-approach]] — 비교 대상 소스
- [[claude-code]] — 언급된 agentic coding tool
