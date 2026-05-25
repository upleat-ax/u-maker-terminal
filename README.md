# U-MAKER Terminal

> **AI 시대를 위해 다시 설계된 터미널** — Claude Code · Codex · Cursor 같은 AI 코딩 에이전트를 한 곳에서, 더 빠르고, 더 똑똑하게.

기존 터미널은 *사람이 직접 명령을 입력한다*는 전제로 만들어졌습니다.
하지만 지금 우리는 AI 에이전트가 코드를 쓰고, PR을 올리고, 문서와 다이어그램을 생성하는 시대를 살고 있습니다.
U-MAKER Terminal 은 이 새로운 워크플로우 위에서 다시 설계된, **macOS · Windows 크로스플랫폼 터미널 에뮬레이터** 입니다.

## Install

Download the latest installer from the [Releases page](https://github.com/upleat-ax/u-maker-terminal/releases/latest):

| Platform | Asset |
|---|---|
| macOS (Universal — Intel & Apple Silicon) | `u-maker_<version>_universal.dmg` |
| Windows 10 / 11 (x64) — NSIS installer | `u-maker_<version>_x64-setup.exe` |
| Windows 10 / 11 (x64) — MSI installer | `u-maker_<version>_x64_en-US.msi` |

설치 후 별도 업데이트 작업은 필요 없습니다. 새 버전은 백그라운드에서 자동 다운로드되어, 재시작 시 적용됩니다 (`tauri-plugin-updater`).

---

## AI 개발에 특화된 핵심 기능

### 🪄 LLM 기반 명령어 자동완성

타이핑 중인 prefix, 현재 작업 디렉토리, 그리고 최근 실행한 명령 기록을 컨텍스트로 LLM이 **이어질 명령을 회색 텍스트로 미리** 보여줍니다.
Tab 한 번이면 그대로 채워집니다.

- **OpenRouter API 키 한 줄**만 설정하면 동작 (기본 모델: `gpt-4o-mini`, 향후 모델 교체는 OpenRouter 게이트웨이를 통해 확장 가능).
- 800ms 디바운스 + 로컬 캐시로 비용/지연 최소화.
- 디렉토리별 명령 히스토리 학습 → 같은 폴더에서 자주 쓰던 패턴을 우선 추천 (글로벌 집계 fallback).

> *"`git checkout `" 까지만 쳐도 자주 쓰는 브랜치를 그대로 제안.*
> *프로젝트별로 다른 빌드 명령, 테스트 명령도 알아서 학습.*

### 📊 Claude 주간 한도 실시간 모니터링 *(macOS 전용)*

StatusBar 우측에 **현재 주의 Claude 사용률 (Wk %)** 이 항상 떠 있습니다.

- macOS Keychain에 저장된 Claude Code OAuth 토큰을 자동으로 읽어 Anthropic Usage API에 조회 — **별도 설정 없이** 동작.
- 60초마다 자동 갱신.
- Opus 4.x 를 거침없이 들이부을 때, *남은 페이스를 한 눈에 보면서* 조절할 수 있습니다.

> Windows 빌드에서는 토큰 저장 경로가 달라 현재 표시되지 않습니다 (향후 지원 예정).

### 📄 AI 산출물을 위한 통합 뷰어

AI 에이전트는 코드만 만들지 않습니다. 마크다운, Mermaid 다이어그램, OpenAPI 스펙, 스프레드시트, 이미지까지 — 다양한 산출물을 쏟아냅니다.
U-MAKER Terminal 은 **모든 주요 포맷을 터미널 안에서 그대로** 보여줍니다.

| 포맷 | 지원 형태 |
|---|---|
| **Markdown** | GFM + Mermaid 다이어그램 자동 렌더 + 풍부한 코드 하이라이트 |
| **OpenAPI / Swagger** | YAML·JSON 자동 감지, 엔드포인트별 시각화 |
| **Diff** | AI 가 만든 변경분 사이드-바이-사이드 검토 |
| **소스 코드** | Monaco Editor (VS Code 동일 엔진) — 신택스 하이라이트 · 폴딩 · 멀티커서 |
| **JSON** | 트리뷰 + 컬러 하이라이트 |
| **이미지 / 비디오** | 인라인 프리뷰 + 트랙패드 핀치 줌 |
| **Word (.docx) / Excel (.xlsx)** | 네이티브 미리보기 — 변환 도구 따로 안 띄워도 됨 |
| **PDF** | 핀치 줌 지원 인라인 프리뷰 |

별도 IDE 나 외부 뷰어로 빠져나갈 필요가 없습니다. **AI ↔ 검토 ↔ 다음 명령** 의 사이클이 한 화면 안에서 끊김 없이 돕니다.

### 🪟 멀티 AI 세션 동시 운영

- **탭** + **수평/수직 분할 패널**로 여러 AI CLI를 나란히 띄울 수 있습니다.
  *왼쪽엔 Claude Code, 오른쪽엔 Codex, 아래엔 로그 모니터 — 한 화면에서.*
- **워크스페이스 탭** — 여러 프로젝트를 동시에 열어두고 컨텍스트 전환 비용을 없앱니다.
- 세션마다 독립적인 PTY · CWD · 셸 환경 유지.

### 🌿 Git · PR 워크플로우 통합

AI 가 자주 만드는 결과물은 결국 **PR** 입니다. U-MAKER Terminal 은 PR 중심 워크플로우에 최적화되어 있습니다.

- **사이드바**: Staged / Changes / Stashes / **Worktrees** 실시간 표시 + 드래그앤드롭 파일 이동
- **StatusBar**: 현재 브랜치 · dirty 상태 · 열린 PR 수를 한눈에
- **GitPanel**: 상태바 클릭만으로 git 변경 내역 패널 즉시 호출
- **PrPanel**: GitHub / GitLab 열린 PR 목록과 상세를 **터미널 안에서** 확인 (브라우저 왕복 X)
- **한글 파일명 등 비-ASCII 경로** 정상 처리 (`git -c core.quotepath=false` 자동화)

### 🧩 `.u-maker` 프로젝트 통합

`.u-maker/` 폴더가 있는 프로젝트는 사이드바에서 **전용 아이콘**으로 강조 표시됩니다.
[u-maker](https://github.com/upleat-ax/u-maker) PBGD (**Plan → Build → Gatekeeping → Deploy**) 파이프라인과 결합하면, **기획서 작성부터 코드 생성, 품질 검수, 배포까지** 별도 IDE 없이 터미널 하나로 끝낼 수 있습니다.

---

## 그 밖의 강력한 기능들

- **탭 색상 라벨** — 워크스페이스 탭마다 우클릭 컨텍스트 메뉴에서 8가지 색상 지정 가능, 워크스페이스별 영구 저장
- **워크스페이스 검색** — 대규모 모노레포에서도 AI 가 만든 함수/문자열을 즉시 검색
- **Quick Open** (`Cmd+P` / `Ctrl+P`) — VS Code 식 파일 빠른 열기
- **SSH 원격 접속** — 호스트 저장 + 키/패스워드 인증, **vi · tmux 풀스크린에서도 사이즈 깨짐 없음**
- **워크스페이스 캐시** + 리로드 버튼 — 대형 트리도 부팅 즉각
- **터미널 내 검색 오버레이** — 출력 결과에서 텍스트 빠르게 찾기 (`@xterm/addon-search`)
- **LSP 지원** — Language Server Protocol 연동으로 에디터 컨텍스트 보강
- **테마 · 폰트 · 키바인딩 커스터마이즈** — 설정 모달에서 즉시 변경
- **네이티브 클립보드 연동** — OS 클립보드와 1:1 동기화
- **자동 업데이트** — `tauri-plugin-updater` 로 무중단 업데이트

---

## 왜 Tauri 인가? — 사용자 관점의 이점

내부 구현이 아닌 사용자가 체감하는 가치 측면에서:

- **가벼움** — Electron 대비 메모리/디스크 사용량이 현저히 낮습니다. 백그라운드에 항상 띄워두기 부담 없음.
- **빠른 부팅** — Rust 네이티브 백엔드로 시작 시간이 짧습니다.
- **OS 통합** — 네이티브 메뉴, 알림, 클립보드, 자동 업데이트가 OS 표준 방식대로 동작.
- **안전한 IPC** — 프론트엔드와 백엔드 간 호출이 명시적으로 정의되어 있어, 예측 가능한 동작과 권한 모델.

---

## For Developers

이 저장소는 공개되어 있지만, 라이선스는 비공개(Private) 상태입니다. 빌드된 바이너리는 자유롭게 다운로드/사용 가능합니다.

### Prerequisites

- [Bun](https://bun.sh/) ≥ 1.2.0
- [Node.js](https://nodejs.org/) ≥ 20.0.0
- [Rust](https://www.rust-lang.org/tools/install) (Tauri 빌드용)
- macOS 13.0+ **또는** Windows 10/11 (x64) + [WebView2 Runtime](https://developer.microsoft.com/en-us/microsoft-edge/webview2/)

### Getting Started

```bash
bun install          # 의존성 설치
bun run dev          # 개발 모드 (프론트 + Tauri 동시 기동)
bun run build        # 프로덕션 빌드
```

### Scripts

| Command | Description |
|---------|-------------|
| `bun run dev` | Start Tauri dev (frontend + backend) |
| `bun run build` | Build all packages and the Tauri app |
| `bun run lint` | Lint all packages |
| `bun run type-check` | Run TypeScript type checking |
| `bun run storybook` | Launch Storybook |
| `bun run clean` | Clean build artifacts |

### Tech Stack (요약)

React 18 + TypeScript + Vite · Rust (Tauri v2) + portable-pty · xterm.js · Monaco Editor · Zustand + React Query · Turborepo + Bun workspaces

---

## License

Private. (Release binaries are freely downloadable from the Releases page.)
