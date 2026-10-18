# Sidekick

[한국어](README.md)

A Windows 11 sidebar for Claude Code, Codex and Google AI (Antigravity) in one window. Sidekick is not a new AI engine: it starts the engines that ship with each vendor's official app and only replaces the window around them. Sign-in, models, MCP servers, plugins and conversation history are the same ones the official apps use.

![Main window — conversations grouped by folder and the changes (git diff) panel](docs/screenshots/main-light.png)

Main window: conversations grouped by folder, with the files the AI changed shown in the changes panel. The title bar shows the remaining usage; suggested replies sit above the input.

## What it does

### One conversation, several AIs

- **Claude, Codex and Google AI in one conversation.** You can switch AI mid-conversation. A finished Claude or Codex turn is appended to the other side's official history, so you can keep going in the official apps too. Google AI conversations continue in Sidekick.
- **Nothing left out when switching.** The AI you switch to gets everything it has not seen yet, in full; what it already saw is not sent again. Above a size you set, only the recent messages go inline and the full history is passed as a file.
- **Official engines.** Sign-in, model lists, MCP servers, plugins and slash commands are shared with the official apps. Skills in the chosen working folder come first in the `/` list. For Claude account plugins you choose in settings whether to pass everything, only skills and commands, or nothing.
- **Settings in the input bar.** Pick the AI, model, reasoning level, permission mode and working folder. The model menu also shows your plan and remaining usage. For Claude, the reasoning button can turn on workflows; the ⚡ button turns on fast mode, which switches off when you close the window or change conversation.
- **Auto model and reasoning.** Set to **Auto** and Sidekick picks them per turn from how hard the task is; the choice is recorded in an "Auto" step in the answer. Whether an ongoing conversation may change model is a setting: keep, don't keep, or compact then switch. "Compact then switch" compacts the conversation with the previous model before sending with the new one (Claude, Codex).
- **Autopilot.** A permission mode that answers tool approvals and the AI's questions for you. Multiple-choice questions are left on screen for you.
- **Team mode.** Turn it on with the **Team** chip in the input bar; the choice is remembered per conversation (PC and phone). The AI you picked conducts and Gemini workers do the actual work: with Claude or Codex selected, that AI (with the model you chose) is the conductor; with Google AI selected, Claude Opus or Gemini 4 Argon conducts. Workers run on Gemini Flash through your Google subscription (Antigravity), and the conductor picks the worker's reasoning level per task. You can set the conductor's reasoning level, a cap on worker reports and how long to wait for a worker. Each answer shows conductor and worker tokens separately, plus an estimate of the usage team mode saved. Worker conversations are hidden from the list and from syncing.
- **Change the working folder.** Changing the folder of a started conversation continues it as a new conversation in the folder you pick.
- **Continue elsewhere.** Continue the current conversation in a new session, another AI, a new conversation in the same folder or a new git worktree, or copy its context.
- **Keep going while it answers.** Messages sent mid-answer go into a queue, or step in right away if you set it so. Queued messages can be removed, and with an empty input the send button becomes the stop button. You can open other conversations while one is answering. Up/Down in the input recalls earlier messages.
- **Background tasks.** The number and progress of tasks the AI runs in the background are shown in the conversation and in the list.
- **Regenerate and edit.** Regenerate rewinds the same conversation to just before that question, like the official apps (Claude rewind, Codex thread revert, Antigravity revert for Google AI), and sends it again. No new conversation is created. For Google AI, Sidekick first lists the files the AI changed after that point and lets you revert them too or rewind only the conversation. You can also edit and resend a message, branch from any message, and resend a message that failed to send.
- **Approvals and questions** from the AI, and confirmation requests from MCP servers, appear as cards in the conversation. You get a notification when an answer finishes or needs a reply.
- **Notification window.** Finished answers, questions and approval requests can show in a small separate window that does not take focus; you can answer right there. With it off, the sidebar peeks in or a Windows notification is used.
- **Suggested questions and replies.** The new-conversation screen suggests questions. Suggested replies are made when you click the input by default, or after every answer; you can choose the model for suggestions or turn them off.
- **Usage and context size.** Remaining usage for Claude, Codex and Google AI, shown separately. Each answer shows the model, tokens used, time taken and context size. When you return to a conversation with a large context, Sidekick asks whether to continue in a new conversation (configurable).
- **When to compact.** Set in settings when Claude and Codex summarize a long conversation; lower means less usage.
- **Attachments.** Attach the current screen, a specific window or image files. A setting attaches the current screen to every question.
- **Auto-attach selected text.** Press `Ctrl+Space` with text selected in another program to attach it. While a window is open, text you select by dragging or double-clicking can be attached too (can be turned off).
- **Sidekick-only global guidance.** Text in `~/.sidekick3/guidance.md` is added to conversations you have from Sidekick (Claude, Codex and Google AI). By default it is sent in full once per conversation, followed by a short reminder. It does not apply to official apps or terminals. Edits take effect from the next message; an empty file adds nothing.
- **Pick up after a restart.** If Sidekick closes during an update or crash and is back within 30 minutes, it asks the conversation that was answering to carry on, once (can be turned off).

### Organizing conversations

- Group the list by date, folder or custom group. Groups made in the Claude and Codex apps are shared.
- Rename conversations and pin them to the top of the list; the right-click or three-dot menu also moves them between groups.
- **Auto-organize.** Without any clicks, new conversations go into a fitting group, new groups are created when similar conversations pile up, and groups that are no longer needed are removed (conversations are never deleted). Only changes are organized, every few minutes, with the lightest judge model, pausing when the quota is nearly used. Conversations you moved by hand and pinned ones are left alone. Turn it off in Settings > Chat, or press "Organize now" in the group view.
- **Group order.** The group holding your most recent conversation comes first (sidebar, main window and phone alike). Settings > Chat > Group order switches back to your own order.

### Sidebar

- `Ctrl+Space` opens it. You can also set hotkeys for a new conversation and for the main window, or open it with the Copilot key.
- Float it as a window, or dock it to a screen edge, where it slides in and out; docking can push other windows aside.
- **Background effects:** Mica, Mica Alt, Acrylic, Acrylic without the gray tint, or none. The sidebar has separate effects for floating and docked, and the main window has its own. Theme, transparency, UI scale and font size are adjustable.

### Main window

- Conversations open in tabs, and a tab can be moved to a new window. The conversation list, document, files, changes (git) and terminal panels can be dragged into any arrangement.
- **Documents:** Markdown (with KaTeX math) and PDF. You can pick text to attach to a question, leave notes, and edit and save. Files the document pane can't open (Office documents, videos, archives, etc.) open in QuickLook when it is installed, and QuickLook can be added to Explorer's 'Open with' menu.
- **Files:** a file tree of the working folder. The right-click menu opens files in the document panel or the default app, copies or pastes paths into the conversation, and attaches file contents.
- **Changes:** see what the AI changed with git diffs and revert it. Reverted content is kept in a Sidekick folder for 30 days.
- **Terminal:** tabs for the commands the AI ran and for your own terminal (your own terminal is Windows only).

### Phone

- An Android app lets you read conversations, send questions and answer approval requests from your phone. See [Phone remote](#phone-remote).

The sidebar, floating. The new-conversation screen shows the remaining usage for each provider and suggested questions:

![Sidebar — floating](docs/screenshots/sidebar-chat.png)

The sidebar docked to the right edge; other windows make room for it:

![Sidebar — docked](docs/screenshots/sidebar-docked.png)

Dark theme with a README open in the document panel:

![Dark theme](docs/screenshots/main-dark.png)

## Install

Download from [sidekick-releases](https://github.com/Lian-CrescentMoon/sidekick-releases/releases/latest).

- Windows 11: `Sidekick-Setup-<version>.exe`. Installs into your user folder without admin rights; remove it from Settings > Apps.
- Linux arm64 (e.g. Raspberry Pi 5): `sudo apt install ./sidekick_<version>_arm64.deb`
- Linux x64: `sidekick_<version>_amd64.deb` or the `tar.gz`
- Android (phone remote): open `SidekickRemote-<version>.apk` on the phone to install it.

After installing, the app downloads and installs new versions itself, and only uses files whose signature checks out.

### What else you need

Only the official app for the AI you want to use. Sidekick reuses its sign-in.

- Claude: the Claude desktop app or Claude Code CLI
- Codex: the Codex app or Codex CLI
- Google AI: [Antigravity CLI](https://www.antigravity.google/docs/cli/install/) 1.3.1 or later

## Phone remote

The Android app in `android/` (Sidekick Remote) connects to Sidekick on your PC, over the same Wi-Fi or, away from home, over a Tailscale network both devices are on. Create a pairing QR under "휴대폰 원격 연결" in the PC settings, scan it with the phone, and approve on the PC once the confirmation number matches the one on the phone. Each phone gets its own switches for "send, stop and settings" and "approve tools and questions".

What the phone app can do:

- List and search conversations, view by date or group, filter by state and sort
- Start new conversations (including in a new folder), rename, pin to the top and move between groups
- Send and stop, choose what happens to messages sent mid-answer, cancel queued messages, slash command suggestions
- Attach photos and view images in conversations
- Regenerate, edit and resend, branch from a message, resend a message that failed
- Continue in a new session, another AI or a new conversation in the same folder
- Suggested replies
- Answer tool approvals and the AI's questions, including questions that arrive after a turn has ended
- Change model, reasoning level, permission mode, how auto model may switch, and team mode
- See the remaining usage per provider and message info (model, tokens, time taken)
- Background notifications, an optional app lock, theme

| List | Approval | Answer | Dark |
|---|---|---|---|
| ![](docs/screenshots/phone-list.png) | ![](docs/screenshots/phone-approval.png) | ![](docs/screenshots/phone-markdown.png) | ![](docs/screenshots/phone-dark.png) |

Get the APK from [sidekick-releases](https://github.com/Lian-CrescentMoon/sidekick-releases/releases/latest) or build it with `scripts/build-android.ps1`. Once installed, the phone app downloads newer versions from the paired PC or the public GitHub repository into the Downloads folder by itself; you install the downloaded file manually. Setup and limits: [docs/REMOTE_SETUP.md](docs/REMOTE_SETUP.md) (Korean).



## Layout

- `electron/`: the Electron shell (windows, tray, hotkeys, notification window, auto-update)
- `src/Sidekick.Backend`, `src/Sidekick`: the .NET 10 backend (engine connections, reading and syncing histories)
- `src/Sidekick/ui`: the UI (HTML, CSS and ES modules, no build step)
- `src/Sidekick.Remote`: the phone remote server
- `android/`: the phone app (Java, no third-party libraries)
- `installer/`, `scripts/`: installer and release scripts
- `tests/`: regression tests. They never call a real model or touch user histories; they use fake engines and temporary folders.

How the engines are connected: Claude runs the official app's `claude.exe` over the stream-json protocol, Codex runs `codex.exe app-server` over JSON-RPC, and Google AI runs the Antigravity CLI. Conversations are read from the official histories in `~/.claude/projects` and `~/.codex/sessions`; Sidekick only ever appends to them. Sidekick's own settings and logs are in `~/.sidekick3`.

## Building

On Windows:

```
powershell -File scripts/build-electron.ps1 -Out <folder>
```

You need the .NET 10 SDK, the Electron 44.6.0 runtime (default location `%USERPROFILE%\.sidekick\electron\dist`) and the `koffi` module. `scripts/build-installer.ps1` builds the installer, `python scripts/build-linux.py --arch arm64|x64` builds the Linux packages and `scripts/build-android.ps1` builds the phone APK.

Run a test project with `dotnet run --project tests/<Name>.Tests -c Debug`.

## Known limits

- Google AI accepts image and screen-capture attachments (up to 4 per message; not with GPT-OSS models). Conversations continued through the Antigravity CLI do not support in-conversation tool approval yet; tools that need extra approval are skipped by the official engine.
- Sidekick does not append to a history that an official app currently has open; it waits until the app lets go.
- The Claude app only shows newly added conversations after it restarts.
- On the phone, edit-and-resend changes text only, and there is no direct camera capture.
- The UI text is Korean. macOS is not supported.

## License

[MIT](LICENSE)
