# LLM Wiki — Personal Knowledge Management

개인 지식 베이스를 LLM이 구축하고 유지보수합니다. 소스를 모으면 LLM이 정리된 위키로 만듭니다.

## 빠른 시작

1. `diki/`를 Obsidian vault로 엽니다
2. `raw/articles/`, `raw/papers/`, `raw/notes/` 에 소스 파일을 넣습니다
3. LLM에게 ingest를 요청합니다
4. Obsidian에서 위키를 탐색합니다

## 구조

```
diki/
├── AGENTS.md           ← 위키 스키마 (OpenCode 설정)
├── raw/                ← 원본 소스 (이곳에 추가)
│   ├── articles/
│   ├── papers/
│   ├── notes/
│   └── assets/
├── wiki/               ← LLM이 생성한 페이지 (한국어+영어)
│   ├── index.md        ← 전체 카탈로그
│   ├── log.md          ← 작업 이력
│   ├── overview.md     ← 시작 페이지
│   ├── entities/
│   ├── concepts/
│   ├── sources/
│   └── topics/
└── quartz/             ← 정적 사이트 빌더
    └── content → ../wiki (심볼릭 링크)
```

## 워크플로우

- **Ingest**: 소스 추가 → LLM이 요약, 교차참조, 인덱스 업데이트
- **Query**: 질문 → LLM이 위키 검색 후 답변 종합
- **Lint**: 건강검진 → 모순, 고아페이지, stale 콘텐츠, 빠진 링크 발견

## 배포 (GitHub Pages)

위키를 웹사이트로 배포합니다.

### 로컬 미리보기

```bash
cd quartz
npm ci
npx quartz plugin install --from-config
npx quartz build --serve
```

http://localhost:8080 에서 확인 가능.

### GitHub Pages 배포

1. GitHub에 repo를 push합니다
2. Settings → Pages → Source를 "GitHub Actions"로 설정합니다
3. `git push` 하면 자동으로 빌드 및 배포됩니다

## 설정

- `AGENTS.md`: 위키 스키마와 LLM 동작 정의
- `quartz/quartz.config.yaml`: 사이트 설정 (제목, 테마, 플러그인)
