# ⚒️ **Hefaistos v5.4.1** — The Blacksmith of Burp Suite

<div align="center">
  <img width="720" alt="Hefaistos Cyberpunk Overview" src="https://github.com/user-attachments/assets/4d7f49ff-5bbc-4e0a-b639-b34acd801ced" />
  <br /><br />
  <p><i>Forging precision weapons to uncover hidden vulnerabilities, automate attack workflows, and dominate the application security landscape.</i></p>

  [![Version](https://img.shields.io/badge/version-5.4.0-blueviolet?style=for-the-badge&logoColor=white)](https://github.com/joelindra/Hefaistos)
  [![Burp Suite](https://img.shields.io/badge/Burp%20Suite-Compatible-brightgreen?style=for-the-badge&logo=burpsuite)](https://portswigger.net/burp)
  [![Java](https://img.shields.io/badge/Java-11%2B-orange?style=for-the-badge&logo=openjdk)](https://openjdk.org/)
  [![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)](https://github.com/joelindra/Hefaistos/blob/main/LICENSE)
  [![Downloads](https://img.shields.io/github/downloads/joelindra/Hefaistos/total?color=ff69b4&style=for-the-badge&logo=github)](https://github.com/joelindra/Hefaistos/releases/latest)
</div>

---

## 🔥 **Overview**

**Hefaistos** is an advanced, high-performance security extension for **Burp Suite** engineered for modern penetration testers, red teamers, and bug bounty researchers. Named after the mythical blacksmith of the gods, Hefaistos transforms everyday HTTP traffic into automated, targeted attack vectors.

Combining a sleek cyberpunk interface with enterprise-grade testing engines, Hefaistos accelerates security assessments across API endpoints, authentication mechanisms, token security, and multi-vector fuzzing campaigns.

---

## ⚡ **The Arsenal**

```
 ┌─────────────────────────────────────────────────────────────────────────┐
 │                            HEFAISTOS SUITE                              │
 ├──────────────┬──────────────┬──────────────┬──────────────┬─────────────┤
 │   ⚔️ FORGE   │   🔨 HAMMER  │ 🔌 xREPEATER │   🧰 MISC    │  🔄 UPDATE  │
 │  Fuzzing &   │     JWT      │  cURL & API  │  Reshapers & │   In-App    │
 │ Auto-Attacks │ Exploitation │  Runner Hub  │ Calculators  │  Auto-Sync  │
 └──────────────┴──────────────┴──────────────┴──────────────┴─────────────┘
```

---

### 1. ⚔️ **Forge** — Advanced HTTP Fuzzer & Attack Automation
A multi-threaded, target-aware fuzzing engine built for high-velocity injection and vulnerability discovery.

#### 🎯 **Target & Execution Engine**
- **Multi-Target Workspace**: Manage multiple request targets simultaneously with custom color-coded tabs.
- **Marker & Markerless Fuzzing**: Target positional injection markers (`§...§`) or run fully automated markerless attack suites.
- **Smart Baseline Comparison**: Evaluates status codes, response lengths, reflection grep matches, and response diffs against clean baselines.
- **WAF Evasion & Throttling**: Granular control over requests per minute (RPM), concurrency threads, and inter-request delays.

#### 🛡️ **Automated Attack Cards (No Marker)**
- **MA & PT (Mass Assignment & Parameter Testing)**:
  - Automatically parses and extracts all unique parameters from response bodies (JSON schemas, HTML `<input>`, `<textarea>`, `<select>`, and URL query strings).
  - Intelligently mutates parameter values: appends `"Hades"` to string/character values and `"1337"` to numeric/digit values.
  - Generates dedicated 1-to-1 test requests per unique parameter, dynamically injecting mutated payloads into JSON bodies, Form URL-encoded bodies, or URL query parameters.
- **Blind XSS on Referer**: Injects out-of-band Blind XSS callbacks across Referer and routing headers.
- **Edit Authentication**: Tests privilege escalation and authentication bypass through Bearer token manipulation, header stripping, and credential corruption.
- **Parameter Pollution (HPP)**: Evaluates backend parameter precedence and collision vulnerabilities.
- **Broken Authentication**: Probes endpoint access control against stripped or invalid authorization states.
- **Host Header Injection**: Tests for password-reset poisoning, cache poisoning, and internal SSRF routing via custom Host and X-Forwarded headers.
- **Unwanted HTTP Method**: Tests unsupported and dangerous HTTP verbs (`OPTIONS`, `PUT`, `DELETE`, `TRACE`, `CONNECT`, `PATCH`).
- **Verbose Error Analysis**: Delivers targeted payloads to provoke detailed stack traces, database errors, and debug disclosures.

#### 💣 **Marker-Based Payload Suites**
- **Injection Categories**: SQL Injection (Error, Boolean, Time, Union), XSS (DOM, Reflected, Event Handlers), SSTI (Jinja, Twig, Freemarker, etc.), Command Injection, LDAP Injection, XML External Entity (XXE), and Unsafe Deserialization.
- **Traversal & Redirection**: Directory / Path Traversal, Open Redirect, and CRLF Injection.
- **Custom Payload Sets**: Load custom wordlists, multi-positional payload sets, and specialized attack dictionaries.

---

### 2. 🔨 **Hammer** — Ultimate JWT Toolkit
A dedicated suite for inspecting, tampering, and cracking JSON Web Tokens (JWT).

- **Real-Time Token Inspector**: Visual decoder with formatted JSON tree editing for JWT Headers and Claims.
- **Algorithm Confusion Attacks**: Automated testing for `RS256` $\to$ `HS256` key confusion using public keys / X.509 certificates.
- **Signature Bypass**: One-click generation of `None` algorithm tokens and stripped signature attacks.
- **Header Injection Vectors**: Automated injection tests for `jwk`, `jku`, `x5u`, and `kid` directory traversal vectors.
- **High-Speed Secret Cracker**: Multi-threaded dictionary brute-force engine for cracking HMAC secrets (`HS256`, `HS384`, `HS512`).
- **Collaborator Integration**: Out-of-band interaction testing for SSRF and blind token validation flaws.

---

### 3. 🔌 **xRepeater** — Request Workstation & API Runner
A streamlined dual-pane workstation designed for rapid command conversion and bulk API testing.

- **Curl to Repeater**:
  - Convert raw `curl` commands into structured HTTP requests instantly.
  - Automatically parses methods, headers, Basic/Bearer authentication, JSON bodies, form data, and query strings.
  - Live preview and direct dispatch to Burp Proxy or Burp Repeater.
- **Postman Collection Runner**:
  - Native `.json` Postman collection importer supporting nested folder structures.
  - Automatic `{{variable}}` environment resolution.
  - Interactive checkbox table to select specific endpoints or entire collections.
  - **Batch Execution**: Dispatch selected requests to Burp Repeater or fire them through the Burp Proxy with live history logging (Status, Method, URL, Name).

---

### 4. 🧰 **Misc** — Traffic Reshaping & Security Utilities
Auxiliary tools and dynamic traffic manipulation handlers.

- **MyReshaper Traffic Handler**: Rule-based request and response rewriting using regex pattern matching and header modifications.
- **DigiPwn Traffic Handler**: Automatic interceptor and payload transformer for specialized assessments.
- **Security Calculators**: Full implementation of **CVSS v3.1** and **CVSS v4.0** scoring metrics with vector string generators.
- **Cryptographic Tools**: Real-time hash calculation (MD5, SHA-1, SHA-256, SHA-512) and encoding/decoding utilities.

---

### 5. 🔄 **Update** — In-App System Updater
Seamlessly stay up-to-date with official releases directly inside Burp Suite.

- **One-Click Check**: Real-time release comparison against the latest GitHub version.
- **Automated Download**: Download new versions directly within the UI.
- **Live Reload**: Unload and update the extension seamlessly without restarting Burp Suite.

---

## 🚀 **Quick Start**

1. **Download**: Grab the latest `Hefaistos.jar` from [Releases](https://github.com/joelindra/Hefaistos/releases/latest).
2. **Install in Burp Suite**:
   - Go to `Extensions` $\rightarrow$ `Installed` $\rightarrow$ `Add`.
   - Select `Java` as the extension type.
   - Choose `Hefaistos.jar` and click `Next`.
3. **Launch**:
   - Access the **Hefaistos** tab from the top navigation bar.
   - Right-click any HTTP request in Proxy, Repeater, or Target $\rightarrow$ **Send to Hefaistos** $\rightarrow$ **Forge** / **Hammer**.

---

## ⚙️ **Requirements & Compatibility**

| Requirement | Supported Version |
|:---|:---|
| **Java Runtime** | OpenJDK 11 or higher (Java 17 / 21 fully supported) |
| **Burp Suite** | Burp Suite Professional / Community Edition (2023.4+) |
| **Operating System** | Windows, Linux, macOS |

---

## 📋 **Workspace Matrix**

| Tab | Primary Capabilities |
|:---|:---|
| ⚔️ **Forge** | Multi-target HTTP fuzzer, **MA & PT**, automated attack cards, marker-based injections |
| 🔨 **Hammer** | JWT decoding, algorithm confusion, header injection, HMAC dictionary cracking |
| 🔌 **xRepeater** | cURL command converter, Postman collection batch runner, history logger |
| 🧰 **Misc** | MyReshaper & DigiPwn handlers, CVSS v3.1/v4.0 calculators, hash tools |
| 🔄 **Update** | Version checker and in-app automated updater |

---

## 📄 **License**

This project is licensed under the **[MIT License](LICENSE)**.

<div align="center">
  <br>
  <b>⚒️ Forged for Excellence. Engineered for Impact. 🔥</b>
</div>
