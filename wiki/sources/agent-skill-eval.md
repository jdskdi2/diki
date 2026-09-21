---
title: "이밸 없이 에이전트 스킬을 배포하지 마라"
created: 2026-09-21
updated: 2026-09-21
tags: [source, ai, llm]
sources: [Clippings/이밸 없이 에이전트 스킬을 배포하지 마라.md]
aliases: ["No Eval No Deploy", "Agent Skill Eval"]
---

# 이밸 없이 에이전트 스킬을 배포하지 마라

[[philipp-schmid]] (Google DeepMind) 강연 정리 글. Agent가 non-deterministic하기 때문에 skill을 문서가 아니라 eval + CI/regression으로 관리되는 소프트웨어 자산으로 다뤄야 한다고 주장한다.

원문: https://wikidocs.net/blog/@jaehong/24001/ (박재홍 정리)

## 핵심 주장

Skill이 나쁜지 task가 어려운지 구분 불가 → File 2개(JSON test cases + Python harness)와 cheap한 regex assert만으로 시작 가능. 진짜 자산은 버려지는 skill이 아니라 남는 eval이다 ("이밸이 스킬보다 오래 산다").

## 주요 내용

- **현실 진단**: SkillBench가 5만+ skill 색인했으나 eval 갖춘 것은 거의 없음. 실패 시 skill 미발동 vs skill 오류 vs 모델 한계 구분 불가.
- **효과는 입증됨**: SkillBench 1.1 (100여 과제) 기준 skill 평균 약 15% 성능 향상. 단 사람 작성 skill이 최고, AI 생성 skill은 오히려 하락 가능. `SKILL.md 500줄` 초과 = 리팩토링 신호.
- **핵심 구분**: 우리가 쓰는 에이전트 (Cursor/Claude Code, 인간이 안전망, slash 강제 발동 가능) vs 우리가 만드는 에이전트 (고객용, model-invoked만 존재 → eval 필수).
- **Skill 구조 = [[progressive-disclosure]] 3겹**: title+description (항상 context, trigger 판단) → SKILL.md 본문 (통째로 context) → 참조 파일들 (필요시 탐색). 종류: capability skill (한시적) vs preference skill (오래감, regression 보호).
- **좋은 skill 7원칙**: description에 why/when/how + 부정 케이스 / 에세이가 아닌 directive / 얇게 + 참조 분리 (description은 매 호출 100~200 token 비용) / 절차 못박지 말고 목표·제약만 / no-op 제거 / 주기적 폐기 판단.
- **실전 사례 (Gemini Interactions API)**: 학습 cutoff 이후 신 API라 모델이 구방식으로 생성 → 117개 테스트 케이스 → 유효 코드 생성률 약 90%. 자산은 JSON cases + Python script (Gemini CLI 실행 + regex assert). LLM as judge는 복잡한 경우+rubric만.
- **월요일 숙제**: 최다 사용 skill 1개 골라 prompt 5개 작성, 10~20개로 작게 시작 (happy 5 + negative 5), 격리 clean workspace, 케이스당 5~6회 반복, ablation (on/off 비교), skill diff → eval 자동 실행·병합 차단.

## 관련 페이지

- [[agent-skills]] — skill 구조와 작성 원칙
- [[agent-eval]] — eval·harness·CI 개념
- [[progressive-disclosure]] — 3겹 구조 원칙
- [[philipp-schmid]] — 원강연자
- [[warp-self-improving-agents]] — self-improvement loop 동반 소스
- [[agent-skills-eval-loop]] — 종합 토픽
