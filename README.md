# CodePort

> Control Codex from your iPhone. Keep the runtime, your files, and the actual work on your Mac.

![Platform](https://img.shields.io/badge/iOS%20%26%20iPadOS-17%2B-black?style=flat-square&logo=apple)
![Platform](https://img.shields.io/badge/macOS-14%2B-black?style=flat-square&logo=apple)
![Language](https://img.shields.io/badge/Swift-6.0-F05138?style=flat-square&logo=swift&logoColor=white)
![UI](https://img.shields.io/badge/SwiftUI-Native-0066CC?style=flat-square&logo=swift&logoColor=white)
![Status](https://img.shields.io/badge/Status-Private%20Beta-orange?style=flat-square)

<p align="center">
  <img src="Codeport%20mobile/Assets.xcassets/AppIcon.appiconset/ios_marketing_1024x1024.png" alt="CodePort App Icon" width="180">
</p>

---

## What Is CodePort?

CodePort is a native iPhone and iPad control center for OpenAI Codex running on your Mac.

Send prompts, watch live output, answer approval requests, inspect changes, manage branches, and keep long-running Codex work moving without sitting at your desk.

CodePort is not a standalone AI runtime. Codex still runs on your Mac through **CodePort Bridge**, a native macOS companion app that connects your phone to the Codex app-server.

---

## Download CodePort Bridge

CodePort requires the Mac companion app before the iPhone app can connect.

[![Download CodePort Bridge](https://img.shields.io/badge/Download-CodePort%20Bridge-000000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/frafra077/codeport-app/releases)

1. Download the latest **CodePort Bridge** release for macOS.
2. Move the app to **Applications**.
3. Launch CodePort Bridge and keep it running in the menu bar.
4. Open CodePort on iPhone and scan the QR code shown by the Bridge.

After pairing once, CodePort remembers your trusted Mac and reconnects automatically.

---

## How It Works

| App | Platform | Role |
|-----|----------|------|
| **CodePort** | iPhone / iPad | Send prompts, monitor runs, answer approvals, manage chats |
| **CodePort Bridge** | Mac | Runs near Codex, handles pairing, relay, encryption, Git, and app-server routing |
| **Codex app-server** | Mac | Executes Codex sessions, tool calls, file edits, and workspace operations |

CodePort sends messages to the Bridge, the Bridge forwards them to `codex app-server`, and responses stream back to your iPhone in real time.

Your codebase stays on your Mac. File edits, shell commands, Git actions, and Codex sessions are executed locally.

---

## Current Features

| Feature | Description |
|---------|-------------|
| **Native iPhone and iPad app** | Start and continue Codex threads from iOS and iPadOS |
| **Native Mac Bridge** | Menu bar companion app with QR pairing, settings, console, and version reporting |
| **Live response streaming** | Watch Codex output, tool activity, command results, and assistant messages as they happen |
| **Trusted QR pairing** | Scan once, save the Mac as a trusted device, and reconnect without reconfiguring |
| **End-to-end encrypted transport** | Uses X25519, Ed25519, HKDF-SHA256, AES-256-GCM, and replay protection after pairing |
| **Local and relay connection modes** | Works on the same network and supports compatible relay-based remote access |
| **Push notifications** | Get notified when a run finishes or when Codex needs approval |
| **Voice input** | Dictate prompts with native speech transcription |
| **Image attachments** | Attach images from Photos, camera, pasteboard, or picker flows |
| **Plan Mode support** | Start planning turns and respond to structured decision prompts from iPhone |
| **Subagent visibility** | Follow subagent activity directly inside the mobile conversation timeline |
| **File and skill mentions** | Use autocomplete for workspace files and Codex skills while composing prompts |
| **Slash commands** | Trigger supported runtime actions from the composer |
| **Git controls** | View diffs, switch branches, create branches, commit, push, pull, stash, reset to remote, and open PR compare URLs |
| **Managed worktrees** | Move work into isolated worktrees for safer branch-based changes |
| **Change review and revert** | Inspect file-change summaries and apply assistant revert flows when needed |
| **Context usage view** | Track current thread context-window usage from the app |
| **Archived chats** | Keep old threads out of the main sidebar without losing them |
| **Runtime defaults** | Choose model, reasoning effort, service tier, and Mac access defaults for new turns |
| **Account visibility** | See the Codex account and plan currently active on your Mac Bridge |

---

## Security Model

CodePort is designed around one simple rule: the Mac is the trusted execution environment.

- Codex runs on your Mac.
- Your workspace stays on your Mac.
- The Bridge owns local process, Git, filesystem, and approval handling.
- The iPhone acts as a secure remote control.
- Pairing stores trusted device identity in Keychain.
- Encrypted envelopes protect message contents after the handshake.
- Relay servers route traffic but do not run Codex or replace the Bridge.

---

## Remote Access

On the same Wi-Fi network, CodePort can connect locally.

Outside your LAN, CodePort supports a compatible WebSocket relay. You can self-host a relay or expose one through infrastructure you control.

Guides:

- [Remote Access Guide](docs/remote-access-guide.en.md)
- [Guida Accesso Remoto](docs/remote-access-guide.it.md)
- [Cloudflare Push Worker](cloudflare-push-worker/README.md)

Remote access still requires CodePort Bridge running on your Mac.

---

## Requirements

- iPhone or iPad running **iOS/iPadOS 17+**
- Mac running **macOS 14+**
- **OpenAI Codex** installed and configured on your Mac
- **CodePort Bridge** running on your Mac
- Same Wi-Fi network for local mode, or a compatible relay for remote access

---

## Setup

### First Run

1. Install and open **CodePort Bridge** on your Mac.
2. Open **CodePort** on your iPhone or iPad.
3. Scan the Bridge QR code.
4. Start a new Codex thread from your phone.

### Daily Use

1. Keep CodePort Bridge running in the Mac menu bar.
2. Open CodePort on iPhone.
3. Send prompts, review output, approve commands, and manage changes from wherever you are.

---

## Built With

![Swift](https://img.shields.io/badge/Swift-F05138?style=for-the-badge&logo=swift&logoColor=white)
![SwiftUI](https://img.shields.io/badge/SwiftUI-0066CC?style=for-the-badge&logo=swift&logoColor=white)
![Xcode](https://img.shields.io/badge/Xcode-1575F9?style=for-the-badge&logo=xcode&logoColor=white)
![iOS](https://img.shields.io/badge/iOS-000000?style=for-the-badge&logo=ios&logoColor=white)
![macOS](https://img.shields.io/badge/macOS-000000?style=for-the-badge&logo=macos&logoColor=white)

---

## Status

CodePort is currently in private beta.

The app is under active development, with ongoing work around Bridge releases, remote access, notifications, Git workflows, and the mobile Codex experience.

---

## Roadmap

- [x] Native iPhone and iPad app
- [x] Native macOS Bridge
- [x] QR pairing and trusted reconnect
- [x] Live response streaming
- [x] End-to-end encrypted session transport
- [x] Remote relay support
- [x] Push notifications
- [x] Voice input
- [x] Image attachments
- [x] Plan Mode
- [x] Git branch, diff, commit, push, pull, stash, and worktree controls
- [x] Bridge download flow
- [ ] Public beta
- [ ] More packaged Bridge release channels
- [ ] Hosted relay option

---

## Follow The Journey

[![Follow on X](https://img.shields.io/badge/Follow_on_X-000000?style=for-the-badge&logo=x&logoColor=white)](https://x.com/fraraf85)

---

## Disclaimer

CodePort is an independent project and is not affiliated with, endorsed by, or officially connected to OpenAI.

Codex is a product and trademark of OpenAI.

---

> This is a showcase repository. Source code access is limited to collaborators and testers.
