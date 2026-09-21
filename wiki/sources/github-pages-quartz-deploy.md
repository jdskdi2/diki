---
title: "GitHub Pages + Quartz 배포 가이드"
created: 2026-07-03
updated: 2026-07-03
tags: [source, knowledge-management, pkm, github, quartz]
sources: [raw/articles/llm-wiki.md]
aliases: ["Quartz Deploy Guide", "GitHub Pages Setup"]
---

# GitHub Pages + Quartz 배포 가이드

Obsidian vault를 Quartz로 정적 사이트로 변환하고 GitHub Pages에 배포하는 전체 과정.

## 목표

- LLM이 유지보수하는 PKM 위키를 웹사이트로 공개
- `git push` 한 번으로 자동 빌드 및 배포
- 무료, 서버 관리 불필요

## 배포 구조

```
diki/                          ← Obsidian vault + Quartz 프로젝트
├── wiki/                      ← LLM이 관리하는 위키 페이지
├── quartz/
│   ├── content → ../wiki      ← 심볼릭 링크 (wiki를 Quartz가 읽음)
│   ├── quartz.config.yaml     ← 사이트 설정
│   └── public/                ← 빌드 결과물 (git 제외)
├── .github/workflows/
│   └── deploy.yml             ← GitHub Actions 자동 배포
└── .gitignore
```

## 단계별 과정

### 1단계: Quartz 설치

```bash
# Quartz 클론
git clone https://github.com/jackyzha0/quartz.git quartz
cd quartz

# 의존성 설치
npm i

# 플러그인 설치
npx quartz plugin install --from-config
```

**Quartz란?**
- Obsidian markdown을 정적 사이트로 변환하는 빌드 도구
- wikilinks, graph view, backlinks, search를 기본 지원
- Node.js v22 이상 필요

### 2단계: 심볼릭 링크 설정

```powershell
# Windows (PowerShell)
Remove-Item -Recurse -Force "content"
New-Item -ItemType Junction -Path "content" -Target "..\wiki"

# Linux/macOS
rm -rf content
ln -s ../wiki content
```

**왜 심볼릭 링크인가?**
- 파일이 한 곳(`wiki/`)에만 존재
- Obsidian에서 편집하면 Quartz 빌드에 즉시 반영
- 동기화 불일치 문제 없음

**GitHub Actions에서의 동작:**
- Ubuntu runner에서는 심볼릭 링크가 기본적으로 동작
- `git clone` 시 심볼릭 링크가 올바르게 복원됨

### 3단계: 설정 파일 작성

`quartz/quartz.config.yaml` 주요 설정:

```yaml
configuration:
  pageTitle: diki
  pageTitleSuffix: " — PKM Wiki"
  locale: ko-KR
  baseUrl: "doo.github.io/diki"    # GitHub Pages URL
  ignorePatterns:
    - private
    - templates
    - .obsidian
```

**주요 플러그인:**
- `obsidian-flavored-markdown` — Obsidian 문법 지원
- `graph` — 노트 간 연결 시각화
- `backlinks` — 백링크 표시
- `search` — 전문 검색
- `tag-page` — 태그별 페이지 생성
- `content-index` — 사이트맵, RSS 생성

### 4단계: 로컬 빌드 테스트

```bash
cd quartz
npx quartz build --serve
# http://localhost:8080 에서 확인
```

**빌드 출력:**
- 8개 markdown 입력 → 112개 HTML 파일 출력
- `public/` 폴더에 생성

### 5단계: GitHub Actions workflow

`.github/workflows/deploy.yml` 전체 코드:

```yaml
name: Deploy Quartz site to GitHub Pages

on:
  push:
    branches:
      - main

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0
      - uses: actions/setup-node@v4
        with:
          node-version: 22
      - name: Install Quartz dependencies
        working-directory: quartz
        run: npm ci
      - name: Install plugins
        working-directory: quartz
        run: npx quartz plugin install --from-config
      - name: Build Quartz
        working-directory: quartz
        run: npx quartz build
      - uses: actions/upload-pages-artifact@v3
        with:
          path: quartz/public

  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

#### 설정 항목 설명

| 설정 | 값 | 설명 |
|------|-----|------|
| `on.push.branches` | `main` | main 브랜치 push 시 트리거 |
| `permissions.contents` | `read` | repo 코드 읽기 권한 |
| `permissions.pages` | `write` | GitHub Pages 쓰기 권한 |
| `permissions.id-token` | `write` | GitHub Pages 인증용 OIDC 토큰 (누락 시 403) |
| `concurrency.group` | `"pages"` | 동일 배포 작업 그룹핑 |
| `concurrency.cancel-in-progress` | `false` | 기존 배포 완료까지 대기 |
| `fetch-depth` | `0` | 전체 git 히스토리 fetch (날짜 메타데이터용) |
| `node-version` | `22` | Quartz 최소 요구 버전 |
| `working-directory` | `quartz` | 빌드 작업 디렉토리 |
| `npm ci` | - | `package-lock.json` 기반 정확한 설치 |
| `upload-pages-artifact` | `quartz/public` | 빌드 결과물을 artifact로 업로드 |
| `deploy-pages` | `v4` | artifact를 실제 Pages에 배포 |

#### 동작 흐름

```
git push origin main
        │
        ▼
┌─────────────────────┐
│ GitHub Actions 시작  │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│ build job           │
│  1. checkout        │
│  2. node setup      │
│  3. npm ci          │
│  4. plugin install  │
│  5. quartz build    │
│  6. upload artifact │
└─────────┬───────────┘
          │ (성공 시)
          ▼
┌─────────────────────┐
│ deploy job          │
│  1. deploy-pages    │
│  2. URL 할당        │
└─────────┬───────────┘
          │
          ▼
https://jdskdi2.github.io/diki/
```

#### GitHub Actions 핵심 개념

- **Workflow**: `.github/workflows/*.yml` 파일 하나 = 하나의 자동화 파이프라인
- **Job**: workflow 내의 독립 실행 단계. `build` → `deploy` 순서대로 실행
- **Step**: job 내의 개별 명령어. `uses`(외부 액션) 또는 `run`(셸 명령)
- **Runner**: GitHub가 제공하는 가상머신. 내 서버 불필요
- **Artifact**: job 간 파일 전달 수단. build 결과물을 deploy에 전달
- **Environment**: 배포 대상. `github-pages`는 GitHub가 관리하는 호스팅 환경

#### `npm ci` vs `npm install`

| | `npm ci` | `npm install` |
|---|---------|--------------|
| 기준 파일 | `package-lock.json` | `package.json` |
| 동작 | lock 파일을 정확히 따름 | 의존성 해결 후 lock 업데이트 가능 |
| 속도 | 빠름 | 느림 |
| 사용 상황 | CI/CD (재현성 중요) | 개발 환경 |

### 6단계: GitHub 설정

1. GitHub repo 생성 또는 기존 repo 사용
2. **Settings → Pages → Source: "GitHub Actions"** 선택
3. Git push → 자동 배포

**URL:** `https://jdskdi2.github.io/diki/`

### 7단계: 배포 확인

- **Actions** 탭에서 빌드 진행상황 확인
- 빌드 성공 시 자동으로 Pages에 반영
- 빌드 시간: 약 60-90초

## 핵심 개념 정리

### GitHub Pages란?

- GitHub가 무료로 제공하는 정적 사이트 호스팅
- Public repo: 무제한 무료
- Private repo: 월 2,000분 무료 (Linux runner 기준)
- runner 서버 구축 불필요 — GitHub가 알아서 가상머신 할당

### GitHub Actions란?

- `git push` 시 자동으로 빌드/테스트/배포를 실행하는 CI/CD 도구
- `.github/workflows/` 폴더에 YAML 파일로 정의
- GitHub가 Ubuntu 가상머신을 알아서 띄우고, 빌드 후 닫음
- 내 컴퓨터와 무관하게 동작

### 심볼릭 링크 vs 직접 복사

| | 심볼릭 링크 | 직접 복사 |
|---|---|---|
| 파일 위치 | 한 곳 (`wiki/`) | 두 곳 (`wiki/` + `quartz/content/`) |
| 동기화 | 자동 (동일 파일 참조) | 수동 또는 스크립트 |
| GitHub Actions | 보통 동작 | 항상 동작 |
| 복잡도 | 낮음 | 높음 |

### Quartz 플러그인 구조

```
plugins:
  transformers: [...]  → 콘텐츠 변환 (frontmatter, 마크다운 파싱)
  filters: [...]       → 콘텐츠 필터링 (draft 제거)
  emitters: [...]      → 파일 생성 (HTML, 사이트맵, RSS)
```

## 관련 페이지

- [[obsidian]] — 위키를 탐색하는 도구
- [[llm-wiki-karpathy]] — LLM Wiki 패턴 원본
