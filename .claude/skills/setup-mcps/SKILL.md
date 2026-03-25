---
name: setup-mcps
description: 팀에서 사용하는 MCP 서버(Figma, Slack, Atlassian, Notion)를 한번에 설치한다. "MCP 설치", "MCP 셋업", "MCP 세팅", "MCP 한번에 설치", "setup mcps" 등의 요청에 트리거된다.
---

# MCP 일괄 설치 스킬

팀에서 사용하는 4개의 MCP 서버를 한번에 설치한다.

## 설치할 MCP 목록

| MCP | 연결 대상 | 전송 방식 |
|-----|----------|----------|
| Figma | Figma 디자인 파일 | HTTP (OAuth) |
| Slack | Slack 워크스페이스 | HTTP (OAuth) |
| Atlassian | Jira, Confluence | SSE (OAuth) |
| Notion | Notion 워크스페이스 | HTTP (OAuth) |

## 실행 절차

아래 명령어들을 **Bash 도구로 순서대로 실행**한다.

### 1단계: 기존 설치 확인

먼저 이미 설치된 MCP가 있는지 확인한다.

```bash
claude mcp list
```

이미 설치된 MCP는 건너뛴다. 아래 4개 중 설치되지 않은 것만 설치한다.

### 2단계: MCP 설치

각 MCP를 `claude mcp add` 명령어로 설치한다. **`-s user` 옵션**을 사용하여 모든 프로젝트에서 사용 가능하도록 한다.

#### Figma MCP
```bash
claude mcp add figma -s user --transport http https://mcp.figma.com/mcp
```

#### Slack MCP
```bash
claude mcp add slack -s user --transport http https://mcp.slack.com/mcp
```

#### Atlassian MCP (Jira + Confluence)
```bash
claude mcp add atlassian -s user --transport sse https://mcp.atlassian.com/v1/sse
```

#### Notion MCP
```bash
claude mcp add notion -s user --transport http https://mcp.notion.com/mcp
```

### 3단계: 설치 확인

설치가 완료되면 전체 목록을 확인한다.

```bash
claude mcp list
```

### 4단계: 인증 안내

사용자에게 다음 안내를 출력한다:

---

**MCP 설치가 완료되었습니다!**

각 MCP는 처음 사용할 때 OAuth 인증이 필요합니다. 아래처럼 진행하세요:

1. **Claude Code를 재시작**합니다 (터미널에서 `claude` 다시 실행)
2. 각 MCP를 처음 사용하면 **브라우저가 열리며 로그인**을 요청합니다
3. 로그인하면 자동으로 연결됩니다

| MCP | 인증 방법 | 필요한 계정 |
|-----|----------|------------|
| Figma | 브라우저 OAuth | Figma 계정 |
| Slack | 브라우저 OAuth | Slack 워크스페이스 계정 |
| Atlassian | 브라우저 OAuth | Atlassian 계정 |
| Notion | 브라우저 OAuth | Notion 계정 |

**테스트 예시:**
- `Figma 파일 목록 보여줘` → Figma MCP 테스트
- `Slack 채널 목록 보여줘` → Slack MCP 테스트
- `Jira 프로젝트 목록 보여줘` → Atlassian MCP 테스트
- `Notion에서 최근 페이지 검색해줘` → Notion MCP 테스트

---

## 주의사항

- 이미 설치된 MCP는 **건너뛴다** (중복 설치 방지)
- 설치 중 에러가 발생하면 해당 MCP만 건너뛰고 나머지를 계속 설치한다
- 모든 MCP는 `-s user` 스코프로 설치하여 **모든 프로젝트에서 공통 사용** 가능하다
