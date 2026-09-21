---
title: "Agent Skills Eval Loop (종합)"
created: 2026-09-21
updated: 2026-09-21
tags: [topic, ai, llm]
sources: [warp-self-improving-agents.md, agent-skill-eval.md, prompt-generation-openai-api.md, ai-native-sdlc-playbook.md]
aliases: ["스킬 이밸 루프"]
---

# Agent Skills Eval Loop (종합)

Skill 작성 → eval 검증 → improver 갱신 → CI 회귀방지의 closed loop. 4개 소스가 각 조각을 맡는다.

## 루프 조립

1. **작성** ([[agent-skills]]): principles not rules, 얇게 + 참조 분리, directive. [[meta-prompt]]로 초안 자동 생성 가능 ([[prompt-generation-openai-api]]).
2. **검증** ([[agent-eval]]): JSON cases + harness + regex assert로 시작. Happy 5 + negative 5, 케이스당 5~6회, ablation on/off. SkillBench 평균 +15%, AI 생성 skill은 하락 가능 — 검증 없이 배포 금지.
3. **개선** ([[warp-self-improving-agents]]): base skill → human feedback (what+why, 일하는 곳에서 low friction) → improver skill (scheduled) → 작은 PR → human approve → 다음 run 상속.
4. **회귀방지** ([[ai-native-sdlc-playbook]]): skill diff → eval 자동 실행·병합 차단. Preference skill은 regression 보호. Continuous evals (20-50 tasks)로 pass-rate gate.

## 핵심 구분

- Skills vs memory: procedural·stable·deliberate vs auto-written·계속 변함.
- 쓰는 에이전트 (인간 안전망) vs 만드는 에이전트 (model-invoked만, eval 필수).
- Capability skill (한시적, 폐기 판단) vs preference skill (오래감).

## 격언

"이밸이 스킬보다 오래 산다." 진짜 자산은 검증이다.

## 관련 페이지

- [[agent-skills]] / [[agent-eval]] — 개념 쌍
- [[meta-prompt]] — 자동 생성
- [[warp]] / [[philipp-schmid]] — 주체
