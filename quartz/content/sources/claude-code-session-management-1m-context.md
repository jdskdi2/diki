---
title: "Using Claude Code — Session Management and 1M Context"
created: 2026-09-21
updated: 2026-09-21
tags: [source, ai, llm]
sources: [Clippings/Using Claude Code session management and 1M context.md]
aliases: ["Claude Code 1M Session Guide"]
---

# Using Claude Code — Session Management and 1M Context

[[thariq-shihipar]]의 실용 가이드. 1M context로 길어진 session을 다섯 가지 수단으로 관리하는 법을 정리한다.

원문: https://claude.com/blog/using-claude-code-session-management-and-1m-context

## 핵심 주장

매 턴을 branching point로 보고 목적에 맞는 수단을 골라야 한다. Continue가 default지만, 잘못된 경로는 rewind, 새 task는 clear, 비대해진 mid-task는 compact, 결론만 필요하면 subagent가 정답이다.

## 다섯 가지 선택지

| 상황 | 수단 |
|------|------|
| 같은 task 계속 | Continue |
| 잘못된 경로 | `/rewind` (Esc Esc, 이후 삭제 후 재시도) |
| 비대해진 mid-task | Compact (`/compact focus on X, drop Y`처럼 steer) |
| 새 task | `/clear` (직접 brief 작성, fresh start) |
| 중간산출물 중 결론만 필요 | [[subagents]] (깨끗한 window에 위임, 결과만 회수) |

## 주요 팁

- **New task = new session**: 1M으로 full-stack app도 가능하지만 [[context-rot]]은 여전. 단 context 재구축 비용이 크면 같은 session 유지가 싸다.
- **Rewind > correction**: 실패한 시도에 덧붙이기보다 file reads 직후로 rewind 후 배운 점 포함 재프롬프트.
- **Bad autocompact 방지**: 방향 예측 불가 상태에서 자동 compaction되면 요약에서 탈락한話題로 점프할 때 손실. 1M 여유를 활용해 proactively `/compact` + 하고 싶은 일 설명이 안전. Compaction 시점이 rot으로 가장 least intelligent한 시점이기 때문.
- **Subagent 판단 테스트**: "will I need this tool output again, or just the conclusion?"

## 관련 페이지

- [[claude-code]] — 대상 제품
- [[compaction]] — compact/autocompact 개념
- [[subagents]] — 위임 패턴
- [[context-rot]] — 길어진 session의 성능 저하
- [[context-engineering-memory-compaction-tool-clearing]] — API 관점의 compaction
- [[thariq-shihipar]] — 저자
