---
title: "The AI-Native SDLC Playbook (Claude)"
created: 2026-09-21
updated: 2026-09-21
tags: [source, ai, llm]
sources: [Clippings/The AI-Native SDLC playbook  Claude by Anthropic.md]
aliases: ["AI-Native SDLC", "Agentic SDLC"]
---

# The AI-Native SDLC Playbook (Claude)

Anthropic Applied AI팀의 stage-by-stage playbook. Code가 더 이상 bottleneck이 아니므로, build 주변의 human-speed 단계(Plan·Review/Test·Deploy)와 거버넌스를 AI-native loop로 재설계해야 한다고 주장한다.

원문: https://claude.com/blog/the-ai-native-sdlc-playbook

## 핵심 주장

Linear flow → loop. AI embedded at each point, automated handover. 각 stage가 version-controlled committed artifact를 남기고 다음 stage가 이를 읽으며, human은 gate에서 판단·승인에 집중한다.

Artifact chain: `intent.md → spec.md → plan.md → diff+tests → PR findings → incident → intent.md` (audit trail: who asked·what produced·who approved).

## Stage별要点

- **Plan** = `intent.md` (human readable + machine actionable). **Design** = requirements+design 단일 세션, skills로 정책 적용·git versioned.
- **Build**: plan mode default (읽기만, `plan.md` commit). `CLAUDE.md` ≤1페이지 (`/init` 생성 후 cut down, 두 번 틀리면 기록). skills (`.claude/skills/<name>/SKILL.md`, 정책 변경 시 owner sign-off). hooks (보호 경로 차단·format/lint·credential 차단). parallel sessions (worktree별 독립) + [[subagents]].
- **Test**: session self-verification (`make test/build/lint`). Continuous evals in CI (20-50 real tasks, pass-rate로 merge gate, incident마다 영구 eval 추가).
- **Deploy**: AI in PR review loop (`REVIEW.md` 3 passes: Bugs·Security·Compliance). hooks as approval gates (`production-gate.sh`). CI/CD는 `claude -p` read-only triage → branch protection 경유 PR.
- **Maintain = closing the loop**: deterministic detection script (rolling window·Western Electric rules) + `bands.yaml` (1σ log, 2σ read-only diagnose, 3σ PR/runbook) → `claude -p` 실행 → 진단 `intent.md` → human triage → fix 후 eval 추가.

## 관련 페이지

- [[ai-native-sdlc]] — 개념 정리
- [[agent-skills]] — skills 운영
- [[agent-eval]] — continuous evals
- [[subagents]] — build 병렬화
- [[claude-code]] — 실행 도구
- [[agentic-ai-scientific-computing]] — 과학 소프트웨어 관점의 동반 소스
- [[ai-coding-workflow]] — 종합 토픽
