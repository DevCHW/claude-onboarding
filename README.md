# setup-mcps

Figma, Slack, Atlassian(Jira/Confluence), Notion MCP를 한번에 설치하는 Claude Code 플러그인입니다.

## 설치

```bash
/plugin install setup-mcps@DevCHW/claude-onboarding
```

또는 Claude Code에서 `/plugin` → Discover에서 검색

## 사용

설치 후 Claude Code에서:

```
MCP 설치해줘
```

또는

```
/setup-mcps
```

## 포함된 MCP

| MCP | 연결 대상 | 할 수 있는 일 |
|-----|----------|-------------|
| **Figma** | Figma | 디자인 파일 분석, 컴포넌트 구조 파악 |
| **Slack** | Slack | 메시지 전송, 스레드 요약 |
| **Atlassian** | Jira, Confluence | 티켓 조회/생성, 문서 작성/수정 |
| **Notion** | Notion | 페이지 생성/수정, 검색 |

## 설치 후

1. Claude Code를 재시작합니다
2. 각 MCP를 처음 사용할 때 브라우저에서 OAuth 로그인이 열립니다
3. 로그인하면 자동으로 연결됩니다

## 수동 설치 (플러그인 없이)

```bash
claude mcp add figma -s user --transport http https://mcp.figma.com/mcp
claude mcp add slack -s user --transport http https://mcp.slack.com/mcp
claude mcp add atlassian -s user --transport sse https://mcp.atlassian.com/v1/sse
claude mcp add notion -s user --transport http https://mcp.notion.com/mcp
```

## 라이선스

MIT
