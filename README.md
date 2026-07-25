# ⚒️ **Hefaistos v5.3.9** — The Blacksmith of Burp Suite

<div align="center">
  <img width="720" alt="Hefaistos Cyberpunk Overview" src="https://github.com/user-attachments/assets/4d7f49ff-5bbc-4e0a-b639-b34acd801ced" />
  <br /><br />
  <p><i>In the neon-lit underbelly of the web, one forge stands above all.<br>
  Forging tools to hammer vulnerabilities, listen for callbacks in the dark, and automate the shadows.</i></p>

  [![Version](https://img.shields.io/badge/version-5.3.9-blueviolet?style=for-the-badge&logoColor=white)](https://github.com/joelindra/Hefaistos)
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

## 🚀 **What's New in v5.3.9 — Forge Modernization**

This update refines the core experience with production-ready polish:

- **✨ Native HTTP Viewers** — All fuzzer results now use Burp Suite’s powerful `IMessageEditor`: full syntax highlighting, proper formatting, and the complete right-click context menu (Send to Repeater, Intruder, Scanner, etc.).
- **🔄 Synchronized Dual Tabs** — Elegant side-by-side comparison: **Original vs. Modified Request** and **Original vs. Modified Response**.
- **⚡ Optimized Attack Logic** — Streamlined Parameter Pollution and Host Header Injection modules for faster, cleaner, and more focused scans.
- **🛠️ UI & Stability Enhancements** — Improved layout consistency, better baseline response handling, and overall visual refinement.

---

## 🛠️ **The Arsenal**

### 1. ⚔️ **Forge** — Advanced HTTP Fuzzer
A high-velocity, precision fuzzer built for complex injection campaigns.

- Multi-target parallel fuzzing with unique color-coded sessions
- No-marker attack suites: **Blind XSS (Referer)**, **Authentication Token Manipulation**, **Parameter Pollution**
- Rich payload library (SQLi, XSS, Path Traversal, SSRF) + custom wordlists
- RPM throttling & smart delay controls to evade WAFs
- Real-time grep highlighting for instant payload reflection detection

### 2. 🔨 **Hammer** — Ultimate JWT Toolkit
The most comprehensive JWT analysis and exploitation suite.

### 3. 🔌 **Curltorepeater** — Instant Command Converter
Zero-friction bridge from CLI/browser to Burp.

- Intelligent parsing of `curl` commands into complete Burp requests
- Automatic proxy routing
- Full support for custom methods, headers, auth, and body data

---

## ⚡ **Quick Start**

1. **Download** the latest `.jar` from [Releases](https://github.com/joelindra/Hefaistos/releases)
2. **Load** into Burp Suite (Extender → Add → Select JAR)
3. **Right-click** any request → **Send to Hefaistos** → Choose your weapon
4. **AI Features** (optional): Add your Gemini API key in **Assistant → Settings**

> [!TIP]
> Use the built-in **Update** tab to stay on the bleeding edge.

---

## 🔧 **Requirements**

- **Java**: OpenJDK 11 or higher
- **Burp Suite**: Community or Professional (2023.4+ recommended)
- **Build** (optional): Maven

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
