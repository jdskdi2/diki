---
title: "AI Tools Study — 같은 모델, 다른 도구"
created: 2026-09-22
updated: 2026-09-22
tags: [source, ai, llm, productivity, tool]
sources: [ai-tools-study.html]
aliases: ["AI 도구는 왜 이렇게 많을까", "AI Tools Spectrum"]
---

# AI Tools Study — 같은 모델, 다른 도구

개인 스터디 노트 (`raw/notes/ai_tool/ai-tools-study.html`). ChatGPT·Claude Code·Cursor·OpenClaw 등이 겉보기엔 다르지만 GPT·Claude·Gemini·Grok 몇 개 모델을 공유한다는 관찰에서 출발. 차이를 만드는 건 모델이 아니라 **모델을 감싸는 틀([[ai-harness]])** 이라는 주장.

## 핵심 주장

- **같은 모델, 다른 하네스**: 7가지 유형은 "완전히 다른 AI"가 아니라 소수 모델을 각기 다른 system prompt·Tool·Context·실행 환경·Agent Loop로 감싼 결과.
- **선택 기준은 모델이 아니라 하네스**: 어떤 모델이냐 못지않게 어떤 하네스 위에서 쓰느냐가 결과물을 가른다.
- **체감 차이는 자율성에서**: 세 분류축 중 "얼마나 맡기는가"가 가장 큰 체감 차이를 만든다.

## 하네스 5요소 (Harness)

| 요소 | ChatGPT 예시 | Codex 예시 |
|------|--------------|------------|
| 시스템 프롬프트 | 친절한 대화 어시스턴트 | 계획·수정·테스트하는 코딩 에이전트 |
| Tool | 웹검색·이미지 생성 | 파일 읽기/쓰기·셸·git |
| Context | 대화 히스토리 | 프로젝트 파일 구조·코드 전체 |
| 실행 환경 | 텍스트 반환 샌드박스 | 실제 파일 변경 가능한 로컬/클라우드 |
| Agent Loop | 1회 응답 후 대기 | 계획→실행→확인→재시도 반복 |

같은 Claude라도 Chat / [[claude-code]] / [[claude-cowork]] 에서 prompt·tool·context·환경·loop가 전부 다르게 동작한다는 두 번째 예시도 포함.

## 3분류축 + 7유형 스펙트럼

**세 가지 기준** ([[ai-tool-autonomy-spectrum]]):
1. 어디서 말을 거는가 (interface: 채팅·터미널·에디터·브라우저·메신저)
2. 얼마나 맡기는가 (autonomy: 매 턴 확인 ↔ 맡기고 잊음)
3. 실제로 어디서 일이 벌어지는가 (execution: 로컬 셸·클라우드 VM·로그인된 웹)

**자율성 낮은 → 높은 순 7유형**:

| # | 유형 | 대표 도구 | 인터페이스 / 실행 몸체 |
|---|------|----------|----------------------|
| 01 | Chat | ChatGPT·Claude·Gemini·Grok | 채팅창 / 없음 |
| 02 | 코딩 CLI | [[claude-code]]·Codex CLI·Gemini CLI | 터미널 / 로컬 셸 |
| 03 | 코딩 IDE | [[cursor]]·Windsurf·Copilot·[[google-antigravity]] | 에디터 / 에디터+로컬 |
| 04 | 브라우저형 | [[aside]]·Comet·Atlas·Claude in Chrome | 브라우저 / 로그인된 웹페이지 |
| 05 | 데스크톱 위임형 | [[claude-cowork]]·ChatGPT Agent | 데스크톱 앱 / 로컬 파일+앱 |
| 06 | 메신저 상주형 | [[openclaw]]·Hermes Agent | 메신저 / 상시 프로세스 |
| 07 | 팀원형 | [[grok-bot]] | 역할 부여 텍스트 / 클라우드 전용 VM |

유형별 차별점: CLI는 **실행 권한**(파일 변경·명령 실행)이 Chat과 다름. IDE는 diff·파일 구조로 시각 확인 + Antigravity의 멀티 에이전트 병렬. 브라우저형은 API 없이 로그인된 사이트 직접 조작. 위임형은 비개발자 사무 업무용 포장. 상주형은 앱을 켜지 않아도 서버 상시 대기 + 모델 교체 가능, 대신 권한·보안 리스크. 팀원형은 전용 VM + 이메일/업무툴 로그인 + 역할별 다중 실행.

## 관련 페이지

- [[ai-harness]] — 5요소 프레임워크 개념
- [[ai-tool-autonomy-spectrum]] — 3축·7유형 분류 개념
- [[claude-code]] — CLI 대표, Chat/Cowork 대비 예시
- [[cursor]] — IDE 대표
- [[aside]] — 브라우저형 대표
- [[claude-cowork]] — 데스크톱 위임형 대표
- [[openclaw]] — 메신저 상주형 대표
- [[grok-bot]] — 팀원형 대표
- [[agent-docs-pattern]] — system prompt·SKILL 등 하네스 문서 패턴 토픽
- [[ai-coding-workflow]] — coding CLI/IDE가 속한 workflow 토픽
