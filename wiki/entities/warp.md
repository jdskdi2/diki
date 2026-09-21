---
title: "Warp"
created: 2026-09-21
updated: 2026-09-21
tags: [entity, tool, ai, llm]
sources: [warp-self-improving-agents.md]
aliases: ["워프"]
---

# Warp

AI-powered terminal + agentic development environment (2020 설립). Claude 기반 self-improving agent loop 사례의 주체다.

## 핵심 내용

- **규모**: $73M 투자, 월 800K 개발자, Fortune 500의 56% 사용, 10M Claude Code sessions, 40M Warp Agent conversations.
- **패턴**: inner/base skill → human feedback → outer/improver skill (scheduled, Oz 플랫폼에서 실행) → 작은 PR → 다음 run에 상속 ([[warp-self-improving-agents]]).
- **스택**: Rust / Golang / GitHub Actions. 공개 데모 `warp-agents-demo-github-issue-triage`.

## 관련 페이지

- [[agent-skills]] — base/improver skill 개념
- [[agent-eval]] — feedback 품질과 측정
- [[agent-skills-eval-loop]] — 종합 토픽
