# Hefaistos - Burp Suite Extension Suite

[![GitHub Repo stars](https://img.shields.io/github/stars/joelindra/Hefaistos?style=social)](https://github.com/joelindra/Hefaistos) [![GitHub issues](https://img.shields.io/github/issues/joelindra/Hefaistos)](https://github.com/joelindra/Hefaistos/issues)  [![Burp Suite Compatible](https://img.shields.io/badge/Burp%20Suite-Compatible-brightgreen)](https://portswigger.net/burp)

<img width="427" height="640" alt="H3F41ST0S Overview" src="https://github.com/user-attachments/assets/4d7f49ff-5bbc-4e0a-b639-b34acd801ced" />

### Documentation
```
https://joelindra.gitbook.io/all-tools/hefaistos
```

**Hefaistos** is a powerful, modular Burp Suite extension designed for web application security testing. Inspired by the mythical blacksmith of the gods, it forges tools to hammer vulnerabilities, listen for callbacks, and analyze requests with AI-powered insights. Built with a sleek, modern UI featuring glitch effects and neon themes, Hefaistos combines usability with advanced functionality for pentesters and bug bounty hunters.

This extension integrates seamlessly into Burp Suite, adding a dedicated tab with multiple sub-tools (panels) for fuzzing, JWT manipulation, reverse shells, request logging, and AI-driven analysis. It's actively maintained, with auto-update support via GitHub releases.

> **Note:** Hefaistos is for **authorized security testing only**. Always obtain explicit permission before using these tools on any target.

## 🚀 Features

Hefaistos packs a suite of specialized panels, each tailored for specific pentesting tasks:

| Panel | Description | Key Capabilities |
|-------|-------------|------------------|
| **🔨 Forge** | Advanced fuzzer for injecting payloads into HTTP requests. | - Multi-category payloads (SQLi, XSS, Path Traversal, etc.)<br>- Custom payloads and wordlists<br>- Parallel execution with rate limiting<br>- Real-time results table with status code highlighting |
| **🔨 Hammer** | JWT (JSON Web Token) analysis and cracking tool. | - Decode/encode headers and payloads<br>- Brute-force secret keys<br>- Algorithm confusion attacks<br>- Security checklist and fuzzing |
| **🌐 Tripod** | Listener for HTTP webhooks and reverse shells. | - HTTP callback server<br>- Reverse shell handler with interactive terminal<br>- Payload generator (shells, webshells, exfil)<br>- Port killer for conflict resolution |
| **🔩 Anvil** | Request logger and collector for interesting traffic. | - Auto-captures from Burp tools (Proxy, Repeater, etc.)<br>- Parameter extraction and summaries<br>- Collect/export lists of key requests |
| **🤖 Assistant** | AI-powered request analysis using LLMs. | - Integrate with Gemini, ChatGPT, Claude<br>- Bulk analysis mode<br>- Custom prompt templates<br>- History and export |
| **📋 Usage** | Interactive guide to all tools. | - Step-by-step tutorials<br>- Embedded HTML docs with links |
| **ℹ️ About** | Extension info with glitchy, hacker-themed UI. | - Version details<br>- Glitch animations and scan lines |
| **🔄 Updates** | Built-in updater. | - Auto-checks GitHub releases<br>- One-click download and hash verification |

- **Modern UI:** Dark theme with neon accents, animations (glitch text, scan lines), and responsive layouts.
- **Context Menu Integration:** Right-click requests in Burp (e.g., Proxy, Repeater) to "Send to [Tool]".
- **Extensibility:** YAML-based config, JSON templates, and modular panels.
- **Security Focus:** Built-in checklists, encodings, and OOB (Out-of-Band) support via Burp Collaborator.

## 📋 Table of Contents
- [Requirements](#requirements)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Panel Guides](#panel-guides)
  - [Forge - Fuzzer](#forge---fuzzer)
  - [Hammer - JWT Tool](#hammer---jwt-tool)
  - [Tripod - Listener](#tripod---listener)
  - [Anvil - Request Logger](#anvil---request-logger)
  - [Assistant - AI Analyzer](#assistant---ai-analyzer)
  - [Usage](#usage)
  - [About & Updates](#about--updates)
- [Configuration](#configuration)
- [Troubleshooting](#troubleshooting)
- [License](#license)
- [Support](#support)

## Requirements

- **Burp Suite Professional** (Community edition may work but lacks some integrations).
- **Java 8+** (bundled with Burp).
- **Internet Access** (for AI providers, updates, and Collaborator).
- **API Keys** (for Assistant panel: Gemini, OpenAI, Anthropic).

No additional dependencies required—everything is self-contained.

## Installation

1. **Download the JAR:**
   - Grab the latest release from [GitHub Releases](https://github.com/joelindra/Hefaistos/releases).

2. **Load in Burp:**
   - Open Burp Suite > **Extender** tab > **Extensions** > **Add**.
   - Select **Extension type: Java** and browse to `Hefaistos.jar`.
   - Click **Next** > **Load** > **Close**.

3. **Verify:**
   - A new **Hefaistos** tab appears in the main Burp interface.
   - Check the **Extender > Output** tab for "initialized successfully!".

4. **Auto-Update:**
   - Switch to the **Updates** panel in Hefaistos—it checks for new versions on load.

> **Pro Tip:** Enable Burp's **Auto-reload extensions** in settings for seamless updates (though manual unload/reload is recommended for safety).

## Quick Start

1. **Launch Burp** and load a target (e.g., via Proxy).
2. **Intercept Traffic:** Use Burp Proxy to capture requests.
3. **Right-Click a Request:** In Proxy/HTTP History, right-click > **Send to Hefaistos > [Panel]** (e.g., Forge for fuzzing).
4. **Explore Panels:** Switch tabs in the Hefaistos interface.
   - **Anvil:** Logs all traffic automatically—collect interesting requests.
   - **Assistant:** Paste a request and hit **Submit to AI** for vuln analysis.
   - **Tripod:** Start a listener on port 8080 for callbacks.
5. **View Usage Guide:** Check the **Usage** panel for tool-specific tutorials.

**Example Workflow:**
- Capture a login request in Proxy.
- Send to **Hammer** to crack the JWT session token.
- If vulnerable, send to **Forge** to fuzz parameters.
- Use **Tripod** for OOB exfil payloads.
- Analyze with **Assistant** for a full report.

## Panel Guides

### Forge - Fuzzer
The **Forge** panel is a powerful fuzzer for testing HTTP requests with various payloads.

- **Load Requests:** Right-click a request in Burp (e.g., Proxy, Repeater) > **Send to Forge**.
- **Select Marker:** Use `§` (default) or a custom marker to define payload insertion points.
- **Choose Payloads:** Select from built-in categories (e.g., SQLi, XSS, Path Traversal) or load custom wordlists.
- **Configure:** Set threads (via spinner) and requests per minute (RPM) for controlled scanning.
- **Run:** Click **Start**; monitor results in the sortable table (color-coded by status: 200=green, 500=red).
- **Inspect:** View modified vs. original request/response in side-by-side viewers.
- **Export:** Copy results or save to a file for reporting.

### Hammer - JWT Tool
The **Hammer** panel is designed for analyzing and attacking JSON Web Tokens (JWTs).

- **Decode JWT:** Paste a JWT into the input area; it auto-decodes header and payload.
- **Edit Mode:** Click **Edit** to modify claims or algorithms; save or reset changes.
- **Attacks:**
  - **Brute-Force:** Load a wordlist to crack the secret key.
  - **Algorithm Confusion:** Supply a public key to exploit misconfigured signing.
  - **Fuzzing Checklist:** Run automated security tests for common JWT vulnerabilities.
- **Output:** Results appear in the attack output area; copy tampered JWTs for testing.

### Tripod - Listener
The **Tripod** panel handles HTTP webhooks and reverse shells for OOB testing.

- **Modes:** Choose **HTTP Webhook** (for callbacks) or **Reverse Shell** (interactive terminal).
- **Start Listener:** Set a port (e.g., 8080) > **Start Listener**.
- **Payload Generator:**
  - Select category (e.g., Reverse Shell, Web Shell).
  - Choose OS (Linux/Windows) and shell type (e.g., Bash, PowerShell).
  - Auto-fill IP/port from listener settings.
  - Apply encodings (e.g., Base64, URL).
- **Interact:** Send commands in the terminal; view connection history in the table.
- **Utilities:** Use **Kill Used Ports** to terminate processes on conflicting ports.

### Anvil - Request Logger
The **Anvil** panel logs and analyzes HTTP requests from Burp tools.

- **Automatic Logging:** Captures requests from Proxy, Repeater, etc., into a sortable table.
- **Inspect Details:** Click a row to view:
  - **Summary:** Parsed URL/body parameters.
  - **Request/Response:** Raw data in Burp's message editor.
- **Collect Findings:** Select a request > **Add to List** to save its summary in the side panel.
- **Export:** Use **Copy List** to grab collected items; **Clear History** resets everything.

### Assistant - AI Analyzer
The **Assistant** panel leverages large language models (LLMs) for automated security analysis.

- **Setup:** Go to **Settings** tab > Enter API keys for Gemini, ChatGPT, or Claude.
- **Send Requests:** Right-click a request > **Send to Assistant**; it loads with a selected prompt template.
- **Analyze:**
  - Choose a provider and template (e.g., "Find SQLi vulnerabilities").
  - Edit the prompt directly if needed.
  - Enable **Bulk Mode** for multiple requests (separate with `---REQUEST_SEPARATOR---`).
- **Results:** View AI responses in the output area; history table tracks past analyses.
- **Templates:** Add/edit custom prompts in the **Templates** tab for tailored scans.

### Usage
The **Usage** panel provides an interactive guide for all tools.

- **Content:** Step-by-step HTML tutorials with emojis and clickable links.
- **Navigation:** Scrollable cards for each tool (Forge, Hammer, Tripod, Anvil, Assistant).
- **Purpose:** Quick reference without leaving Burp; ideal for new users.

### About & Updates
- **About:** Displays extension info with a hacker-themed UI (glitch effects, neon colors, scan lines).
- **Updates:**
  - Auto-checks GitHub for new releases.
  - Displays latest version, release notes, and SHA-256 hash.
  - Download updates with one click; manual reload required in Burp.

## Configuration

- **Settings Location:** Stored in Burp's extension settings (persists across sessions).
- **Assistant API Keys:**
  - Enter in **Assistant > Settings** tab.
  - Export/import configs via file for backup or team sharing.
- **Payloads/Templates:**
  - Edit built-in payloads in `ForgePanel.java` (requires rebuild).
  - Manage Assistant prompt templates via UI.
- **Custom Themes:** Modify colors/fonts in source files (e.g., `AboutPanel.java`, `UsagePanel.java`).
- **Config File:** `/config.yaml` in the JAR defines version and defaults (repackage to modify).

## Troubleshooting

| Issue | Solution |
|-------|----------|
| **"Port in use" (Tripod)** | Use **Kill Used Ports** to list/terminate processes; check port field. |
| **AI Errors (Assistant)** | Verify API keys; check quota limits; view stderr in **Extender > Output**. |
| **No Context Menu** | Restart Burp; check **Extender > Errors** for load issues. |
| **Update Fails** | Download manually from [Releases](https://github.com/joelindra/Hefaistos/releases); unload/reload JAR. |
| **Blank Panels** | Ensure Java 8+; check **Extender > Output** for stack traces. |
| **Slow Fuzzing (Forge)** | Reduce threads/RPM in settings; check network latency. |

- **Logs:** All output/errors are logged to **Extender > Output** in Burp.
- **Bugs:** Report issues on [GitHub Issues](https://github.com/joelindra/Hefaistos/issues) with:
  - Burp version
  - Java version
  - Steps to reproduce
  - Stack trace (if available)

## License

This project is licensed under the [MIT License](LICENSE) - see the file for details.

## Screenshots
<img width="1918" height="953" alt="image" src="https://github.com/user-attachments/assets/584e2333-c254-4a44-8e38-bc214d768aab" />
<img width="1919" height="977" alt="image" src="https://github.com/user-attachments/assets/291599a9-c26c-469b-960a-d3ba208a81e3" />
<img width="1917" height="973" alt="image" src="https://github.com/user-attachments/assets/7a8aaf08-68c7-4b71-80df-a2af8c105e66" />
<img width="1918" height="975" alt="image" src="https://github.com/user-attachments/assets/aa2f16af-81bb-401f-b6f4-a7d14bf3ccb4" />
<img width="1916" height="950" alt="image" src="https://github.com/user-attachments/assets/08412ef0-c891-4606-a7c3-5f22461c7f2f" />

## Support

- **Issues:** [GitHub Issues](https://github.com/joelindra/Hefaistos/issues)
- **Discussions:** [GitHub Discussions](https://github.com/joelindra/Hefaistos/discussions)

Thanks for using Hefaistos—forge your way to better security! ⚒️🔥

---

*Built with ❤️ by Joel Indra. Contributions from the Burp community.*  
*Last Updated: September 15, 2025*
