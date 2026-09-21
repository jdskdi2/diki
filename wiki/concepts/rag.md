---
title: "RAG (Retrieval-Augmented Generation)"
created: 2026-07-03
updated: 2026-07-03
tags: [concept, ai, llm]
aliases: ["Retrieval Augmented Generation"]
---

# RAG (Retrieval-Augmented Generation)

LLM이 외부 문서 컬렉션에서 관련 정보를 검색한 뒤 답변을 생성하는 패턴.

## 작동 방식

1. 사용자가 문서 컬렉션 업로드
2. 쿼리 시 LLM이 관련 chunk를 검색
3. 검색된 fragment를 контекст로 활용해 답변 생성

## 한계 (LLM Wiki 관점에서)

- 매 질문마다 관련 fragment를 새로 검색해야 함 — **축적이 없음**
- 5개 문서를 종합해야 하는 질문이면, LLM이 매번 관련 조각을 찾아 조각拼凑
- NotebookLM, ChatGPT file uploads 등이 이 방식 사용

## LLM Wiki와의 차이

| | RAG | LLM Wiki |
|---|-----|----------|
| 지식 저장 | 검색 인덱스 (chunk) | 구조화된 위키 (markdown) |
| 쿼리 시 | 매번 새로 검색 | 미리 구축된 위키에서 탐색 |
| 교차참조 | 없음 | 위키 페이지 간 링크로 사전 구축 |
| 종합 | 쿼리마다 재생성 | 점진적으로 구축되고 유지됨 |
| bookkeeping | LLM이 하지 않음 | LLM이 담당 |

## 관련 페이지

- [[llm-wiki-karpathy]] — RAG 대안으로서의 LLM Wiki
- [[memex]] — 지식 저장소의 역사적 맥락
- [[context-engineering]] — 검색 대신 미리 구축된 위키·context를 curate하는 방식
- [[context-engineering-guide]] — context 실전 종합 토픽
