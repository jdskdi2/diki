---
title: "모델 사양에 대한 접근 방식 (OpenAI)"
created: 2026-09-21
updated: 2026-09-21
tags: [source, ai, llm]
sources: [Clippings/모델 사양에 대한 접근 방식.md]
aliases: ["OpenAI Model Spec", "Model Spec Approach"]
---

# 모델 사양에 대한 접근 방식 (OpenAI)

OpenAI Model Spec은 모델 행동의 intended behavior를 정의하는 공개 프레임워크(public framework / interface, not implementation)다. 안전성·사용자 자유·책임성의 상충을 명시적으로 균형 맞추는 것을 목표로 한다.

원문: https://openai.com/ko-KR/index/our-approach-to-the-model-spec/ (2026-03-25), Spec: https://model-spec.openai.com/

## 핵심 내용

- **Interface, not implementation**: 대상은 모델이 아니라 사람 (직원·사용자·개발자·연구자·정책입안자). 내부 토큰 형식·학습 방식과 분리.
- **3대 목표**: 점진적 배포 (incremental deployment) / 심각한 피해 방지 / OpenAI 운영 지속성 유지.
- **[[model-spec]]의 핵심 — instruction hierarchy**: OpenAI > 개발자 > 사용자. 충돌 시 higher authority 우선. 각 정책·지시에 levels of authority 부여.
- **Hard rules vs defaults**: 하드 규칙은 변경불가 경계 (신체위해·불법·지시체계 훼손·`stay_in_bounds`·`chatgpt_u18`). 기본값은 조정 가능한 출발점 — guideline-level (어조·스타일) vs user-level (진실성·객관성, 명시적 지시시에만 변경).
- **해석 보조**: decision criteria (예: `control_side_effects` — 되돌릴 수 없는 행동 최소화) + 구체적 사례 (Compliant/Violation 쌍).
- **상세 Spec이 필요한 4이유**: 투명성·책임성 / 내부 협업용 조정 언어 / 지능·컨텍스트 한계 보완과 예측가능성 / 평가용 공개 카테고리.
- **운영**: 현실보다 0~3개월 앞선 목표치. 수십명 참여 개방형 프로세스. 함께 공개된 model-spec-evals (scenario-based evals). 좋은 Spec 기준 = 명확성·실질적 규칙·핵심 사례·견고성·일관성.

## 관련 페이지

- [[model-spec]] — 개념 정리
- [[openai]] — 작성 주체
- [[claude-opus-5-system-prompts]] — Anthropic 구현 예시와 비교
- [[agent-eval]] — model-spec-evals 연결
