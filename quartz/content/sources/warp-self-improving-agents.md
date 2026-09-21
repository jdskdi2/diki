---
title: "How Warp Builds Self-Improving Agents on Claude"
created: 2026-09-21
updated: 2026-09-21
tags: [source, ai, llm]
sources: [Clippings/How Warp builds self-improving agents on Claude.md]
aliases: ["Warp Self-Improving Loop"]
---

# How Warp Builds Self-Improving Agents on Claude

[[warp]]가 Agent Skills 기반 self-improvement loop로 stateless human feedback 문제를 해결한 사례. 10M Claude Code sessions, 40M Warp Agent conversations 규모에서 검증된 패턴이다.

원문: https://claude.com/blog/how-warp-builds-self-improving-agents-on-claude

## 핵심 구조 — 2 skills + human in between

Inner/base skill이 일하고 → human feedback을 모은 뒤 → outer/improver skill이 주기적으로 base skill을 작은 PR로 고쳐서 다음 실행에 상속시킨다.

- **문제**: first-pass prompt 80% 정확도면 noisy한 경험. 수동 prompt rewrite·AGENTS.md 개선은 scale 안 됨.
- **해법**: Skills는 plain files라 agent가 잘 고친다. 업데이트는 reviewable·approvable·mergeable하며 정상 PR workflow 통과 후 다음 run에 상속.
- **실전 예 (issue triage)**: GitHub issue → triage agent (label·complexity·feasibility) → maintainer가 what+why로 피드백 → scheduled improver agent가 feedback 수집·요약 → 최소 edit 제안 → human approve·merge.

## Skill 작성·운영 팁

- **Principles not rules**: 똑똑한 사람에게 지시하듯 (`Look for repeated code` > 변수명 exhaustive rules). Why 설명으로 일반화 유도.
- **Small + [[progressive-disclosure]]**: 본문 대신 resource files·scripts 참조.
- **Feedback quality > volume**: 시니어의 detailed domain feedback 소량도 강력. 수집은 PR/issue 코멘트처럼 일하는 곳에서 low friction으로.
- **Skills vs memory**: skills = procedural·stable·run-agnostic·deliberate 변경 vs memory = 추론 중 auto-written·계속 변함.
- **측정**: verifiable domain은 verification harness 먼저. Non-verifiable은 golden outputs + deterministic evals. Global metrics (time to merge·contributor count·cost)로 개선 측정.

## 관련 페이지

- [[warp]] — 사례 주체
- [[agent-skills]] — skill 개념 정리
- [[agent-eval]] — eval·harness·golden outputs
- [[progressive-disclosure]] — skill 설계 원칙
- [[agent-skill-eval]] — eval 관점의 동반 소스
- [[agent-skills-eval-loop]] — 종합 토픽
