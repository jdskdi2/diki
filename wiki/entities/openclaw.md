---
title: "OpenClaw"
created: 2026-09-22
updated: 2026-09-22
tags: [entity, tool, ai, llm]
sources: [ai-tools-study.md]
aliases: ["오픈클로"]
---

# OpenClaw

메신저 상주형 에이전트의 대표 예시. 텔레그램·디스코드 같은 메신저로 지시하면 서버에 상시 대기 중인 프로세스가 알아서 판단하고 움직인다.

## 특징

- **인터페이스**: 메신저. 실행 몸체는 서버·컴퓨터에서 계속 켜져 있는 프로세스 ([[ai-tools-study]]).
- **차별점**: 특정 회사 모델에 묶이지 않고 원하는 모델을 갈아 끼울 수 있음 (model-agnostic). 내가 앱을 켜지 않아도 동작.
- **리스크**: 계속 켜져 있고 권한도 많다는 점에서 잘못된 지시나 외부 공격(prompt injection 등)에 노출될 위험이 함께 언급됨.

## 관련 페이지

- [[ai-harness]] — 실행 환경·loop가 차별점인 사례
- [[ai-tool-autonomy-spectrum]] — 상주형이 속한 분류 (자율성 매우 높음)
- [[grok-bot]] — 비슷하게 상시 동작하지만 전용 VM을 갖는 팀원형과 대비
- [[aside]] — 로그인된 환경 조작이라는 점에서 유사, 상시성은 다름
