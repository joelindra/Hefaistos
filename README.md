# H3F41ST0S - Burp Suite Extension Toolkit

[![GitHub License](https://img.shields.io/badge/License-Hades-blue?style=flat-square)](https://github.com/joelindra/hefaistos/blob/main/LICENSE)
[![Burp Suite Extension](https://img.shields.io/badge/Burp%20Suite-Extension-orange?style=flat-square)](https://portswigger.net/burp)
[![Java](https://img.shields.io/badge/Java-11+-blue?style=flat-square)](https://www.oracle.com/java/)

<img width="427" height="640" alt="H3F41ST0S Overview" src="https://github.com/user-attachments/assets/4d7f49ff-5bbc-4e0a-b639-b34acd801ced" />

H3F41ST0S is a powerful Burp Suite extension designed for web application security testing. It combines multiple tools into a single, hacker-themed interface, offering functionalities for request logging, JWT analysis, fuzzing, webhook listening, reverse shell handling, payload generation, and AI-assisted request analysis. Perfect for penetration testers and security researchers.

> "Not everything needs to be clarified; sometimes, just let them be with their assumptions."  
> — H3F41ST0S

## Table of Contents

- [Features](#features)
  - [Forge - Fuzz Heker](#forge---fuzz-heker)
  - [Hammer - JWT Heker](#hammer---jwt-heker)
  - [Tripod - Hook Heker](#tripod---hook-heker)
  - [Anvil - Request Heker](#anvil---request-heker)
  - [Assistant - AI Heker](#assistant---ai-heker)
  - [Additional Tabs](#additional-tabs)
- [Installation](#installation)
- [Usage](#usage)
  - [Quick Start](#quick-start)
  - [Example: Using Forge (Fuzzer)](#example-using-forge-fuzzer)
  - [Example: Using Assistant (AI Analysis)](#example-using-assistant-ai-analysis)
- [Configuration](#configuration)
- [Screenshots](#screenshots)
- [Contributing](#contributing)
- [License](#license)

## Features

H3F41ST0S integrates several tools, each accessible via its own tab in Burp Suite. Below is an overview of each tool's capabilities.

### Forge - Fuzz Heker
A robust web application fuzzer supporting multiple requests and injection points.

| Feature | Description |
|---------|-------------|
| Attack Modes | SQL Injection, XSS, Path Traversal, LDAP Injection, Open Redirect, SSTI, Verbose Error, CRLF Injection, Deserialization, XXE, Command Injection, Unwanted HTTP Methods, Broken Authentication, Host Header Injection |
| Marker System | Uses `§` for primary injection points; supports specific markers for targeted attacks |
| Execution | Parallel attacks with configurable threads and rate limits |
| Results | Color-coded table, filtering by target/category, CSV export, live statistics |

### Hammer - JWT Heker
A comprehensive tool for JSON Web Token (JWT) analysis and attacks.

| Feature | Description |
|---------|-------------|
| Decoder | Instant header/payload decoding, pretty-printed output, signature verification |
| Security Tests | Fuzzing checklist (e.g., 'none' algorithm, kid/jku/jwk injections, algorithm confusion), weak secret brute-forcing |
| Key Support | Symmetric (HS256/384/512) and asymmetric (RS256/ES256) algorithms |
| Wordlists | Paste or load from file for brute-force attacks |

### Tripod - Hook Heker
A multi-purpose utility for webhook listening, reverse shell handling, and payload generation.

| Feature | Description |
|---------|-------------|
| Modes | HTTP Webhook (captures incoming requests), Reverse Shell (interactive terminal) |
| Request History | Sortable table with full request details |
| Payload Generator | Reverse/Bind Shell, Web Shell, Data Exfiltration; supports Linux/Windows, Base64/URL encoding |
| Port Management | Kill processes on used ports for conflict resolution |

### Anvil - Request Heker
A request logging and analysis tool for capturing and examining HTTP traffic.

| Feature | Description |
|---------|-------------|
| Logging | Auto-captures requests from Burp tools (Proxy, Repeater, etc.) |
| Interface | Sortable log table, detailed viewers (Summary, Request, Response) |
| Collection | Save interesting request summaries in a side panel |
| Management | Clear history, copy collected items to clipboard |

### Assistant - AI Heker
Integrates AI for automated security analysis of HTTP requests.

| Feature | Description |
|---------|-------------|
| Providers | Gemini 2.5 Pro (primary), ChatGPT, Claude |
| Prompt System | Customizable templates, editable prompt area |
| Workflow | Send requests from Burp, edit prompts, submit for AI analysis |
| Settings | Configure API keys and manage templates |

### Additional Tabs
- **Usage**: Provides detailed, styled instructions for all tools.
- **About**: Features a glitchy, hacker-themed UI with system info and external links.
- **Update**: Automatic update checker with GitHub integration, release notes, and one-click downloads.

## Installation

1. **Prerequisites**:
   - Burp Suite Professional or Community Edition.
   - Java 11+ (Burp's runtime environment).

2. **Download**:
   - Clone the repository: `git clone https://github.com/joelindra/hefaistos.git`
   - Or download the pre-built JAR from [Releases](https://github.com/joelindra/hefaistos/releases).

3. **Load in Burp Suite**:
   - Open Burp Suite > Extender > Extensions > Add.
   - Select "Java" as the extension type and load the JAR file.
   - The "H3F41ST0S" tab will appear in Burp Suite.

## Usage

Navigate to the "H3F41ST0S" tab in Burp Suite to access all tools. Each tool operates independently with its own panel or sub-tab.

### Quick Start
- Right-click any request in Burp (e.g., Proxy, Repeater) and select "Send to [Tool]" (e.g., Send to Forge, Send to Hammer, etc.).
- Use the **Usage** tab for detailed instructions on each tool.

### Example: Using Forge (Fuzzer)
1. Send one or more requests to Forge via the context menu.
2. Mark injection points in the request with `§`.
3. Enable desired attacks in the Swag tabs and add payloads.
4. Configure threads/rate limits and click "Start" to begin fuzzing.
5. Analyze results in the color-coded table; export to CSV if needed.

### Example: Using Assistant (AI Analysis)
1. Go to Assistant > Settings and enter your API key (e.g., Gemini).
2. Send a request via the context menu to populate the prompt area.
3. Select a prompt template or edit the prompt manually.
4. Click "Submit to AI" to receive the analysis in the response panel.

For detailed workflows, refer to the **Usage** tab.

## Configuration
- **API Keys (Assistant)**: Set in Assistant > Settings tab.
- **Wordlists (Hammer/Forge)**: Paste directly or load from a file.
- **Ports (Tripod)**: Ensure ports are accessible; use "Kill Used Ports" to resolve conflicts (use cautiously).

## Screenshots
<img width="1918" height="953" alt="image" src="https://github.com/user-attachments/assets/584e2333-c254-4a44-8e38-bc214d768aab" />
<img width="1919" height="977" alt="image" src="https://github.com/user-attachments/assets/291599a9-c26c-469b-960a-d3ba208a81e3" />
<img width="1917" height="973" alt="image" src="https://github.com/user-attachments/assets/7a8aaf08-68c7-4b71-80df-a2af8c105e66" />
<img width="1918" height="975" alt="image" src="https://github.com/user-attachments/assets/aa2f16af-81bb-401f-b6f4-a7d14bf3ccb4" />
<img width="1916" height="950" alt="image" src="https://github.com/user-attachments/assets/08412ef0-c891-4606-a7c3-5f22461c7f2f" />

Report bugs or suggest features in the [Issues](https://github.com/joelindra/hefaistos/issues) section.

## License
Licensed under the Hades License
© 2025 Joel Indra | Underworld & AI  

For more information, visit [Website](https://docs.joelindra.id) or [GitHub](https://github.com/joelindra/hefaistos).
