---
title: "Agent Eval"
created: 2026-09-21
updated: 2026-09-21
tags: [concept, ai, llm]
sources: [agent-skill-eval.md, warp-self-improving-agents.md, ai-native-sdlc-playbook.md]
aliases: ["에이전트 이밸", "Skill Eval"]
---

# Agent Eval

Skill·에이전트 변경이 성능을 올리는지 자동 확인하는 테스트 모음. Non-deterministic한 agent를 다루는 핵심 안전장치다.

## 왜 필요한가

Skill 미발동 vs skill 오류 vs 모델 한계는 실행 없이는 구분 불가. 특히 고객용 에이전트 (model-invoked만 존재)에서는 eval이 필수다 ([[agent-skill-eval]]).

## 구성 요소

- **최소 시작**: JSON test cases (`{prompt, language, should_trigger, expected_checks}`) + Python harness (실행 + regex assert). 10~20개로 시작 (happy 5 + negative 5), 케이스당 5~6회 반복, 격리 clean workspace.
- **채점**: regex assert (값쌈) → LLM as judge + rubric (복잡한 경우만) → trace (`trace_contains: "read SKILL.md"`).
- **실험**: ablation (skill on/off 비교), 다중 harness (Cursor/Antigravity/Codex).
- **운영**: skill diff → eval 자동 실행·병합 차단 (CI/regression). Preference skill은 regression 보호.
- **효과**: SkillBench 1.1 기준 skill 평균 약 15% 향상. 사람 작성 skill이 최고, AI 생성은 하락 가능.
- **SDLC 연결** ([[ai-native-sdlc-playbook]]): continuous evals in CI (20-50 real tasks, pass-rate로 merge gate, incident마다 영구 eval 추가). Model-spec-evals도 같은 계열 ([[openai-model-spec-approach]]).

## 격언

"이밸이 스킬보다 오래 산다." 스킬은 일회용 반창고, 진짜 자산은 검증이다.

## 관련 페이지

- [[agent-skills]] — 검증 대상
- [[agent-skills-eval-loop]] — 종합 토픽
- [[ai-native-sdlc]] — CI eval 운영처
