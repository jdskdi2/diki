---
title: "DESIGN.md"
created: 2026-09-21
updated: 2026-09-21
tags: [concept, ai, llm]
sources: [design-md-google-stitch-guide.md]
aliases: ["디자인엠디", "Vibe Design"]
---

# DESIGN.md

AI agent가 읽는 plain-text design system 문서. Google Stitch 도입 개념 (공식 명명 Vibe Design, 2026-03).

## 정의

"A plain-text design system document that AI agents read to generate consistent UI." 근거: "Markdown is the format LLMs read best." 프로젝트 루트에 두면 Figma export·JSON schema·툴링 없이 동작한다.

## 포맷 9섹션

Visual Theme / Color Palette & Roles / Typography / Component Stylings / Layout / Depth & Elevation / Do's and Don'ts / Responsive / Agent Prompt Guide.

## 역할 분리

`AGENTS.md` (how to build) vs `DESIGN.md` (look & feel). 함께 관리 권장. [[agent-docs-pattern]]에서 CLAUDE.md·SKILL.md·intent/spec/plan과 함께 정리한다.

## 생태계와 한계

VoltAgent `awesome-design-md` (9 카테고리 69 브랜드, MIT) + `getdesign.md` 조회·CLI (`npx getdesign@latest add stripe`). 한계: 공개 CSS 추출 ≠ 공식토큰, drift·유지보수 불확실, 브랜드 identity 상업용 확인 필요.

## 관련 페이지

- [[google-stitch]] — 도입 주체
- [[agent-skills]] — Stitch skills 연동
- [[agent-docs-pattern]] — 종합 토픽
