# Claude Code 온보딩

비개발 직군(PM, 디자이너, QA)을 위한 Claude Code 온보딩 자료와 스킬 모음입니다.

## 포함된 스킬

### `setup-mcps` — MCP 일괄 설치

팀에서 사용하는 4개의 MCP를 한번에 설치합니다:

| MCP | 연결 대상 |
|-----|----------|
| **Figma** | Figma 디자인 파일 분석 |
| **Slack** | Slack 메시지 전송/요약 |
| **Atlassian** | Jira 티켓, Confluence 문서 |
| **Notion** | Notion 페이지 검색/생성 |

### 사용 방법

#### 방법 1: 이 저장소를 클론하여 사용

```bash
git clone https://github.com/DevCHW/claude-onboarding.git
cd claude-onboarding
claude
```

Claude Code에서:
```
MCP 설치해줘
```

#### 방법 2: 기존 프로젝트에 스킬만 복사

```bash
# 기존 프로젝트 디렉토리에서
mkdir -p .claude/skills/setup-mcps
curl -o .claude/skills/setup-mcps/SKILL.md \
  https://raw.githubusercontent.com/DevCHW/claude-onboarding/main/.claude/skills/setup-mcps/SKILL.md
```

#### 방법 3: 수동 설치 (스킬 없이)

```bash
claude mcp add figma -s user --transport http https://mcp.figma.com/mcp
claude mcp add slack -s user --transport http https://mcp.slack.com/mcp
claude mcp add atlassian -s user --transport sse https://mcp.atlassian.com/v1/sse
claude mcp add notion -s user --transport http https://mcp.notion.com/mcp
```

### 설치 후

1. Claude Code를 재시작합니다
2. 각 MCP를 처음 사용할 때 브라우저에서 OAuth 로그인이 열립니다
3. 로그인하면 자동으로 연결됩니다

## 라이선스

MIT
