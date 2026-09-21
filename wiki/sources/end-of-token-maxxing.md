---
title: "'토큰 맥싱'의 시대는 끝났다 — 메타·아마존·우버의 선택"
created: 2026-09-21
updated: 2026-09-21
tags: [source, ai, llm]
sources: [Clippings/'토큰 맥싱'의 시대는 끝났다 메타·아마존·우버의 선택.md]
aliases: ["End of Token Maxxing", "Token-Maxxing"]
---

# '토큰 맥싱'의 시대는 끝났다 — 메타·아마존·우버의 선택

2025년 유행한 token 사용량 리더보드로 AI 활용도를 줄 세우던 token-maxxing 문화의 붕괴를 다룬 기사. Token ≠ 산출물·정직도이며 token = 공급자 매출일 뿐이라는 주장이다.

원문: https://yozm.wishket.com/magazine/detail/3790/ (2026-06-09, Yozm IT)

## 핵심 주장

실력은 "적게 쓰고 잘 쓰기" + "무엇을 풀었는지" outcome으로 평가해야 한다.

## 붕괴 3원인

1. **토큰 ≠ 산출물**: Uber가 2026년 AI 코딩 예산을 4달 만에 소진, 일부 엔지니어 월 $2,000 → 성과 입증 불가 → 도구별 1인당 월 $1,500 cap + 내부 대시보드 + 예외 승인제.
2. **토큰 ≠ 정직도**: Amazon 직원이 사내 도구로 불필요 작업까지 AI에 떠넘기며 부풀리기. [[token-maxxing]]은 Goodhart's law의 전형 — 잣대가 목표가 되면 잣대로서 무효.
3. **토큰 = 공급자 매출**: 신형 모델 단가 인상 (GPT-5.5 직전 2배, Gemini 3.5 Flash 약 3배, Claude Opus 4.7 새 tokenizer로 동일 텍스트 최대 +35% token). 공급자 악마화는 아니나 소비자 성과와 무관한 지표를 내 성과로 착각 말 것.

## 대안

- **적게 쓰고 잘 쓰기**: Anthropic 원칙 — 결과 가능성 최대 + 신호 분명한 정보만 최소 투입. Harness engineering (context 주입·성과 관리·피드백 루프) 발전. 한국 신조어 토성비 (토큰 가성비) — 돈으로 무엇을 얻었는가.
- **성과 측정은 발명 불필요**: LOC로 개발자 평가하면 장황 코드만 양산되듯, 기존 방식대로 "어떤 고객/조직 문제를 풀었고 얼마 기여했는가" 물으면 됨.

## 관련 페이지

- [[token-maxxing]] — 개념 정리
- [[context-engineering]] — 최소 투입 원칙의 이론적 근거
- [[effective-context-engineering-agents]] — Anthropic 원칙 원문 요약
- [[ai-coding-workflow]] — 비용·성과 관점 종합 토픽
