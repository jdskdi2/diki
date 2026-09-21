---
title: "Index"
created: 2026-07-02
updated: 2026-09-21
tags: [index, navigation]
aliases: ["Catalog", "Sitemap"]
---

# Index

## Sources

- [[llm-wiki-karpathy]] — Andrej Karpathy의 LLM Wiki 패턴 제안. RAG 대신 지속적 위키를 구축하는 PKM 접근법.
- [[github-pages-quartz-deploy]] — GitHub Pages + Quartz 배포 가이드. 자동 빌드/배포 과정과 GitHub Actions 상세 설명.
- [[effective-context-engineering-agents]] — Anthropic의 context engineering 정의 글. Smallest high-signal set + 3기법.
- [[context-engineering-memory-compaction-tool-clearing]] — Memory·compaction·tool clearing 실측 비교 (329K 토큰 실험).
- [[context-engineering-claude-5-rules]] — Claude 5 세대 규칙 전환. 80% 프롬프트 삭제 실험 + Then→Now 6전환.
- [[claude-code-session-management-1m-context]] — Claude Code 1M session 관리. Continue/Rewind/Clear/Compact/Subagents.
- [[claude-opus-5-system-prompts]] — Claude Opus 5 system prompt 전문. Safeguards routing + refusal 정책.
- [[warp-self-improving-agents]] — Warp의 self-improving loop. Base skill → feedback → improver skill → PR.
- [[ai-native-sdlc-playbook]] — Anthropic AI-native SDLC playbook. Artifact chain으로 도는 loop.
- [[prompt-engineering-best-practices-2026]] — 2026 prompt best practices. Core habits + 최소 advanced 조합.
- [[prompt-generation-openai-api]] — OpenAI Playground Generate 원리. Meta-prompt + meta-schema 공개.
- [[agent-skill-eval]] — 이밸 없이 스킬 배포 금지. Eval이 스킬보다 오래 산다.
- [[end-of-token-maxxing]] — Token-maxxing 붕괴 기사. Token ≠ 산출물, 적게 쓰고 잘 쓰기.
- [[openai-model-spec-approach]] — OpenAI Model Spec 접근법. Instruction hierarchy + hard rules.
- [[agentic-ai-scientific-computing]] — 에이전트 시대 과학 컴퓨팅 8건 보고. 검증이 새 병목.
- [[design-md-google-stitch-guide]] — Google Stitch DESIGN.md 도입 가이드. AI용 design system 문서.

## Entities

- [[andrej-karpathy]] — AI researcher. Tesla AI 전 이사, OpenAI 공동 창업자. LLM Wiki 패턴 원저자.
- [[obsidian]] — 마크다운 기반 PKM 도구. LLM Wiki에서 위키 탐색 IDE 역할.
- [[anthropic]] — Claude·Claude Code 개발사. Context engineering·SDLC 글 발행 주체.
- [[openai]] — GPT·Codex 제공사. Meta-prompt·Model Spec·과학 컴퓨팅 보고서 주체.
- [[claude-code]] — Anthropic agentic coding 도구. Context 기법들의 공통 예시.
- [[warp]] — AI 터미널 + agentic dev 환경. Self-improving loop 사례 주체.
- [[google-stitch]] — AI UI 생성 도구. DESIGN.md 개념 도입 (Vibe Design).
- [[thariq-shihipar]] — Anthropic MTS, Claude Code 담당. 5규칙·세션관리 글 저자.
- [[philipp-schmid]] — Google DeepMind. Skill eval 강연자.

## Concepts

- [[memex]] — Vannevar Bush의 Memex (1945). 개인적 지식 저장소와 associative trails 컨셉.
- [[rag]] — Retrieval-Augmented Generation. LLM Wiki가 대안으로 제시하는 기존 지식 검색 방식.
- [[context-engineering]] — 최적 context state를 curate하는 discipline. Prompt의 상위 개념.
- [[prompt-engineering]] — 지시 구조화 craft. Explicit·specific·context-rich + 최소 advanced.
- [[progressive-disclosure]] — 필요 시점 layer-by-layer 로딩. Skill·retrieval 공통 원칙.
- [[compaction]] — 대화 요약 압축 후 새 window로 계속. Lossy하지만 범용.
- [[agentic-memory]] — Window 밖 file 기반 지속 기록. Cross-session 유일 해법.
- [[tool-result-clearing]] — Tool result만 surgical 삭제. 가장 가벼운 compaction.
- [[subagents]] — 깨끗한 window에 위임 후 결론만 회수. 병렬 탐색에 강함.
- [[context-rot]] — 토큰 증가에 따른 recall·정밀도 저하. Context engineering의 문제 정의.
- [[agent-skills]] — File-based 지식 인코딩. 3겹 disclosure + principles not rules.
- [[agent-eval]] — Skill·에이전트 검증 테스트. JSON cases + harness + CI 회귀방지.
- [[meta-prompt]] — Prompt를 생성하는 상위 프롬프트. Reasoning-before-conclusions.
- [[token-maxxing]] — 토큰 사용량 과시 문화와 붕괴. 토성비·outcome 평가로 전환.
- [[model-spec]] — 모델 행동 공개 프레임워크. Hierarchy + hard rules vs defaults.
- [[design-md]] — AI용 plain-text design system. AGENTS.md와 역할 분리.
- [[ai-native-sdlc]] — AI-native 소프트웨어 생명주기. Artifact chain loop.

## Topics

- [[context-engineering-guide]] — 5개 context 소스 종합 실전 가이드. 이론→실측→규칙→操作.
- [[agent-skills-eval-loop]] — Skill 작성→eval→improver→CI 종합 루프.
- [[ai-coding-workflow]] — Engineering·검증·비용 3축 종합. 새 병목과 측정법.
- [[agent-docs-pattern]] — AGENTS·CLAUDE·SKILL·DESIGN·Intent 문서 역할 분담 패턴.
