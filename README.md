# Sidekick 설치 파일

Sidekick은 Claude Code, Codex, Google AI(Antigravity)를 한 창에서 사용하는 Windows 11용 사이드바입니다. 각 AI의 공식 엔진을 그대로 쓰며, 로그인과 모델, MCP 서버, 플러그인, 대화 기록을 공식 앱과 공유합니다. Android 휴대폰 앱으로 PC의 대화를 이어서 쓸 수도 있습니다.

This repository hosts the installers for Sidekick, a Windows 11 sidebar that runs Claude Code, Codex and Google AI with their official engines; the source code and full description are at [Lian-CrescentMoon/sidekick](https://github.com/Lian-CrescentMoon/sidekick).

## 설치

[최신 릴리스](https://github.com/Lian-CrescentMoon/sidekick-releases/releases/latest)에서 운영체제에 맞는 파일을 받으세요.

- **Windows 11:** `Sidekick-Setup-<버전>.exe`를 실행합니다. 관리자 권한 없이 설치되며, 설정 > 앱에서 제거합니다.
- **Linux arm64(라즈베리파이 5 등):** `sudo apt install ./sidekick_<버전>_arm64.deb`
- **Linux x64:** `sidekick_<버전>_amd64.deb` 또는 `tar.gz`
- **Android(휴대폰 원격):** `SidekickRemote-<버전>.apk`를 휴대폰에서 열어 설치합니다.

`SHA256SUMS.txt`로 받은 파일의 해시를 확인할 수 있습니다.

사용하려는 AI의 공식 앱이나 CLI(Claude 데스크톱 앱 또는 Claude Code CLI, Codex 앱 또는 Codex CLI, Antigravity CLI 1.3.1 이상)를 먼저 설치하고 로그인해 두세요. Sidekick은 그 로그인 상태를 그대로 사용합니다.

## 업데이트

- **PC:** 설치한 Sidekick이 새 버전을 스스로 받아 설치합니다. 업데이트 파일은 서명을 확인한 뒤 사용합니다. 설정 > 업데이트에서 자동 설치를 끄거나 지금 확인할 수 있습니다.
- **휴대폰:** 앱이 연결된 PC나 이 저장소에서 새 APK를 받아 다운로드 폴더에 저장합니다. 받은 파일을 직접 열어 설치합니다.

## 소스와 자세한 설명

기능 설명, 휴대폰 연결 방법, 직접 빌드하는 방법은 소스 저장소 [Lian-CrescentMoon/sidekick](https://github.com/Lian-CrescentMoon/sidekick)의 [README](https://github.com/Lian-CrescentMoon/sidekick#readme)를 참고하세요. 라이선스는 MIT입니다.
