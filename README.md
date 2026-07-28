# ⚒️ **Hefaistos v5.4.0** — The Blacksmith of Burp Suite

<div align="center">
  <img width="720" alt="Hefaistos Cyberpunk Overview" src="https://github.com/user-attachments/assets/4d7f49ff-5bbc-4e0a-b639-b34acd801ced" />
  <br /><br />
  <p><i>In the neon-lit underbelly of the web, one forge stands above all.<br>
  Forging tools to hammer vulnerabilities, listen for callbacks in the dark, and automate the shadows.</i></p>

  [![Version](https://img.shields.io/badge/version-5.4.0-blueviolet?style=for-the-badge&logoColor=white)](https://github.com/joelindra/Hefaistos)
  [![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)](https://github.com/joelindra/Hefaistos/blob/main/LICENSE)
  [![Burp Suite](https://img.shields.io/badge/Burp%20Suite-Compatible-brightgreen?style=for-the-badge&logo=burpsuite)](https://portswigger.net/burp)
  [![Java](https://img.shields.io/badge/Java-11%2B-orange?style=for-the-badge&logo=openjdk)](https://openjdk.org/)

  <br />
  <a href="https://github.com/joelindra/Hefaistos/releases/latest"><img src="https://img.shields.io/github/downloads/joelindra/Hefaistos/total?color=ff69b4&style=for-the-badge&logo=github" alt="Downloads"></a>
</div>

---

## 🔥 **Overview**

**Hefaistos** is a sophisticated, modular extension for **Burp Suite** — meticulously crafted for elite web application security testing. Drawing inspiration from the mythical blacksmith of the gods, it transforms raw requests into precision weapons.

With a sleek cyberpunk aesthetic and professional-grade features, Hefaistos empowers pentesters and bug bounty hunters to **fuzz smarter**, **exploit deeper**, **analyze faster**, and **report cleaner**.

---

## 🚀 **What's New in v5.4.0 — xRepeater Overhaul**

This update modernizes the **xRepeater** tab into a full-featured request workstation:

- **✨ xRepeater Redesign** — A modern split-panel layout: **Curl to Repeater** on the left, **Postman Collection** on the right. Rounded cards, pulse-status indicators, and a polished cyberpunk UI.
- **📦 Postman Collection Importer** — Load a `.json` Postman collection and instantly enumerate every API endpoint. Automatic `{{variable}}` resolution from collection environment variables. Folder nesting, Bearer / Basic auth, and raw / urlencoded / formdata bodies are all parsed and displayed in a checkbox-selectable table.
- **🎯 Multi-Select Send** — Tick one, several, or all endpoints and dispatch them in one click:
  - **Send Selected → Repeater** — pushes selected requests straight into Burp Repeater for manual tuning.
  - **Send Selected → Proxy** / **Send All → Proxy** — fires requests through the Burp proxy and records every response in the built-in **History** log (status code, method, name, URL).
- **🛠️ Curl Parser Improvements** — More robust handling of methods, headers, auth (`-u`), data (`-d` / `--data-raw`), and quoted URLs.
- **🧹 Codebase Cleanup** — Removed unused panel files (`AboutPanel`, `AnvilPanel`, `AssistantPanel`, `TMPanel`, `TripodPanel`, `UsagePanel`) for a leaner, cleaner codebase.

---

## 🛠️ **The Arsenal**

### 1. ⚔️ **Forge** — Advanced HTTP Fuzzer
A high-velocity, precision fuzzer built for complex injection campaigns.

- Multi-target parallel fuzzing with unique color-coded sessions
- No-marker attack suites: **Blind XSS (Referer)**, **Authentication Token Manipulation**, **Parameter Pollution**
- Rich payload library (SQLi, XSS, Path Traversal, SSRF) + custom wordlists
- RPM throttling & smart delay controls to evade WAFs
- Real-time grep highlighting for instant payload reflection detection
- Native HTTP viewers with full Burp right-click context menu

### 2. 🔨 **Hammer** — Ultimate JWT Toolkit
The most comprehensive JWT analysis and exploitation suite.

### 3. 🔌 **xRepeater** — Curl Converter & Postman Runner
A dual-purpose request workstation.

- **Curl to Repeater** — Paste any `curl` command and instantly convert it into a complete HTTP request with method, headers, auth, and body. Send it through the proxy and view the live response.
- **Postman Collection Runner** — Import a Postman collection, resolve environment variables, select endpoints via checkboxes, and send them to **Repeater** or **Proxy** in bulk. Every proxied request is logged in the History panel with status codes.

### 4. 🧰 **Misc** — Traffic Handlers & Utilities
Proxy traffic handlers, request reshaping, and auxiliary tools accessible from the Misc tab.

### 5. 🔄 **Update** — One-Click Updater
Stay on the bleeding edge with the built-in update checker.

---

## ⚡ **Quick Start**

1. **Download** the latest `.jar` from [Releases](https://github.com/joelindra/Hefaistos/releases)
2. **Load** into Burp Suite (Extender → Extensions → Add → Select JAR)
3. **Navigate** to the **xRepeater** tab to start converting curl commands or importing Postman collections
4. **Right-click** any request in Burp → **Send to Hefaistos** → Choose your weapon (Forge / Hammer)
5. **AI Features** (optional): Add your Gemini API key in **Assistant → Settings**

> [!TIP]
> Use the built-in **Update** tab to stay on the bleeding edge.

---

## 🔧 **Requirements**

- **Java**: OpenJDK 11 or higher
- **Burp Suite**: Community or Professional (2023.4+ recommended)
- **Build** (optional): Maven

---

## 📋 **Tab Reference**

| Tab | Purpose |
|-----|---------|
| **Forge** | Advanced HTTP fuzzer with multi-target attacks |
| **Hammer** | JWT analysis, decoding, and exploitation |
| **Misc** | Traffic handlers and utility tools |
| **xRepeater** | Curl-to-request converter & Postman collection runner |
| **Update** | Plugin update checker |

---

## 📄 **License & Credits**

**MIT License** — Free to use, modify, and distribute.

Forged with passion by **[Joel Indra](https://github.com/joelindra)**.

---

<div align="center">

**Forge your path through the matrix.**  
**⚒️ Neon never sleeps. 🔥**

</div>

<p align="center">
  <a href="https://github.com/joelindra/Hefaistos/issues">🐛 Report Bug</a> • 
  <a href="https://github.com/joelindra/Hefaistos/discussions">💡 Suggest Feature</a>
</p>
