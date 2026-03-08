# ⚒️ Hefaistos v5.3.4 — The Blacksmith of Burp Suite

<div align="center">
  <img width="600" alt="Hefaistos Cyberpunk Overview" src="https://github.com/user-attachments/assets/4d7f49ff-5bbc-4e0a-b639-b34acd801ced" />
  <br />
  <p><i>Forging tools to hammer vulnerabilities, listen for callbacks, and automate the shadows.</i></p>

  [![Version](https://img.shields.io/badge/version-5.3.4-blueviolet?style=for-the-badge&logoColor=white)](https://github.com/joelindra/Hefaistos)
  [![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)](https://github.com/joelindra/Hefaistos/blob/main/LICENSE)
  [![Burp Suite](https://img.shields.io/badge/Burp%20Suite-Compatible-brightgreen?style=for-the-badge&logo=burpsuite)](https://portswigger.net/burp)
  [![Java](https://img.shields.io/badge/Java-11%2B-orange?style=for-the-badge&logo=openjdk)](https://openjdk.org/)
</div>

---

## 🔥 Overview

**Hefaistos** is an advanced, modular suite for **Burp Suite**, meticulously engineered for modern web application security testing. Inspired by the mythical blacksmith of the gods, this extension forges a powerful arsenal of tools to automate fuzzing, manipulate JWTs, handle reverse shells, and leverage AI-powered analysis—all wrapped in a sleek, cyberpunk-inspired UI.

Whether you're a seasoned pentester or a bug bounty hunter, Hefaistos streamlines your workflow and amplifies your impact.

---

## 🚀 What's New in v5.3.4

The **Forge Update** brings massive improvements across the entire suite:

- **🎯 TM (Target Manager)**: Modern 3-column reporting tool with integrated CVSS v3.1 calculator, vulnerability details editor, and live report preview.
- **🎯 Multi-Target Forge**: Run parallel fuzzing campaigns across different targets simultaneously with color-coded tracking.
- **⚡ Hammer Editor**: Real-time JWT header/payload editor with instant signature regeneration.
- **🐚 Tripod Interactive**: Full reverse shell handler with an interactive terminal and payload generator.
- **📋 Anvil Collected Items**: Curated findings panel for report-ready request collection.
- **🎨 UI Refinement**: Modernized theme-aware components, elevated rounded cards, and improved performance.

---

## 🛠️ The Arsenal (Core Modules)

### 1. ⚔️ Forge — Advanced Fuzzer

A high-performance HTTP fuzzer designed for complex injection testing.

- **Multi-Target Support**: Fuzz multiple requests in parallel with unique color IDs.
- **Smart Payloads**: Pre-built categories (SQLi, XSS, Path Traversal, SSRF) + Custom wordlists.
- **RPM Throttling**: Precision control over request rates to avoid detection/WAF triggers.
- **Grep Highlighting**: Instantly spot reflected payloads in real-time results.

### 2. 🎯 TM — Target Manager & Reporting

A modern workspace for documenting findings and calculating risk.

- **3-Column Layout**: Effortlessly manage Vulnerability Details, CVSS Calculation, and Live Preview in one view.
- **CVSS v3.1 Calculator**: Intelligent scoring with pill-style metric selectors and real-time severity badges.
- **Live Report Preview**: Real-time markdown/text preview of the finished vulnerability report.
- **One-Click Export**: Quickly copy perfectly formatted findings to your clipboard for report writing.

### 3. 🔨 Hammer — JWT Toolkit

The ultimate suite for JSON Web Token analysis and exploitation.

- **Real-time Editor**: Modify claims and headers with instant preview and signing.
- **Automated Attacks**: Alg:None, Stripped Signature, Key Injection, and Brute-force.
- **JKU/JWK Spoofing**: Integrated Burp Collaborator support for OOB token attacks.
- **Security Checklists**: Comprehensive automated vulnerability scanning for JWTs.

### 4. 🔭 Tripod — Listener & Payload Gen

Your command center for Out-of-Band (OOB) testing and reverse shells.

- **Dual Mode**: HTTP Webhook listener for callbacks + Interactive Reverse Shell handler.
- **Payload Engine**: Multi-platform templates (Linux, Windows, Web Shells) with 8-char Correlation IDs.
- **Port Manager**: Built-in utility to scan and terminate conflicting processes on used ports.
- **Terminal UI**: Searchable, color-coded terminal with auto-reconnection.

### 5. 🔌 Curltorepeater — Speed Converter

Zero-friction conversion of browser/CLI commands.

- **Smart Parsing**: Converts standard `curl` commands into full Burp requests.
- **Proxy Automation**: Automatically routes converted requests through Burp Proxy.
- **Full Support**: Handles headers, body data, auth flags, and custom methods.

### 6. ⚒️ Anvil — Request Logger

Intelligent capture and organization of your testing traffic.

- **Auto-Capture**: Passive logging from Proxy, Repeater, Intruder, and Scanner.
- **Curated Lists**: Select interesting requests to build a report-ready collection.
- **Manual Input**: Paste raw requests for quick parsing and analysis.

---

## ⚡ Quick Start

1. **Install**: Download the latest `.jar` from [Releases](https://github.com/joelindra/Hefaistos/releases) and load it into Burp Suite.
2. **Configure**: Go to the **Update** or **About** panel to check your version and settings.
3. **Analyze**: Right-click any request → **Send to Hefaistos** → Choose your tool.
4. **Automate**: For AI features, get a Gemini API key and add it in the **Assistant → Settings** tab.

---

## 🔧 Installation & Requirements

- **Java Version**: OpenJDK 11 or higher.
- **Burp Suite**: Community or Professional (2023.x recommended).
- **Dependencies**: SnakeYAML (included in the fat JAR).

> [!TIP]
> Use the **Update** panel within the extension to keep Hefaistos at the cutting edge.

---

## 📄 License & Credits

Licensed under the **MIT License**. Created with 🔥 by [Joel Indra](https://github.com/joelindra).

**Support the forge:**

- 🐛 [Report a Bug](https://github.com/joelindra/Hefaistos/issues)
- 💡 [Suggest a Feature](https://github.com/joelindra/Hefaistos/discussions)

---

<p align="center">
  <i>Forge your way to better security. ⚒️🔥</i>
</p>
