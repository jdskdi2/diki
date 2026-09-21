---
title: "The New Rules of Context Engineering for Claude 5"
created: 2026-09-21
updated: 2026-09-21
tags: [source, ai, llm]
sources: [Clippings/The new rules of context engineering for Claude 5 generation models.md]
aliases: ["Claude 5 Context Rules"]
---

# The New Rules of Context Engineering for Claude 5

[[thariq-shihipar]] (Anthropic, Claude Code 담당)의 글. Claude 5급 모델(Opus 5, Fable 5)은 judgment와 [[progressive-disclosure]] 능력이 올라, Claude Code system prompt의 80% 이상을 삭제해도 coding eval 손실이 없었다는 실험에서 출발한다.

원문: https://claude.com/blog/the-new-rules-of-context-engineering-for-claude-5-generation-models

## 핵심 주장

Context engineering도 "overconstraining 규칙 나열"에서 "판단을 살리는 가벼운 context + 필요 시점 로딩 + 잘 설계된 interface"로 바꿔야 한다.

## Then → Now 6개 전환

1. **Rules → Judgement**: "no comments" 같은 강한 guardrail 삭제 → "Write code that reads like surrounding code"처럼 모델 판단에 위임.
2. **Examples → Interfaces**: Tool 사용 예시가 탐색 공간을 제약. Enum + 한 줄 힌트 같은 expressive한 parameter 설계가 낫다.
3. **Upfront → Progressive disclosure**: 상시 불필요 정보는 skill로 분리해 선택 호출. Tool도 deferred loading.
4. **Repeat → Simple tool descriptions**: System + tool 중복 제거. 사용법은 tool description 한 곳에.
5. **CLAUDE.md memory → Auto-memory**: `#` 수동 저장 대신 관련 memory 자동 저장.
6. **Simple specs → Rich references**: Markdown plan을 넘어 HTML artifacts, code, rubrics + verifier agents를 reference로. `@` mention으로 포함.

## 조립법

- **System** = product context (harness 제작 시에 집중, 평소엔 건드리지 않음)
- **CLAUDE.md** = repo 한 줄 소개 + gotchas에 토큰 집중, obvious한 내용은 생략
- **Skills** = 필요 시 찾는 lightweight guide, 과도한 제약 금지, 길면 다파일 분할
- **References** = plan 관련 심층 정보

## 관련 페이지

- [[context-engineering]] — 상위 개념
- [[progressive-disclosure]] — 핵심 전환 전략
- [[agent-skills]] — skill 설계 지침
- [[effective-context-engineering-agents]] — 이전 세대 정의 글
- [[claude-code]] — 적용 대상 제품
- [[thariq-shihipar]] — 저자
