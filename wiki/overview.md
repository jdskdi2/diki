---
title: "Overview"
created: 2026-07-02
updated: 2026-07-02
tags: [overview, navigation]
aliases: ["Home", "Dashboard"]
---

# Overview

**Personal Knowledge Management (PKM) 위키** — LLM이 구축하고 유지보수하는 지식 베이스입니다.

## 어떻게 작동하나

- **소스**를 `raw/` 폴더에 넣습니다 — 아티클, 논문, 메모 등
- LLM이 읽고 **위키 페이지**를 `wiki/` 에 생성합니다
- 페이지들은 `[[obsidian-link]]` 로 서로 교차참조합니다
- **Obsidian**에서 탐색합니다 — graph view, 링크, 검색

## 구조

| 폴더 | 역할 |
|------|------|
| `raw/` | 원본 소스 문서 (수정 불가) |
| `wiki/` | LLM이 생성한 위키 페이지 (한국어+영어) |

## 페이지 유형

- **[[index\|Index]]** — 위키 전체 내용 카탈로그
- **Sources** — 소스별 요약 페이지
- **Entities** — 사람, 도구, 조직
- **Concepts** — 이론, 프레임워크, 핵심 아이디어
- **Topics** — 여러 소스를 종합한 주제 페이지

## 시작하기

1. `raw/articles/`, `raw/papers/`, `raw/notes/` 에 소스 파일을 넣습니다
2. LLM에게 ingest를 요청합니다
3. Obsidian에서 생성된 페이지를 탐색합니다
4. 질문하면 LLM이 위키를 검색하고 답변을 종합합니다
