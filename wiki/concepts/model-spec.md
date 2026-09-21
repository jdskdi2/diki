---
title: "Model Spec"
created: 2026-09-21
updated: 2026-09-21
tags: [concept, ai, llm]
sources: [openai-model-spec-approach.md, claude-opus-5-system-prompts.md]
aliases: ["모델 스펙", "Instruction Hierarchy"]
---

# Model Spec

모델 행동의 intended behavior를 정의하는 공개 프레임워크. Interface이지 implementation이 아니다 — 대상은 모델이 아니라 사람이다.

## 핵심 구조 (OpenAI)

- **Instruction hierarchy**: OpenAI > 개발자 > 사용자. 충돌 시 higher authority 우선.
- **Hard rules vs defaults**: 하드 규칙은 변경불가 경계 (신체위해·불법·지시체계 훼손). 기본값은 조정 가능한 출발점 (guideline-level vs user-level).
- **해석 보조**: decision criteria (예: `control_side_effects`) + Compliant/Violation 사례 쌍.
- **3대 목표**: 점진적 배포 / 피해 방지 / 운영 지속성. 현실보다 0~3개월 앞선 목표치.
- **운영**: 투명성·협업 조정 언어·예측가능성·평가 카테고리. model-spec-evals 병행 공개.

## Anthropic 구현 예시와 비교

[[claude-opus-5-system-prompts]]는 같은 문제를 푼 production system prompt 실물이다: defaults to helping + concrete harm시에만 거절, safeguards routing (Fable→Opus, 5% 미만), evenhandedness, knowledge cutoff 2026-05말. Model Spec의 hard rules·hierarchy·refusal handling 구조와 대응된다.

## 관련 페이지

- [[openai]] — Spec 작성 주체
- [[anthropic]] — 비교 구현 주체
- [[agent-eval]] — spec eval 연결
- [[openai-model-spec-approach]] — 소스 요약
