# Hefaistos v2.2.0

[![License](https://img.shields.io/badge/license-Hades-Red.svg)](LICENSE)
[![Burp Suite Compatible](https://img.shields.io/badge/Burp%20Suite-Compatible-green)](https://portswigger.net/burp)

Hefaistos is a robust, multi-tool Burp Suite extension tailored for penetration testers, bug bounty hunters, and cybersecurity experts. Inspired by the Greek god of forging, it equips users with specialized modules to analyze, exploit, and test web applications efficiently. Featuring a cyberpunk-themed interface with glitch effects and neon accents, Hefaistos streamlines workflows for JWT manipulation, fuzzing, webhook listening, and request logging.

<img width="427" height="640" alt="image" src="https://github.com/user-attachments/assets/4d7f49ff-5bbc-4e0a-b639-b34acd801ced" />

**Codename:** HEFAISTOS  
**Version:** 2.2.0 (Released: August 26, 2025)  
**Creator:** Joel Indra  
**Type:** Burp Suite Exploit eXtension
**Mission:** More time for coffee!
**Compatibility:** Burp Suite Professional / Community Edition (v2023+ recommended)  

## Table of Contents

- [Key Features](#key-features)
- [Installation](#installation)
- [Usage](#usage)
  - [Getting Started](#getting-started)
  - [Forge - Fuzz Heker](#forge---fuzz-heker)
  - [Hammer - JWT Heker](#hammer---jwt-heker)
  - [Tripod - Hook Heker](#tripod---hook-heker)
  - [Anvil - Request Heker](#anvil---request-heker)
  - [Usage & About Tabs](#usage--about-tabs)
  - [Advanced Tips](#advanced-tips)
- [Screenshots](#screenshots)
- [Building from Source](#building-from-source)
- [Changelog](#changelog)
- [Known Issues](#known-issues)
- [Contributing](#contributing)
- [License](#license)
- [Credits & Acknowledgments](#credits--acknowledgments)

## Key Features

Hefaistos integrates seamlessly into Burp Suite with a tabbed interface and context menu options. Core tools include:

- **Forge (Fuzzer Heker)**: Multi-request fuzzer with support for multiple injection points, custom payloads, and attacks like SQLi, XSS, Path Traversal, LDAP Injection, Open Redirect, CRLF Injection, Broken Authentication, and Host Header Injection.
- **Hammer (JWT Heker)**: JWT decoder, vulnerability scanner (e.g., alg:none, weak secrets), fuzzer (kid/jku injection), algorithm confusion attacks, and token builder.
- **Tripod (Hook Heker)**: Local webhook listener for OOB testing (SSRF, XXE, Blind XSS) with port management and process killing.
- **Anvil (Request Heker)**: Automated request logger with summaries, parameter extraction, and a collection panel for notable findings.
- **Usage & About**: In-app documentation, system info, and credits.

Additional capabilities:
- **Context Menu Integration**: "Send to Hefaistos" > "Forge" or "Anvil" from Proxy, Repeater, etc.
- **Auto-Save & Load**: Settings (payloads, configs) persist every 30 seconds and on unload.
- **UI Enhancements**: Dark mode, monospace fonts, glitch effects on hover, and emoji separators (e.g., 💀).
- **Performance**: Multi-threaded fuzzing, progress bars, and cancelable operations.
- **Extensibility**: Open-source codebase for adding new attacks or panels.
- **Security-Focused**: Built-in checks for weak keys (RFC 7518) and vulnerability detection.

Hefaistos stands out for its all-in-one approach, reducing the need for multiple extensions.

## Installation

1. **Download the JAR**:
   - Head to the [Releases page](https://github.com/joelindra/Hefaistos/releases) and download the latest `Hefaistos.jar`.
   - Alternatively, build from source (see [Building from Source](#building-from-source)).

2. **Load in Burp Suite**:
   - Launch Burp Suite.
   - Navigate to `Extender` > `Extensions` tab.
   - Click `Add`, choose `Java` as the type, and select the `Hefaistos.jar` file.
   - Confirm loading; the "Hefaistos" tab should appear.
   - Check the console for "Hefaistos loaded successfully!"

3. **Optional Setup**:
   - For Tripod's port killing: Run Burp with admin/root privileges.
   - Ensure firewalls allow incoming connections for webhooks.

**Requirements**:
- Java 8+ (Burp's built-in JRE works fine).
- No additional dependencies—uses Burp's APIs and standard Java libraries.

If issues arise, check the [Known Issues](#known-issues) section or open a GitHub issue.

## Usage

### Getting Started
- After loading, access tools via the "Hefaistos" tab.
- Use right-click context menus in Burp tools (e.g., Proxy history) to send requests to Forge or Anvil.
- Settings auto-save; no manual export needed unless customizing extensively.
- Monitor Burp's output console for logs (info/errors prefixed with "[Hefaistos]").

### Forge - Fuzz Heker
Forge excels at fuzzing multiple requests with multiple markers, supporting parallel/sequential modes.

**Step-by-Step**:
1. **Add Targets**: Right-click requests > "Send to Hefaistos" > "Send to Forge".
2. **Edit Requests**: Select from dropdown, insert `FUZZ` markers (customizable per-request).
3. **Configure Attacks**: In "Swag" tabs, enable modules, edit payloads (lists or files), set threads/delay.
4. **Launch Scan**: Choose mode (Parallel for speed), rate limit, and start. Monitor progress/stats.
5. **Results**: Filter table by category/target. Export to CSV. Detect issues like reflections or errors.

**Supported Attacks**:
- SQL Injection, XSS, Path Traversal, LDAP Injection, Open Redirect, CRLF Injection, Broken Authentication, Host Header Injection, Unwanted HTTP Methods.
- Custom payloads for flexibility.

**Example**: Fuzz for XSS—load payloads like `<script>alert(1)</script>`, enable module, and scan.

### Hammer - JWT Heker
Hammer provides end-to-end JWT handling with three tabs.

**Decoder Tab**:
- Paste JWT for auto-decoding (header/payload as JSON).
- Verify signatures with secrets/keys.
- Auto-analysis: Detects alg:none, weak algos, etc.

**Security Tests Tab**:
- **Fuzzer**: Tests none/kid/jku injections, generates malicious tokens.
- **Algo Confusion**: Converts RS256 to HS256 using public key as secret.
- **Brute-Force**: Cracks HSxxx secrets with wordlists (file preview support).
- Progress bar and cancel button for long ops.

**Builder Tab**:
- Select HS256/384/512, edit payload JSON, provide secret.
- Generates token with weak-key checks.

**Example**: Decode a token, run fuzzer for forgeries, build a new one with elevated claims.

### Tripod - Hook Heker
Tripod listens for OOB interactions and manages ports.

**Step-by-Step**:
1. **Start**: Set port, click "Start Listener". Get endpoint URL (handles multiple IPs/VPNs).
2. **Test**: Inject URL into targets (e.g., SSRF payloads).
3. **History**: Table shows requests (method, URL, time). Click for full view. Sort/filter available.
4. **Ports**: "Kill Used Ports" lists TCP listeners; select to terminate (admin required).
5. **Stop/Clear**: Halt listener or erase history.

**Example**: Test XXE—start on port 8080, payload `<![CDATA[http://your-ip:8080]]>`, check captured request.

### Anvil - Request Heker
Anvil logs requests for analysis and collection.

**Step-by-Step**:
1. **Capture**: Auto-logs from Burp tools or manual send via context menu.
2. **View**: Table with summaries. Select for tabs: Summary (params), Request, Response.
3. **Collect**: "Add to List" appends summaries to side panel (numbered for reports).
4. **Manage**: Clear list with "Clear History".

**Example**: Log suspicious requests from Repeater, collect params for vuln proof.

### Usage & About Tabs
- **Usage**: Detailed guides..
- **About**: System core (version, creator), weapons (features).

### Advanced Tips
- **Performance**: Limit threads in Forge/Hammer for resource-heavy scans.
- **Customization**: Edit source for new fuzz categories or JWT attacks.
- **VPN/Firewall**: For Tripod, ensure ports are open; use `netstat` externally if needed.
- **Error Handling**: Check console for stack traces; report issues on GitHub.
- **Integration**: Combine tools—e.g., fuzz JWTs in Forge, verify in Hammer.

## Screenshots

<img width="558" height="38" alt="image" src="https://github.com/user-attachments/assets/a46861ed-2dd3-4032-9ff9-6da711c8db22" />
<img width="1918" height="1034" alt="image" src="https://github.com/user-attachments/assets/7658f9f6-9465-4074-8e8b-41a42419affd" />
<img width="1807" height="930" alt="image" src="https://github.com/user-attachments/assets/995b6f53-60b8-4ee9-a87d-fb29e806ecaf" />
<img width="1821" height="843" alt="image" src="https://github.com/user-attachments/assets/49660505-0031-45a8-b741-0cd8d6dfa50e" />
<img width="1838" height="1005" alt="image" src="https://github.com/user-attachments/assets/5a294392-368d-42a4-b5ea-6ab1a12aec46" />
<img width="1641" height="978" alt="image" src="https://github.com/user-attachments/assets/9435f68b-5818-4fc6-88b7-caa53b18346a" />

## Credits & Acknowledgments

- **Creator**: Joel Indra – [GitHub](https://github.com/joelindra) | [Website](https://docs.joelindra.id)
- **Libraries**: Jackson for JSON, JJWT for JWT handling, Swing for UI.
- **Community**: Thanks to PortSwigger and the pentesting community.

*Forge your destiny in the digital underworld. Hack! 💀*
