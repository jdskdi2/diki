---
title: "Agent Docs Pattern — AGENTS, CLAUDE, SKILL, DESIGN, Intent"
created: 2026-09-21
updated: 2026-09-21
tags: [topic, ai, llm]
sources: [design-md-google-stitch-guide.md, ai-native-sdlc-playbook.md, context-engineering-claude-5-rules.md, openai-model-spec-approach.md]
aliases: ["에이전트 문서 패턴"]
---

# Agent Docs Pattern — AGENTS, CLAUDE, SKILL, DESIGN, Intent

에이전트에게 읽히는 문서들의 역할 분담 패턴. 각 문서는 다른 질문에 답한다.

## 문서 지도

| 문서 | 질문 | 범위 | 예시 위치 |
|------|------|------|-----------|
| AGENTS.md | how to build (repo 공통) | 빌드·테스트·규약 | repo root |
| CLAUDE.md | 이 repo의 gotchas | ≤1페이지, 두 번 틀리면 기록 | repo root |
| SKILL.md | 필요 시 찾는 guide | lightweight, 과도한 제약 금지 | `.claude/skills/<name>/` |
| DESIGN.md | look & feel | color·type·component·prompt | project root |
| intent/spec/plan.md | 무엇을·왜·어떻게 | artifact chain, commit됨 | stage별 |
| System prompt | product context | harness 제작 시 집중 | 제품 내부 |
| [[model-spec]] | 행동 경계 | hierarchy + hard rules | 조직 공개 |

## 원칙

- **얇게 + 참조 분리**: 자주 읽히는 문서일수록 짧게. 세부사항은 참조 파일로 ([[progressive-disclosure]]).
- **버전관리**: skills·CLAUDE·intent/spec/plan 모두 git에 commit. 정책 변경 시 owner sign-off.
- **판단 위임**: Claude 5 세대는 강한 guardrail보다 가벼운 context + rich references (code·rubrics·verifier agents)가 효과적.
- **DESIGN은 별도 축**: 기능 명세와 시각 명세를 분리해 각 agent가 자기 문서만 읽게 한다 ([[design-md]]).

## 관련 페이지

- [[design-md]] — 시각 명세 개념
- [[agent-skills]] — skill 문서 개념
- [[model-spec]] — 행동 명세 개념
- [[ai-native-sdlc]] — artifact chain 개념
