# U-MAKER Terminal

A macOS terminal emulator built with [xterm.js](https://xtermjs.org/) and [Tauri v2](https://v2.tauri.app/).

## Features

- **Multi-tab / Multi-session** — 탭 기반 터미널 세션 관리 (생성, 분할, 전환)
- **Split Panel** — 수평/수직 분할 패널 지원
- **File Viewer** — 코드 에디터 (Monaco), Markdown, JSON, OpenAPI, Mermaid, Diff 뷰어 내장
- **Workspace Search** — 워크스페이스 내 파일/코드 검색
- **Git Integration** — Git 상태 표시, PR/MR 패널 (GitHub / GitLab)
- **Settings** — 터미널 테마, 폰트, 키바인딩 등 설정
- **Clipboard** — 네이티브 클립보드 연동
- **Auto Update** — 앱 자동 업데이트 (tauri-plugin-updater)
- **LSP** — Language Server Protocol 지원

## Tech Stack

- **Frontend**: React 18 + TypeScript + Vite
- **Backend**: Rust (Tauri v2) + portable-pty
- **Terminal**: xterm.js (fit, search, serialize, unicode11, web-links, canvas addons)
- **Editor**: Monaco Editor
- **State**: Zustand + React Query
- **UI**: CSS Modules + Storybook 8
- **Monorepo**: Turborepo + Bun workspaces

## Project Structure

```
apps/
  terminal/                   # Tauri desktop app
    src/
      components/
        FileViewer/           # CodeEditor, MarkdownViewer, OpenApiViewer, DiffViewer, MermaidBlock, JsonHighlight
        LoginModal/           # M7 로그인 모달
        SearchOverlay/        # 터미널 내 검색 오버레이
        SettingsModal/        # 설정 모달
        Sidebar/              # 사이드바
        SplitPanel/           # 분할 패널
        StatusBar/            # 상태바 (Git, PR 패널)
        TabBar/               # 탭바
        TerminalView/         # xterm.js 터미널 뷰
        WorkspaceSearch/      # 워크스페이스 검색
        WorkspaceTabBar/      # 워크스페이스 탭바
      hooks/                  # useTerminal, useIPC, usePtyOutput, useWorkspaceRepoStatus
      stores/                 # Zustand stores (auth, config, panel, session, tab, fileEditor, workspaceSession)
    src-tauri/
      src/
        commands/             # Tauri IPC commands
          clipboard_commands  # 클립보드
          config_commands     # 설정
          git_commands        # Git 연동
          lsp_commands        # LSP
          pty_commands        # PTY 세션
          search_commands     # 검색
          session_commands    # 세션 관리
          update_commands     # 자동 업데이트
          usage_commands      # 사용량
        config.rs             # 설정 관리
        error.rs              # 에러 처리
        lsp.rs                # LSP 클라이언트
        menu.rs               # 네이티브 메뉴
        pty.rs                # PTY 프로세스 관리
        session.rs            # 세션 상태
packages/
  types/                      # 공유 TypeScript 타입 (config, events, session, commands, ipc, lsp)
  ui/                         # 공유 UI 컴포넌트 라이브러리 (Button, Input)
  infrastructure/
    m7-client/                # M7 API 클라이언트 (Clean Architecture: domain → infrastructure → hooks)
```

## Prerequisites

- [Bun](https://bun.sh/) >= 1.2.0
- [Node.js](https://nodejs.org/) >= 20.0.0
- [Rust](https://www.rust-lang.org/tools/install) (for Tauri)
- macOS 13.0+

## Getting Started

```bash
# Install dependencies
bun install

# Run in development mode
bun run dev

# Build for production
bun run build
```

## Scripts

| Command | Description |
|---------|-------------|
| `bun run dev` | Start Tauri dev (frontend + backend) |
| `bun run build` | Build all packages and Tauri app |
| `bun run lint` | Lint all packages |
| `bun run type-check` | Run TypeScript type checking |
| `bun run storybook` | Launch Storybook |
| `bun run clean` | Clean build artifacts |

## License

Private
