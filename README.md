## Hefaistos — Burp Suite Extension Suite
[![GitHub Repo stars](https://img.shields.io/github/stars/joelindra/Hefaistos?style=social)](https://github.com/joelindra/Hefaistos)
[![GitHub issues](https://img.shields.io/github/issues/joelindra/Hefaistos)](https://github.com/joelindra/Hefaistos/issues)
[![Burp Suite Compatible](https://img.shields.io/badge/Burp%20Suite-Compatible-brightgreen)](https://portswigger.net/burp)

<img width="427" height="640" alt="H3F41ST0S Overview" src="https://github.com/user-attachments/assets/4d7f49ff-5bbc-4e0a-b639-b34acd801ced" />

Hefaistos is a powerful, modular Burp Suite extension designed for web application security testing. Inspired by the mythical blacksmith of the gods, it forges tools to hammer vulnerabilities, listen for callbacks, and analyze requests with AI-powered insights. Built with a sleek, modern UI featuring glitch effects and neon themes, Hefaistos combines usability with advanced functionality for pentesters and bug bounty hunters.

- **Docs:** [GitBook — Hefaistos](https://joelindra.gitbook.io/all-tools/hefaistos)
- **Latest Release:** [GitHub Releases](https://github.com/joelindra/Hefaistos/releases)
- **Screenshots:** See below

> Note: Hefaistos is for authorized security testing only. Always obtain explicit permission before using these tools on any target.

---

## Table of Contents
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Panel Guides](#panel-guides)
  - [Forge — Fuzzer](#forge--fuzzer)
  - [Hammer — JWT Tool](#hammer--jwt-tool)
  - [Tripod — Listener](#tripod--listener)
  - [Anvil — Request Logger](#anvil--request-logger)
  - [Assistant — AI Analyzer](#assistant--ai-analyzer)
  - [Usage](#usage)
  - [About and Updates](#about-and-updates)
- [Context Menu and Integrations](#context-menu-and-integrations)
- [Troubleshooting](#troubleshooting)
- [FAQ](#faq)
- [Security, Privacy and Legal](#security-privacy-and-legal)
- [Roadmap](#roadmap)
- [License](#license)
- [Support](#support)

---

## Features

- **Modular Tool Suite (Panels):**
  - **Forge:** Advanced fuzzer (multi-category payloads, custom wordlists, parallelism, RPM throttling, real-time results, export).
  - **Hammer:** JWT analyzer and attacker (decode/encode, brute-force, alg confusion, checklist and fuzzing).
  - **Tripod:** OOB testing utilities (HTTP webhook listener, reverse shell handler, payload generator, port killer).
  - **Anvil:** Request logger and collector (auto-capture from Burp tools, summaries, curated list, export).
  - **Assistant:** LLM-powered analysis (Gemini, OpenAI, Claude; bulk analysis; prompt templates; history and export).
  - **Usage, About, Updates:** In-product docs, UI showcase, and one-click updater with hash verification.

- **Modern UI:** Dark theme with neon accents, glitch effects, scan lines, responsive layouts.
- **Context Menu Integration:** “Send to Hefaistos → [Panel]” from Proxy, Repeater, etc.
- **Extensibility:** YAML config, modular panels, JSON templates, customizable colors/fonts.
- **Security Focus:** Built-in checklists, encodings, and OOB support via Burp Collaborator.

---

## Requirements

- **Burp Suite Professional** (Community may work but lacks some integrations)
- **Java 8+** (bundled with Burp)
- **Internet access** (for AI providers, updates, Collaborator)
- **API keys** for Assistant panel (Gemini, OpenAI, Anthropic) if used

No additional system dependencies required. JAR ships with bundled libs.

---

## Installation

1. Download the JAR from [GitHub Releases](https://github.com/joelindra/Hefaistos/releases).
2. In Burp Suite: Extender → Extensions → Add → Extension type: Java → Select `Hefaistos.jar` → Next → Load → Close.
3. Verify: A new tab “Hefaistos” appears; Extender → Output shows “initialized successfully!”.
4. Optional: Open the “Updates” panel to auto-check for new versions.

Pro Tip: You can enable Burp's “Auto-reload extensions”, though manual reload is recommended for safety.

---

## Quick Start

1. Launch Burp and capture traffic via Proxy.
2. Right-click a request in Proxy/HTTP history → Send to Hefaistos → Choose a panel.
3. Explore Hefaistos tabs:
   - Anvil: Logs and summarizes traffic automatically.
   - Assistant: Submit a request for LLM-based analysis.
   - Tripod: Start an HTTP webhook listener or reverse shell handler.
4. Refer to the “Usage” panel for in-app tutorials.

Example workflow:
- Capture a login request → Hammer to analyze/crack JWT → Forge to fuzz parameters → Tripod for OOB payloads → Assistant to produce a report.

---

## Panel Guides

### Forge — Fuzzer

- Load requests via context menu (Send to Forge) or paste manually.
- Mark insertion points with `§` (default) or a custom marker.
- Choose payloads by category (SQLi, XSS, Path Traversal, etc.) or load custom wordlists.
- Configure threads and requests-per-minute for controlled scanning.
- Start and monitor results in the sortable, color-coded table (e.g., 200=green, 500=red).
- Inspect modified vs. original request/response in side-by-side viewers.
- Export results to file for reporting.

### Hammer — JWT Tool

- Paste a JWT to auto-decode header and payload.
- Edit mode enables claims/alg modifications; save/reset quickly.
- Attacks:
  - Brute-force secrets via wordlist.
  - Algorithm confusion with supplied public key.
  - Automated security checks and fuzzing.
- Copy tampered tokens and see detailed output.

### Tripod — Listener

- Modes: HTTP Webhook or Reverse Shell (interactive terminal).
- Choose a port and click Start Listener.
- Payload generator:
  - Reverse shell, web shell, or exfil templates.
  - OS selection (Linux/Windows), shell type (Bash/PowerShell).
  - Auto-fill IP/port from the listener.
  - Optional encodings (Base64, URL).
- Utilities include “Kill Used Ports” for conflicts.

### Anvil — Request Logger

- Auto-captures requests from Burp tools into a sortable table.
- Click a row to view parsed summaries and raw request/response.
- Curate interesting requests with “Add to List”; export or clear.

### Assistant — AI Analyzer

- Configure API keys in the Settings tab (Gemini, OpenAI, Anthropic).
- Send a request via context menu or paste manually.
- Choose a provider and a prompt template, adjust if needed.
- Bulk mode supports multiple requests separated by `---REQUEST_SEPARATOR---`.
- View results and access history; export as needed.

### Usage

- In-app guide with step-by-step tutorials, emojis, and links.
- Quick reference for new users without leaving Burp.

### About and Updates

- About: Neon/glitch themed extension info.
- Updates: Auto-checks GitHub for new versions, shows notes and SHA-256 hash, and downloads with one click. Manual reload in Burp is required.

---

## Context Menu and Integrations

- From Proxy, Repeater, etc.: Right-click → Send to Hefaistos → [Forge | Hammer | Tripod | Anvil | Assistant].
- Out-of-Band testing integrates with Burp Collaborator.

---

## Troubleshooting

| Issue | Solution |
|---|---|
| Port in use (Tripod) | Use “Kill Used Ports” and ensure the port field is correct. |
| AI errors (Assistant) | Verify API keys, check provider quotas, see Extender → Output. |
| No context menu | Restart Burp, check Extender → Errors for load issues. |
| Update fails | Download from Releases, unload/reload the JAR in Burp. |
| Blank panels | Ensure Java 8+, check Extender → Output for stack traces. |
| Slow fuzzing (Forge) | Reduce threads/RPM; consider target/network latency. |

Logs: All output/errors appear under Extender → Output in Burp.

---

## FAQ

- Can I use this with Burp Community?
  - Generally yes, but some integrations are Pro-only and performance differs.

- Does Hefaistos phone home or collect telemetry?
  - No. Network calls are limited to your configured providers (AI) and update checks.

- Where are my settings stored?
  - In Burp’s extension settings store. You can export/import via the UI.

- How do I add custom payloads?
  - Use custom wordlists in Forge or modify payloads in `ForgePanel.java` and rebuild.

---

## Security, Privacy and Legal

- Use only with explicit authorization on systems you own or are permitted to test.
- Review payloads and AI prompts before use in sensitive environments.
- When using AI providers, request data may be sent to third parties as part of analysis.
- This tool is provided “as is” without warranty. See License for details.

---

## Roadmap

- Additional payload packs and wordlist management in UI
- More Assistant provider options and structured outputs
- Enhanced reporting/export formats
- Quality-of-life improvements across panels

Track progress and suggest features in [GitHub Issues](https://github.com/joelindra/Hefaistos/issues) and [Discussions](https://github.com/joelindra/Hefaistos/discussions).

---

## License

Licensed under the MIT License. See `LICENSE` for details.

---

## Screenshots
<img width="1918" height="953" alt="image" src="https://github.com/user-attachments/assets/584e2333-c254-4a44-8e38-bc214d768aab" />

<img width="1919" height="977" alt="image" src="https://github.com/user-attachments/assets/291599a9-c26c-469b-960a-d3ba208a81e3" />

<img width="1917" height="973" alt="image" src="https://github.com/user-attachments/assets/7a8aaf08-68c7-4b71-80df-a2af8c105e66" />

<img width="1918" height="975" alt="image" src="https://github.com/user-attachments/assets/aa2f16af-81bb-401f-b6f4-a7d14bf3ccb4" />

<img width="1916" height="950" alt="image" src="https://github.com/user-attachments/assets/08412ef0-c891-4606-a7c3-5f22461c7f2f" />

---

## Support

- Issues: [GitHub Issues](https://github.com/joelindra/Hefaistos/issues)
- Discussions: [GitHub Discussions](https://github.com/joelindra/Hefaistos/discussions)
- Documentation: [GitBook — Hefaistos](https://joelindra.gitbook.io/all-tools/hefaistos)

Thanks for using Hefaistos — forge your way to better testing! ⚒️🔥

Built with N by Joel Indra.
