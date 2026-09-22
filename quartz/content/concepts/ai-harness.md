---
title: "AI Harness"
created: 2026-09-22
updated: 2026-09-22
tags: [concept, ai, llm]
sources: [ai-tools-study.md]
aliases: ["모델을 감싸는 틀", "Harness"]
---

# AI Harness

모델을 감싸고 있는 틀. 같은 모델도 이 틀이 다르면 완전히 다른 도구처럼 느껴진다는 프레임 ([[ai-tools-study]]).

## 5요소

| 요소 | 의미 | 예시 (ChatGPT vs Codex) |
|------|------|------------------------|
| 시스템 프롬프트 | 어떤 역할로 행동할지 지시 | 대화 어시스턴트 vs 계획·수정·테스트 에이전트 |
| Tool | 쓸 수 있는 도구 | 웹검색·이미지 vs 파일·셸·git |
| Context | 무엇을 보며 판단하는지 | 대화 히스토리 vs 프로젝트 파일 전체 |
| 실행 환경 | 일이 일어나는 곳 | 텍스트 샌드박스 vs 실제 파일 변경 환경 |
| Agent Loop | 얼마나 스스로 반복하는지 | 1회 응답 후 대기 vs 계획→실행→확인→재시도 |

같은 Claude가 Chat / [[claude-code]] / [[claude-cowork]] 에서 다르게 동작하는 것도 prompt·tool·context·환경·loop가 다르기 때문이라는 두 번째 예시 포함.

## 왜 중요한가

- **선택 기준 전환**: "어떤 모델이 똑똑한가"보다 "어떤 하네스 위에서 쓰느냐"가 결과를 더 크게 좌우할 때가 많음.
- **문서와 연결**: 하네스를 만드는 재료가 곧 에이전트 문서 (system prompt, SKILL, CLAUDE.md 등) — [[agent-docs-pattern]] 참조.

## 관련 페이지

- [[ai-tools-study]] — 원천 소스
- [[ai-tool-autonomy-spectrum]] — 하네스 차이를 유형으로 정리한 분류
- [[agent-docs-pattern]] — 하네스 제작 문서들의 역할 분담
- [[context-engineering]] — context를 curate하는 discipline으로 연결
- [[agent-skills]] — 하네스의 지식 인코딩 단위
