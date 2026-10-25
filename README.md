<div align="center">

<img src="./assets/logo.png" width="140" height="140" alt="WildAI CLI" />

# WildAI CLI

**Official command-line interface & autonomous coding agent for the WildAI platform.**

[![NPM Version](https://img.shields.io/npm/v/wildai-cli?style=flat-square&color=10a37f)](https://www.npmjs.com/package/wildai-cli)
[![Node Version](https://img.shields.io/badge/node-%3E%3D18.0.0-blue?style=flat-square)](https://nodejs.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.8-3178c6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-macOS%20%7C%20Linux%20%7C%20Windows-lightgrey?style=flat-square)](https://github.com/wildai-poland/wildai-cli)

</div>

---

## ⚡ Overview

`wildai-cli` is a terminal developer environment and autonomous agent built for high-throughput AI engineering workflows. It provides streaming inference with live token telemetry, context-aware repository analysis, and direct filesystem tool execution guarded by strict Human-in-the-Loop security policies.

---

## 🚀 Key Features

* **🤖 Autonomous Developer Agent (`/mode`)**:
  * Direct filesystem authoring (`readFile`, `writeFile`, `listDirectory`).
  * Automated Code-Block Disk Detection: model-generated code in conversations can be immediately saved to disk with interactive confirmation.
  * Native shell execution and Git repository inspection.
  * Human-in-the-Loop confirmation with deterministic execution controls.
* **📊 Real-Time Telemetry & Token Accounting**:
  * Live generation velocity tracking in tokens per second (`tok/s`).
  * Time to First Token (TTFT) measurement.
  * Granular prompt and completion token counts.
  * Session-wide USD cost estimation.
* **🔒 Enterprise-Grade Security Architecture**:
  * **macOS Keychain Integration**: Hardware-backed credential management using the Apple `security` framework. Tokens are never stored in plaintext on disk.
  * **Filesystem Boundary Jail**: Strict path validation prevents Path Traversal attacks beyond the active working directory.
  * **Command Risk Analysis**: Shell execution whitelist combined with heuristic detection of dangerous and obfuscated commands (`rm -rf`, subshells, piping).
  * **Tool Execution Budget**: Built-in iteration limits prevent recursive agent loops.
* **💬 Conversational Threads & One-Shot Mode**:
  * Full conversational state management.
  * Instant single-command prompt resolution without entering interactive mode.
* **📋 Developer Workflow Utilities**:
  * One-key clipboard sync (`/copy`).
  * Complete session export to GitHub Flavored Markdown (`/save`).

---

## 📦 Installation

### Global via NPM

```bash
npm install -g wildai-cli
```

### Running with NPX

```bash
npx wildai-cli
```

### From Source

```bash
git clone https://github.com/wildai-poland/wildai-cli.git
cd wildai-cli
npm install
npm run build
npm link
```

---

## 💻 Quick Start

### 1. Authenticate

```bash
wildai login
```
Session tokens are stored directly in your native **macOS Keychain** (or encrypted via AES-256-GCM with POSIX `0600` permissions on other operating systems).

### 2. Interactive Session

Launch the interactive chat interface:

```bash
wildai
```

### 3. Agent Mode (Autonomous Developer Tooling)

Inside the interactive session, switch to agent mode:

```text
❯ /mode
```

Ask the agent to implement, edit, or test code in your project:

```text
❯ [agent] Utwórz plik test_server.py z prostym serwerem w Pythonie i uruchom test
```

The agent will analyze the request, write the file to your disk (requesting confirmation), and run the test suite.

### 4. One-Shot Execution

Execute single commands directly from your terminal:

```bash
wildai "Napisz algorytm przeszukiwania binarnego w TypeScript z pełnym typowaniem"
```

---

## ⌨️ Command Reference

### Slash Commands (Inside Session)

| Command | Description |
| :--- | :--- |
| `/mode` | Toggle execution mode: **Standard Chat** ↔ **Autonomous Developer Agent** |
| `/model` | Select active AI model from live registry |
| `/tools` | Display available agent tools and execution permissions |
| `/tokens` or `/stats` | View comprehensive token metrics, velocity, and session cost |
| `/copy` | Copy last assistant response to system clipboard |
| `/save [file]` | Export conversation history to Markdown file |
| `/whoami` | Verify account identity, plan status, and active API gateway |
| `/login` | Authenticate without terminating the active session |
| `/logout` | Invalidate session and purge credentials from Keychain |
| `/clear` | Clear terminal display and reset conversation memory |
| `/exit` | Exit the application |

---

## 🛡️ Security Model

WildAI CLI operates under a strict principle of least privilege:

```text
┌────────────────────────────────────────────────────────┐
│                   WildAI Security Core                 │
├─────────────────────────┬──────────────────────────────┤
│ Authentication Storage  │ macOS Keychain / AES-256-GCM │
│ Filesystem Boundaries   │ Project Root Jail (CWD)      │
│ Command Execution       │ Human-in-the-Loop Whitelist  │
│ Tool Iteration Limit    │ Capped at 3 calls / prompt   │
│ Sensitive File Blocking │ .env, SSH keys, credentials  │
└─────────────────────────┴──────────────────────────────┘
```

> [!IMPORTANT]
> All file writes and shell commands require explicit interactive confirmation (`[y/N]`) with default refusal. No agent action can alter system state without human approval.

---

## 🤝 Contributing

We welcome contributions from the community! Please refer to the [Contributing Guide](https://github.com/wildai-poland/.github/blob/main/CONTRIBUTING.md) and [Code of Conduct](https://github.com/wildai-poland/.github/blob/main/CODE_OF_CONDUCT.md).

---

## 📄 License

WildAI CLI is open-source software licensed under the [MIT License](LICENSE).

<div align="center">
  <sub>Maintained by <a href="https://github.com/wildai-poland">WildAI Poland</a>.</sub>
</div>
