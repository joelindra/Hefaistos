# HEFAISTOS - v2.3.0

[![GitHub](https://img.shields.io/badge/GitHub-joelindra-blue?style=flat&logo=github)](https://github.com/joelindra)
[![Website](https://img.shields.io/badge/Website-docs.joelindra.id-green?style=flat&logo=google-chrome)](https://docs.joelindra.id)
[![License](https://img.shields.io/badge/License-Hades-red?style=flat)](LICENSE)

## Table of Contents
- [Overview](#overview)
- [Features](#features)
  - [Forge - Fuzz Heker](#forge---fuzz-heker)
  - [Hammer - JWT Heker](#hammer---jwt-heker)
  - [Tripod - Hook Heker](#tripod---hook-heker)
  - [Anvil - Request Heker](#anvil---request-heker)
- [Installation](#installation)
- [Usage](#usage)
  - [General Navigation](#general-navigation)
  - [Forge - Fuzz Heker](#forge---fuzz-heker-1)
  - [Hammer - JWT Heker](#hammer---jwt-heker-1)
  - [Tripod - Hook Heker](#tripod---hook-heker-1)
  - [Anvil - Request Heker](#anvil---request-heker-1)
- [Credits](#credits)
- [License](#license)

## Overview
H3F41ST0S is a powerful Burp Suite extension designed for advanced web security testing. It combines multiple tools into one suite, focusing on fuzzing, JWT exploitation, webhook listening, and request logging. Built with a cyberpunk aesthetic, it's perfect for penetration testers and security researchers who want to dominate web app vulnerabilities.

<img width="427" height="640" alt="image" src="https://github.com/user-attachments/assets/4d7f49ff-5bbc-4e0a-b639-b34acd801ced" />

**Codename:** H3F41ST0S  
**Creator:** Joel Indra xD  
**Type:** Burp Suite Exploit Module  
**Mission:** Dominate Web Security Testing  
**Compatibility:** Burp Suite Pro/Community  

## Features
H3F41ST0S includes four main tools (referred to as "WEAPONS" in the extension):

### Forge - Fuzz Heker
- A multi-threaded fuzzing tool for crafting malicious HTTP payloads.
- Supports multiple requests and injection points simultaneously.
- Attack modes: Sniper, Battering Ram, Pitchfork, Cluster Bomb.
- Categories: SQL Injection, XSS, Path Traversal, LDAP Injection, Open Redirect, Unwanted HTTP Methods, Verbose Errors, CRLF Injection, Broken Authentication, Custom Payloads, Host Header Injection.
- Features: Auto-detect parameters, positional markers, payload sets, parallel execution, results export to CSV.

### Hammer - JWT Heker
- Comprehensive JWT analysis, attack, and crafting toolkit.
- Decoder: Instant decoding, security analysis, signature verification.
- Security Tests: JWT Fuzzer (none alg, kid/jku injection, algo confusion), Weak Secret Brute Force.
- Builder: Craft custom JWTs with HSxxx algorithms, key length validation.

### Tripod - Hook Heker
- Stealth HTTP listener and port management system.
- Creates local endpoints for OOB testing (SSRF, Blind XSS, XXE).
- Captures and dissects requests in real-time.
- Port management: View and kill processes using TCP ports (with caution).

### Anvil - Request Heker
- Request logging and analysis tool.
- Automatically captures requests from Burp tools.
- Displays logs with sortable table, detailed viewers (Summary, Request, Response).
- Collect interesting requests into a side panel for reporting.

## Installation
1. **Download the JAR:**
   - Clone or download the repository from [GitHub](https://github.com/joelindra).
   - Build the JAR file using your preferred Java build tool (e.g., Maven or Gradle), or download a pre-built release if available.

2. **Load into Burp Suite:**
   - Open Burp Suite.
   - Go to **Extender > Extensions > Add**.
   - Select the JAR file and load it.
   - The extension will appear as a new tab: **H3F41ST0S**.

**Requirements:**
- Java 8 or higher.
- Burp Suite Professional or Community Edition.

## Usage
### General Navigation
- The extension opens with an **About** tab showing system info and features.
- Switch to the **Usage** tab for detailed instructions on each tool.
- Each tool has its own sub-tab under the main extension tab.

### Forge - Fuzz Heker
Forge is a powerful and flexible web application fuzzer designed to handle multiple requests and multiple injection points simultaneously. It offers various attack modes to suit different testing scenarios.

**How It Works: A 5-Step Guide**
1. **Load Your Targets:** In any Burp tool, right-click one or more requests and select the option to send them to Forge (e.g., 'Send to FuzzerVibes').
2. **Define Injection Points:** Select a target request and place markers where payloads should be inserted.
   - Primary Marker (§): Use this for simple, single-point fuzzing. The 'Auto-Detect Parameters' button can automatically place this marker.
   - Positional Markers (§name§): Use distinct named markers for multi-point fuzzing (Pitchfork/Cluster Bomb).
   - Use **Add** to wrap selected text with a marker, and **Clear** to remove only the marker characters, leaving the original text intact.
3. **Configure Attack Modules:** Navigate the 'Swag' tabs. Enable any module (e.g., SQL Injection, XSS) with its checkbox. Edit payload lists directly or load them from a file.
4. **Configure and Launch the Scan:** In 'Scan Control', select your Attack Mode, set the request rate (Req/min), and choose whether to run in parallel. Click 'Start' to begin.
5. **Analyze the Results:** Results appear in real-time. Use filters to narrow down by target or attack category. Click any row to view the full request and response.

**Key Features & Attack Modes**
- **Advanced Marker System:** Each payload-based module supports a specific 'Override Marker', allowing you to run different attacks on different injection points within the same request.
- **Attack Modes Explained:**
  - **Sniper:** Uses one payload list and iterates through each marker one by one.
  - **Battering Ram:** Uses one payload list and injects the same payload into all markers at once.
  - **Pitchfork:** Requires multiple positional markers and a corresponding number of payload sets. It applies payloads in parallel (e.g., user1/pass1, user2/pass2).
  - **Cluster Bomb:** Tests every possible permutation of payloads from all sets. It's thorough but generates many requests.
- **Powerful Results Analysis:** The results table is color-coded by status. A statistics panel provides a live summary of response codes. Context menus allow sending results to other Burp tools.
- **Session Management:** You can **Save** your entire configuration (payloads, settings) and **Export** fuzzing results to a CSV file.

### Hammer - JWT Heker
Hammer is a comprehensive Burp Suite extension for analyzing, attacking, and crafting JSON Web Tokens (JWTs). It provides a user-friendly interface to streamline JWT security testing.

**Decoder Tab: Decode & Analyze**
- This is your primary workspace for inspecting JWTs.
- **Instant Decoding:** Paste a JWT to automatically decode the Header and Payload. The content is pretty-printed for easy reading.
- **Automated Security Analysis:** The tool instantly analyzes the decoded header for critical vulnerabilities. It flags the insecure alg:none algorithm, identifies the algorithm family (symmetric HSxxx vs. asymmetric RSxxx/ESxxx), and suggests relevant attacks.
- **Signature Verification:** Validate a token's integrity by providing the correct key and clicking 'Verify Signature'.
  - For symmetric algorithms (e.g., HS256), use the shared secret.
  - For asymmetric algorithms (e.g., RS256), paste the public key in PEM format.
  - The result will be clearly marked as VALID or INVALID.

**Security Tests Tab: Find Vulnerabilities**
- This tab contains a suite of automated attacks to test for common JWT implementation flaws.
- **JWT Fuzzer:** Generates a list of malicious JWTs based on a checklist of common misconfigurations, including:
  - Algorithm 'none' Attack (including case variations like 'NONE')
  - Signature Stripping (empty signature)
  - 'kid' Path Traversal & SQL Injection Payloads
  - 'jku' & 'jwk' Header Injection and Spoofing
- **Algorithm Confusion (RS256 → HS256):** For tokens signed with an asymmetric algorithm, this attack attempts to forge a new token by signing it with HS256, using the original public key as the HMAC secret.
- **Weak Secret Brute Force:** For tokens signed with symmetric HMAC algorithms (HS256, HS384, HS512), this attempts to guess the secret key. You can paste a small wordlist directly or load a large wordlist from a file.

**Builder Tab: Craft Custom Tokens**
- The Builder allows you to create your own JWTs from scratch for testing.
- **Full Control:** Specify the signing algorithm, edit the JSON payload, and provide a secret key.
- **Built-in Security Check:** For HSxxx algorithms, the builder validates your secret key's length. It will issue a warning if the key is not strong enough according to RFC 7518, preventing the creation of weak tokens.

### Tripod - Hook Heker
Tripod is a versatile webhook listener and port management utility. Its primary purpose is to create a simple, local HTTP endpoint to receive and inspect out-of-band (OOB) requests, essential for testing SSRF, Blind XSS, XXE, and other external interaction-based flaws.

**How to Use the Webhook Listener**
1. **Start the Listener:** Enter a port number (e.g., 8080) and click 'Start Listener'. It binds to 0.0.0.0, making it accessible on all network interfaces.
2. **Get Your Endpoint URL:** The status bar will display all available IP addresses for your machine (e.g., 192.168.1.10). Use the appropriate IP to craft your payload URL.
3. **Trigger an Interaction:** Use this URL as the payload in the application you are testing.
4. **View and Inspect Requests:** Incoming HTTP requests appear in real-time in the 'Request History' table. Click any entry to see the full, raw request.

**Port & Process Management**
- **Stop Listener:** Shuts down the active listener and releases the port.
- **Clear History:** Removes all captured requests from the history table.
- **Kill Used Ports:** This unique feature helps resolve 'port in use' errors.
  - It opens a dialog showing all processes currently listening on TCP ports on your system.
  - The list includes the Port, PID, and Process Name.
  - You can select one or more processes via checkboxes and terminate them directly from the dialog.
  - **Warning:** Use with extreme caution. Terminating the wrong process can disrupt applications or destabilize your OS. This may require administrator/root privileges.

### Anvil - Request Heker
Anvil is a request logging and analysis tool designed to help you collect and examine interesting HTTP requests from across Burp Suite.

**How It Works: A 4-Step Workflow**
1. **Automatic Logging:** Anvil automatically captures requests from other Burp tools (like Proxy, Repeater, etc.) and displays them in the main log table.
2. **Inspect a Request:** Click any entry in the log table to view its details. The 'Request' and 'Response' tabs show the raw data, while the 'Summary' tab provides a clean overview, including parsed URL and body parameters.
3. **Collect Interesting Findings:** If you find a significant request, select it in the table and click the 'Add to List' button. This appends its summary to the 'Collected Items' panel on the right.
4. **Manage Your List:** Use the 'Collected Items' panel to keep a running list of important requests for your report. The 'Clear History' button will clear this list.

**Key Components**
- **Request Log:** A sortable table showing the #, Tool, Host, Method, and URL for every captured request.
- **Detailed Viewer:** A tabbed pane for deep inspection of the selected request's Summary, full Request, and full Response.
- **Collected Items Panel:** A dedicated area to save summaries of key requests, preventing them from getting lost in the noise.

## Screenshots

<img width="1835" height="912" alt="image" src="https://github.com/user-attachments/assets/291b74d0-09cd-4660-92fa-36de296bcc6e" />
<img width="1636" height="838" alt="image" src="https://github.com/user-attachments/assets/7dcb512a-fef2-46db-b4b0-8a206dc15c71" />
<img width="1552" height="627" alt="image" src="https://github.com/user-attachments/assets/f02f672f-833f-4941-9e45-95026ed8fab1" />
<img width="1835" height="944" alt="image" src="https://github.com/user-attachments/assets/4d185286-9b78-473d-82d0-6af39e8f995b" />
<img width="1379" height="828" alt="image" src="https://github.com/user-attachments/assets/02e408aa-1046-45df-b09e-4fd2fe9e2f21" />


## Credits
- **Creator:** Joel Indra
- **Inspiration:** Underworld & AI
- **Libraries:** Jackson (JSON), JJWT (JWT handling), Gson (settings), and Burp Suite API.

## License
Licensed under Hades. See [LICENSE](LICENSE) for details.

© 2025 Joel Indra | Underworld & AI
