---
title: "LLM Wiki (Karpathy Gist)"
created: 2026-07-03
updated: 2026-07-03
tags: [pkm, llm, wiki, knowledge-management]
sources: [raw/articles/llm-wiki.md]
aliases: ["LLM Wiki Pattern"]
---

# LLM Wiki (Karpathy Gist)

Andrej Karpathy가 제안한 **LLM 기반 Personal Knowledge Management 패턴**. GitHub Gist로 공개됨.

## 핵심 아이디어

기존 RAG와 다른 접근법: 소스를 매번 새로 검색하는 대신, LLM이 **지속적인 위키를 점진적으로 구축**한다.

- 소스 추가 시 인덱싱만 하는 게 아니라, 핵심 정보를 추출하고 기존 위키에 통합
- 엔티티 페이지 업데이트, 토픽 요약 수정, 모순 감지, 점진적 종합 강화
- 지식은 한 번 컴파일되고 현재 상태로 유지됨 (매 쿼리마다 재생성되지 않음)

## 3계층 아키텍처

| 계층 | 설명 |
|------|------|
| **Raw sources** | 원본 소스 컬렉션. LLM이 읽기만 하고 수정 불가 |
| **The wiki** | LLM이 생성한 markdown 파일 디렉토리. LLM이 전체를 소유 |
| **The schema** | `AGENTS.md` 같은 설정 파일. LLM에게 위키 구조와 워크플로우를 정의 |

## 3가지 작업

### Ingest
소스를 추가하면 LLM이: 읽기 → 핵심 내용 토론 → 요약 페이지 작성 → 인덱스 업데이트 → 엔티티/개념 페이지 업데이트 → 로그 기록. 하나의 소스가 10-15개 위키 페이지를 건드릴 수 있음.

### Query
질문하면 LLM이 위키를 검색하고 관련 페이지를 읽어 답변을 종합. 좋은 답변은 새 위키 페이지로 저장 가능 — 지식이 축적됨.

### Lint
주기적으로 건강검진: 모순, stale 콘텐츠, 고아 페이지, 누락 교차참조, 데이터 갭 확인.

## indexing과 logging

- **index.md**: 내용 기반 카탈로그. 모든 페이지를 카테고리별로 나열. ingest 시 업데이트
- **log.md**: 시간순 append-only 기록. `## [YYYY-MM-DD] ingest | 제목` 형식으로 파싱 가능

## 왜 효과적인가

bookkeeping이 번거로운데, LLM은 지루해하지 않고 교차참조를 잊지 않으며 한 번에 15개 파일을 업데이트할 수 있음. 유지보수 비용이 거의 0이 되어 위키가 지속됨.

## 참고

- 이 아이디어는 Vannevar Bush의 **[[memex|Memex]]** (1945)와 정신적으로 계승
- Bush의 비전: 개인적, 능동적으로 큐레이션되는, 문서 간 연결이 문서 자체만큼 중요한 지식 저장소
- Bush가 해결하지 못한 것은 유지보수를 누가 하느냐 — LLM이 이를 처리

## 관련 페이지

- [[memex]] — Vannevar Bush의 Memex 개념
- [[obsidian]] — 위키 탐색 도구
- [[rag]] — 기존 RAG 방식과의 비교
