## Hefaistos — Burp Suite Extension Suite

<img width="427" height="640" alt="H3F41ST0S Overview" src="https://github.com/user-attachments/assets/4d7f49ff-5bbc-4e0a-b639-b34acd801ced" />

[![GitHub Repo stars](https://img.shields.io/github/stars/joelindra/Hefaistos?style=social)](https://github.com/joelindra/Hefaistos)
[![GitHub issues](https://img.shields.io/github/issues/joelindra/Hefaistos)](https://github.com/joelindra/Hefaistos/issues)
[![Burp Suite Compatible](https://img.shields.io/badge/Burp%20Suite-Compatible-brightgreen)](https://portswigger.net/burp)

Hefaistos is a powerful, modular Burp Suite extension designed for web application security testing. Inspired by the mythical blacksmith of the gods, it forges tools to hammer vulnerabilities, listen for callbacks, convert curl commands, and analyze requests. Built with a sleek, modern UI featuring glitch effects and neon themes, Hefaistos combines usability with advanced functionality for pentesters and bug bounty hunters.

> Note: Hefaistos is for authorized security testing only. Always obtain explicit permission before using these tools on any target.

---

## Table of Contents
- [Features](#features)
- [Panel Guides](#panel-guides)
  - [Forge — Fuzzer](#forge--fuzzer)
  - [Hammer — JWT Tool](#hammer--jwt-tool)
  - [Tripod — Listener](#tripod--listener)
  - [Curltorepeater — Curl Converter](#curltorepeater--curl-converter)
  - [Anvil — Request Logger](#anvil--request-logger)
  - [Usage — In-App Guide](#usage--in-app-guide)
  - [About — Extension Information](#about--extension-information)
  - [Update — Auto-Updater](#update--auto-updater)
- [Context Menu and Integrations](#context-menu-and-integrations)
- [Troubleshooting](#troubleshooting)
- [FAQ](#faq)
- [Security, Privacy and Legal](#security-privacy-and-legal)
- [Roadmap](#roadmap)
- [License](#license)
- [Support](#support)

---

## Features

### Core Tool Panels (5)

- **Forge — Fuzzer:** Advanced HTTP request fuzzing with multi-target support, pre-built payload categories (SQLi, XSS, Path Traversal, Command Injection, XXE, SSRF), custom wordlists, parallel execution, RPM throttling, real-time results monitoring, grep highlighting, and comprehensive export capabilities.

- **Hammer — JWT Tool:** Complete JWT analysis and attack suite featuring automatic decode/encode, interactive editing, brute-force attacks with wordlists, algorithm confusion attacks, automated security checks, fuzzing capabilities, and Burp Collaborator integration.

- **Tripod — Listener:** Out-of-band testing utilities with dual-mode operation: HTTP webhook listener for capturing callbacks and interactive reverse shell handler. Includes payload generator with multiple templates (reverse shells, web shells, exfil), OS/shell selection, encoding options, and port management utilities.

- **Curltorepeater — Curl Converter:** Convenient curl command converter that transforms standard curl commands into HTTP requests and automatically sends them through Burp Suite proxy. Supports all common curl options including custom headers, request methods (GET, POST, PUT, DELETE, PATCH), authentication, and body data. Perfect for quickly testing API endpoints and converting browser-generated curl commands.

- **Anvil — Request Logger:** Intelligent request capture and analysis tool that automatically logs requests from all Burp Suite tools, provides parsed summaries with parameter extraction, curated list functionality, and export capabilities for reporting.

### Utility Panels (3)

- **Usage:** Interactive in-app guide with step-by-step tutorials, visual references, and quick-start guides for all panels.

- **About:** Neon-themed information panel showcasing extension details with glitch effects and cyberpunk aesthetics.

- **Update:** One-click auto-updater with GitHub release checking, SHA-256 hash verification, release notes display, and safe update process.

### Additional Features

- **Modern UI:** Dark/light theme support with automatic adaptation to Burp Suite's theme, neon accents, glitch effects, and responsive layouts.

- **Context Menu Integration:** Seamless "Send to Hefaistos → [Panel]" integration from Proxy, Repeater, Intruder, and other Burp tools.

- **Extensibility:** YAML configuration support, modular panel architecture, JSON templates, and customizable themes.

- **Security Focus:** Built-in vulnerability checklists, multiple encoding options, OOB testing support via Burp Collaborator, and secure credential storage.

---

## Panel Guides

Hefaistos consists of **8 main panels** organized into two groups: **Core Tools** (Forge, Hammer, Tripod, Curltorepeater, Anvil) and **Utility Panels** (Usage, About, Update).

---

### Forge — Fuzzer

**Advanced HTTP request fuzzing with multi-target support and real-time monitoring.**

**Key Features:**
- **Request Management:**
  - Load requests via context menu ("Send to Forge") or paste manually
  - Support for multiple request targets simultaneously
  - Request selector dropdown to switch between loaded requests
  - Custom marker support (default: `§`) for insertion points

- **Payload Configuration:**
  - Pre-built payload categories: SQL Injection, XSS, Path Traversal, Command Injection, XXE, SSRF, and more
  - Custom wordlist support (load from file)
  - Per-category payload configuration and editing
  - Multiple insertion points per request

- **Fuzzing Controls:**
  - Thread count configuration for parallel execution
  - Requests-per-minute (RPM) throttling to avoid overwhelming targets
  - Parallel execution toggle
  - Start/Stop controls with progress tracking

- **Results & Analysis:**
  - Real-time results table with sortable columns
  - Color-coded status codes (200=green, 3xx=yellow, 4xx=orange, 5xx=red)
  - Side-by-side comparison: original vs. modified request/response
  - Response length, status code, and timing information
  - Grep highlighting for custom patterns
  - Export results to file (CSV/JSON)

- **Advanced Features:**
  - Category and target filtering
  - Request/response viewers with syntax highlighting
  - Status counters (total, success, redirect, error, server error)
  - Progress bar and real-time status updates

---

### Hammer — JWT Tool

**Comprehensive JWT (JSON Web Token) analyzer, editor, and attacker.**

**Key Features:**
- **JWT Decoding & Display:**
  - Automatic header and payload decoding on paste
  - Pretty-printed JSON with syntax highlighting
  - Security analysis with vulnerability checklist
  - Claims viewer with expandable sections

- **JWT Editing:**
  - Edit mode for modifying claims and algorithm
  - Quick save/reset functionality
  - Real-time token regeneration
  - Copy tampered tokens to clipboard

- **Attack Capabilities:**
  - **Brute-Force Attack:**
    - Wordlist-based secret/key cracking
    - Progress tracking with cancel support
    - Configurable thread count
  - **Algorithm Confusion:**
    - Public key injection attacks
    - RSA/ECDSA key support
    - Automatic token regeneration
  - **Security Fuzzing:**
    - Automated security checks
    - Claim manipulation testing
    - Burp Collaborator integration for OOB testing

- **Additional Tools:**
  - Secret/key input for manual verification
  - Detailed attack output with timestamps
  - Export capabilities for analysis results

---

### Tripod — Listener

**Out-of-Band (OOB) testing utilities with HTTP webhook listener and reverse shell handler.**

**Key Features:**
- **Listener Modes:**
  - **HTTP Webhook Mode:**
    - Capture HTTP requests with full headers and body
    - Request history table with sortable columns
    - Request/response viewer with syntax highlighting
    - Search and filter capabilities
  - **Reverse Shell Mode:**
    - Interactive terminal interface
    - Real-time command execution
    - Customizable shell prompt
    - Input/output separation with color coding

- **Payload Generator:**
  - **Payload Categories:**
    - Reverse shell payloads (Bash, PowerShell, Python, etc.)
    - Web shell templates (PHP, JSP, ASPX)
    - Data exfiltration payloads
  - **Configuration Options:**
    - OS selection (Linux, Windows)
    - Shell type (Bash, PowerShell, CMD)
    - IP address auto-fill from listener
    - Port configuration
    - Encoding options (Base64, URL encoding, Hex)
  - **Templates:**
    - Pre-built payload templates
    - Customizable payload structure
    - Copy to clipboard functionality

- **Utilities:**
  - Port conflict resolution ("Kill Used Ports")
  - Request history export
  - Terminal search and highlighting
  - Auto-scroll toggle
  - Theme toggle (dark/light)

- **Advanced Features:**
  - Network interface detection
  - Multiple client connection support (HTTP mode)
  - Request timestamping
  - Export capabilities

---

### Curltorepeater — Curl Converter

**Convert curl commands to HTTP requests and send them through Burp Suite proxy.**

**Key Features:**
- **Curl Command Parsing:**
  - Automatic parsing of curl commands from browser/terminal
  - Support for quoted and unquoted URLs
  - Header extraction from `-H` or `--header` flags
  - Request body extraction from `-d`, `--data`, `--data-raw`, `--data-binary`
  - HTTP method detection from `-X` or `--request` flags
  - Basic authentication support via `-u` or `--user` flags

- **Request Execution:**
  - Automatic conversion to HTTP request format
  - Sends requests through Burp Suite proxy automatically
  - Request/response viewers for full analysis
  - Status code and response information display
  - Error handling with clear messages

- **Supported Curl Options:**
  - `-X` / `--request`: HTTP method specification
  - `-H` / `--header`: Custom headers
  - `-d` / `--data` / `--data-raw` / `--data-binary`: Request body
  - `-u` / `--user`: Basic authentication
  - URL parsing (with or without quotes)

- **Use Cases:**
  - Convert browser DevTools curl commands
  - Test API endpoints quickly without terminal
  - Integrate external tools with Burp Suite
  - Replay requests from documentation
  - Convert Postman/Insomnia curl exports

**Example Usage:**
```bash
curl -X POST https://api.example.com/data \
  -H "Authorization: Bearer token" \
  -H "Content-Type: application/json" \
  -d '{"key":"value"}'
```

Simply paste the curl command into Curltorepeater and click Submit to send it through Burp proxy.

---

### Anvil — Request Logger

**Automatic request capture, logging, and analysis with intelligent summarization.**

**Key Features:**
- **Automatic Capture:**
  - Auto-captures requests from all Burp Suite tools (Proxy, Repeater, Intruder, Scanner)
  - Real-time logging with sortable table
  - Request counter and timestamp tracking

- **Request Analysis:**
  - **Summary View:**
    - Parsed request summary with method, URL, parameters
    - Parameter selection with checkboxes
    - Collapsible sections for extra parameters
    - Request/response metadata
  - **Detailed View:**
    - Full request/response viewers (Burp's native editors)
    - Syntax highlighting
    - Request modification capabilities

- **Curated Lists:**
  - "Add to List" functionality for interesting requests
  - Side panel for curated request summaries
  - Export curated lists
  - Clear list functionality

- **Export & Management:**
  - Export full log or curated list
  - Clear log functionality
  - Request filtering and search
  - Parameter-based organization

---

### Usage — In-App Guide

**Interactive tutorial and quick reference guide built into the extension.**

**Key Features:**
- Step-by-step tutorials for each panel
- Visual guides with emojis and formatting
- Quick reference cards for common tasks
- Links to external documentation
- Modern card-based UI design
- No need to leave Burp Suite for documentation

---

### About — Extension Information

**Neon-themed information panel showcasing the extension.**

**Key Features:**
- Extension metadata and version information
- Glitch effects and animations
- Neon/cyberpunk aesthetic
- Links to documentation and resources
- Visual showcase of the extension's theme

---

### Update — Auto-Updater

**One-click update system with version checking and hash verification.**

**Key Features:**
- **Automatic Version Checking:**
  - Checks GitHub Releases for new versions
  - Background update notifications
  - Tab title indicator when updates are available

- **Update Process:**
  - Release notes display
  - SHA-256 hash verification for security
  - One-click download and update
  - Manual reload prompt after update

- **Safety Features:**
  - Hash verification before installation
  - Version comparison
  - Update history tracking
  - Rollback information

---

## Context Menu and Integrations

### Context Menu Options

Right-click any HTTP request in Burp Suite (Proxy, Repeater, Intruder, Scanner, etc.) to access:

- **Send to Hefaistos → Forge:** Load request into the fuzzer for payload testing
- **Send to Hefaistos → Anvil:** Manually add request to the logger (auto-capture is enabled by default)

### Integrations

- **Burp Collaborator:** Integrated OOB testing support in Hammer (JWT fuzzing) and Forge (payload testing)
- **Burp Suite Tools:** Seamless integration with Proxy, Repeater, Intruder, Scanner, and other Burp tools
- **Auto-Capture:** Anvil automatically captures requests from all Burp Suite tools without manual intervention
- **Curl Integration:** Curltorepeater seamlessly converts curl commands and sends them through Burp proxy for analysis

---

## Troubleshooting

| Issue | Solution |
|---|---|
| Port in use (Tripod) | Use "Kill Used Ports" and ensure the port field is correct. |
| Curl parsing fails (Curltorepeater) | Check curl command format, ensure URL is properly quoted, verify all flags are supported. |
| No context menu | Restart Burp, check Extender → Errors for load issues. |
| Update fails | Download from Releases, unload/reload the JAR in Burp. |
| Blank panels | Ensure Java 8+, check Extender → Output for stack traces. |
| Slow fuzzing (Forge) | Reduce threads/RPM; consider target/network latency. |
| Request not sent (Curltorepeater) | Check Burp proxy settings, ensure proxy is running, verify network connectivity. |

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
- Enhanced curl command parsing with more options support
- Enhanced reporting/export formats
- Quality-of-life improvements across panels
- Additional curl command features (file uploads, cookies, etc.)

Track progress and suggest features in [GitHub Issues](https://github.com/joelindra/Hefaistos/issues) and [Discussions](https://github.com/joelindra/Hefaistos/discussions).

## License

Licensed under the MIT License. See `LICENSE` for details.

---

## Support

- Issues: [GitHub Issues](https://github.com/joelindra/Hefaistos/issues)
- Discussions: [GitHub Discussions](https://github.com/joelindra/Hefaistos/discussions)
- Documentation: [GitBook — Hefaistos](https://joelindra.gitbook.io/all-tools/hefaistos)

Thanks for using Hefaistos — forge your way to better security! ⚒️🔥
