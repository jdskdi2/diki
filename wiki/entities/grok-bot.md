---
title: "Grok Bot"
created: 2026-09-22
updated: 2026-09-22
tags: [entity, tool, ai, llm]
sources: [ai-tools-study.md]
aliases: ["그록 봇"]
---

# Grok Bot

팀원형 에이전트의 예시. 메신저 상주형처럼 계속 일하지만 자기 전용 컴퓨터(클라우드 VM)를 따로 갖고, 이메일·업무툴에 직접 로그인해서 처리한다.

## 특징

- **인터페이스**: 업무 지시 (텍스트로 역할 부여). 실행 몸체는 클라우드에 마련된 전용 컴퓨터 ([[ai-tools-study]]).
- **운용**: "영업 Bot", "버그 재현 Bot"처럼 역할을 나눠 여러 개를 동시 실행. 밤새 시켜두고 아침에 결과만 확인하는 방식.
- **차별점**: [[openclaw]] (내 서버 상주 프로세스) vs Grok Bot (클라우드 전용 VM + 직접 로그인). 상주 위치와 계정 주체가 다름.

## 관련 페이지

- [[openclaw]] — 상주형 대비 대상
- [[ai-tool-autonomy-spectrum]] — 팀원형이 속한 분류 (자율성 매우 높음)
- [[subagents]] — 역할별 병렬 위임 패턴과 연결
