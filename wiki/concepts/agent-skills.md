---
title: "Agent Skills"
created: 2026-09-21
updated: 2026-09-21
tags: [concept, ai, llm]
sources: [warp-self-improving-agents.md, agent-skill-eval.md, ai-native-sdlc-playbook.md, context-engineering-claude-5-rules.md]
aliases: ["에이전트 스킬", "SKILL.md"]
---

# Agent Skills

Prompt에 직접 넣지 않고 file-based로 인코딩한 지식. Agent가 lookup하며 사용하는 실행 단위다.

## 구조

**Progressive disclosure 3겹** ([[agent-skill-eval]]): title+description (항상 context, trigger 판단) → SKILL.md 본문 (통째로 context) → 참조 파일들 (필요시 탐색).

종류 2종: capability skill (한시적, 모델 향상 시 폐기) vs preference skill (팀 취향·관행, 오래감, regression 보호).

## 작성 원칙

- **Principles not rules**: 똑똑한 사람에게 지시하듯, why 설명으로 일반화 유도.
- **얇게 + 참조 분리**: description은 매 호출 100~200 token 비용. `SKILL.md 500줄` 초과 = 리팩토링 신호.
- **Directive, not essay**: 절차 못박지 말고 목표·제약만 (고정 흐름은 스크립트로). no-op 제거.
- **Claude 5 스타일** ([[context-engineering-claude-5-rules]]): 필요 시 찾는 lightweight guide, 과도한 제약 금지, 길면 다파일 분할.
- **SDLC 운영** ([[ai-native-sdlc-playbook]]): `.claude/skills/<name>/SKILL.md`, 정책 변경 시 owner sign-off, institutional knowledge의 version-controlled operational화.

## Self-improvement loop

[[warp]] 패턴: base skill → human feedback → improver skill (scheduled) → 작은 PR → 다음 run 상속. Skills는 plain files라 agent가 잘 고치고, PR workflow로 review 가능 ([[warp-self-improving-agents]]).

## 관련 페이지

- [[agent-eval]] — skill 검증 (쌍으로 읽을 것)
- [[progressive-disclosure]] — 설계 원칙
- [[agent-skills-eval-loop]] — 종합 토픽
- [[philipp-schmid]] — eval 강연자
