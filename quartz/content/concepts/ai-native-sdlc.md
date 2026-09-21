---
title: "AI-Native SDLC"
created: 2026-09-21
updated: 2026-09-21
tags: [concept, ai, llm]
sources: [ai-native-sdlc-playbook.md, agentic-ai-scientific-computing.md]
aliases: ["Agentic SDLC", "AI SDLC"]
---

# AI-Native SDLC

Code가 더 이상 bottleneck이 아니라는 전제에서, Plan·Review/Test·Deploy와 거버넌스를 AI-native loop로 재설계한 소프트웨어 생명주기. Agentic SDLC와 동일 개념이다.

## 정의

Linear flow → loop, AI embedded at each point, automated handover. 각 stage가 version-controlled committed artifact를 남기고 다음 stage가 이를 읽는다: `intent.md → spec.md → plan.md → diff+tests → PR findings → incident → intent.md` ([[ai-native-sdlc-playbook]]).

## 핵심 메커니즘

- **Artifact chain = audit trail**: who asked·what produced·who approved.
- **Build**: plan mode + CLAUDE.md + skills + hooks + parallel sessions + [[subagents]].
- **Test**: session self-verification + continuous evals (20-50 tasks, pass-rate gate).
- **Deploy**: AI review loop + hooks as approval gates + `claude -p` headless.
- **Maintain**: deterministic detection + `bands.yaml` (1σ/2σ/3σ) → 진단 intent.md → human triage → eval 추가.

## 과학 컴퓨팅 관점

[[agentic-ai-scientific-computing]]의 8건 보고서는 같은 전환을 보여준다: engineering bottleneck↓, 검증이 새 병목, 연구자 역할 = 정의·검증·조율. Upstream vs fork governance가 유지관리 과제.

## 관련 페이지

- [[agent-skills]] — 제도화 수단
- [[agent-eval]] — continuous evals
- [[ai-coding-workflow]] — 종합 토픽
