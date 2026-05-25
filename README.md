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



## License

Private
