---
title: "DESIGN.md — Google Stitch 도입 가이드"
created: 2026-09-21
updated: 2026-09-21
tags: [source, ai, llm]
sources: [Clippings/DESIGN.md  Google Stitch가 도입한 DESIGN.md - DESIGN.md 도입 배경부터 적용해보기(VoltAgent awesome-design-md 컬렉션 활용 가이드).md]
aliases: ["DESIGN.md Guide", "Stitch DESIGN.md"]
---

# DESIGN.md — Google Stitch 도입 가이드

[[google-stitch]]가 도입한 DESIGN.md 개념 정리 (갓대희 블로그, 2026-04-23). AI agent용 plain-text design system 문서로, 프로젝트 루트 Markdown 한 장에 color·typography·component·layout·prompt까지 명세해 AI UI 생성의 랜덤성을 single source of truth로 해결한다.

원문: https://goddaehee.tistory.com/582

## 핵심 내용

- **정의**: "A plain-text design system document that AI agents read to generate consistent UI." 근거: "Markdown is the format LLMs read best, so there's nothing to parse or configure."
- **역할 분리**: `AGENTS.md` (how to build) vs `DESIGN.md` (look & feel). 함께 관리 권장.
- **포맷 9섹션**: Visual Theme / Color Palette & Roles (semantic name+hex+role) / Typography / Component Stylings (상태포함) / Layout / Depth & Elevation / Do's and Don'ts / Responsive / Agent Prompt Guide (Quick Color Reference + 복붙 프롬프트).
- **컬렉션**: VoltAgent `awesome-design-md` (MIT, 9 카테고리 69 브랜드). 본문은 `getdesign.md/{brand}/design-md`에서 조회. 설치: `npx getdesign@latest add stripe` → 프로젝트 루트 `DESIGN.md` 저장.
- **대표 예시 3**: Stripe (sohne-var, 얇은 헤드라인, blue-tinted multi-layer shadow) / Vercel (shadow-as-border, Geist + 극단 음수자간) / Linear (dark-mode-first, Inter Variable, `#08090a` + indigo-violet 단일 크로마).
- **활용**: 복사 → 루트 → 에이전트에 명시적 참조 지시. 스켈레톤: 구체 hex/rgba, semantic 이름, 상태포함, 섹션9 프롬프트 조각.
- **한계**: 공개 CSS 추출 ≠ 공식토큰, 신규 레포 drift·유지보수 불확실, 브랜드 visual identity 소유권 별개·상업용 확인 필요. Google 공식 명명은 Vibe Design (2026-03).

## 관련 페이지

- [[design-md]] — 개념 정리
- [[google-stitch]] — 도입 주체
- [[agent-docs-pattern]] — AGENTS.md·CLAUDE.md·SKILL.md와 묶는 종합 토픽
- [[agent-skills]] — Stitch skills 연동 관점
