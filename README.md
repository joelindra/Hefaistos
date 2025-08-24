# Hefaistos v2.1.0

<img width="427" height="640" alt="image" src="https://github.com/user-attachments/assets/4d7f49ff-5bbc-4e0a-b639-b34acd801ced" />

[Hefaistos](#hefaistos) is a powerful Burp Suite extension designed for penetration testers and security researchers to streamline and enhance their security testing workflows. It integrates three specialized modules—[**Forge**](#forge-advanced-fuzzer) for general-purpose fuzzing, [**Hammer**](#hammer-jwt-toolkit) for JSON Web Token (JWT) analysis and attacks, and [**Tripod**](#tripod-webhook-listener) for webhook listening and request capturing—into a single, cohesive interface within Burp Suite.

## Table of Contents
- [Features](#features)
  - [Forge (Advanced Fuzzer)](#forge-advanced-fuzzer)
  - [Hammer (JWT Toolkit)](#hammer-jwt-toolkit)
  - [Tripod (Webhook Listener)](#tripod-webhook-listener)
  - [General Features](#general-features)
- [Installation](#installation)
- [Usage](#usage)
  - [Getting Started](#getting-started)
  - [Forge Example](#forge-example)
  - [Hammer Example](#hammer-example)
  - [Tripod Example](#tripod-example)
  - [Tips](#tips)
- [Configuration](#configuration)
- [Screenshots](#screenshots)
- [Credits](#credits)
- [License](#license)

## Features

### Forge (Advanced Fuzzer)
- **Versatile Fuzzing**: Multi-threaded HTTP request fuzzing to uncover vulnerabilities like SQL Injection, XSS, Path Traversal, and more.
- **Automatic Parameter Detection**: Identifies insertion points with a customizable global marker (e.g., `FUZZ`).
- **Payload Categories**: Pre-built payloads for:
  - **Injection**: SQL Injection, XSS
  - **File/Path**: Path Traversal, File Inclusion
  - **Redirects**: Open Redirect, Unwanted HTTP Methods
  - **Authentication**: Username Enumeration, CRLF Injection, Broken Authentication
  - **Custom**: Custom Payloads, Host Header Injection
- **Customization**: Configure threads, delays, and specific markers per category.
- **Results Analysis**: Sortable table with filters, detailed request/response viewers, and issue detection (e.g., reflected XSS, SQL errors).
- **Statistics**: Tracks response codes (2xx, 3xx, 4xx, 5xx) with a progress bar.
- **Export & Save**: Export results to CSV/JSON and auto-save settings.

### Hammer (JWT Toolkit)
- **Decoder Tab**: Decode JWT headers and payloads, verify signatures with custom secrets, and analyze security issues (e.g., weak algorithms, expired tokens).
- **Security Tests Tab**:
  - **Brute-Force Attacks**: Test weak secrets using wordlists or in-app lists.
  - **Algorithm Confusion**: Perform attacks with public key injection.
  - **Fuzzing Checklist**: Test for vulnerabilities like 'none' algorithm, `kid` path traversal, `jku` spoofing, and JWK injection.
- **Builder Tab**: Generate JWTs with HS256/384/512 algorithms, custom payloads, and secrets.
- **Features**: Progress tracking, cancelable operations, and detailed logs for all actions.

### Tripod (Webhook Listener)
- **HTTP Listener**: Start a server on a specified port (e.g., 8080) to capture incoming HTTP requests, ideal for webhook testing or callbacks.
- **Request History**: Sortable table displaying request index, method, URL, timestamp, and full request details.
- **Context Menu Integration**: Send requests from Burp tools (e.g., Repeater, Proxy) to Tripod via "Send to Tripod".
- **Port Management**: View and kill used ports (with PID detection) to free up resources (requires admin/sudo privileges).
- **IP Detection**: Displays available IP addresses, with warnings for VPN/port accessibility.

### General Features
- **Cyberpunk UI**: Dark theme with glitch effects on the title for a futuristic aesthetic.
- **Context Menu**: "Send to Hefaistos" > "Send to Forge" for quick request importing.
- **Auto-Save**: Saves settings every 30 seconds, on tab changes, or on extension unload.
- **Compatibility**: Works with Burp Suite Professional and Community editions.
- **About Tab**: Provides system info, feature overview, and links to [GitHub](#credits) and [Website](#credits).
- **Error Handling**: Robust logging to Burp's output and error streams.

## Installation

1. Download the latest JAR release from the [Releases](https://github.com/joelindra/Hefaistos/releases) page.
2. In Burp Suite, navigate to **Extender** > **Extensions** > **Add**.
3. Select the Hefaistos JAR file and click **Next**.
4. Once loaded, a new **Hefaistos** tab will appear with sub-tabs: [Forge](#forge-advanced-fuzzer), [Hammer](#hammer-jwt-toolkit), [Tripod](#tripod-webhook-listener), and About.

**Requirements**:
- Java 8 or higher (compatible with Burp's JRE).
- Burp Suite v2023 or later recommended for optimal performance.

## Usage

### Getting Started
1. Open the **Hefaistos** tab in Burp Suite.
2. Right-click a request in any Burp tool (e.g., Proxy, Repeater) and select **Send to Hefaistos** > **Send to Forge**.
3. Configure settings in each module as needed.

### Forge Example
1. In the **Forge** tab, paste an HTTP request or send one via the context menu.
2. Click **Auto-Detect Parameters** to identify insertion points (marked with `FUZZ` or custom markers).
3. Enable desired categories (e.g., SQL Injection, XSS) and customize payloads, threads, or delays.
4. Click **Start Attack** to begin fuzzing.
5. Monitor results in the sortable table, filter by category, and inspect modified requests/responses in the viewers.
6. Export results or save settings manually with the **Save** button.

### Hammer Example
1. In the **Decoder** tab, paste a JWT to view decoded header, payload, and security analysis.
2. Enter a secret key and click **Verify Signature** to check JWT validity.
3. In the **Security Tests** tab:
   - Load a wordlist for brute-force attacks on weak secrets.
   - Run the fuzzing checklist to test for common JWT vulnerabilities.
4. In the **Builder** tab, select an algorithm (e.g., HS256), enter payload JSON and a secret, then click **Generate** to create a new JWT.
5. Monitor progress and logs in the output area.

### Tripod Example
1. In the **Tripod** tab, enter a port number (e.g., 8080) and click **Start Listener**.
2. Send HTTP requests to `http://your-ip:port` (e.g., via curl or a webhook service).
3. View captured requests in the history table, sorted by index, method, URL, or timestamp.
4. Click a row to display the full request in the text area.
5. Use **Kill Used Ports** to terminate processes on occupied ports or **Clear History** to reset the table.

### Tips
- **Forge**: Use smaller wordlists and lower thread counts for initial tests to avoid overwhelming the target server.
- **Hammer**: Ensure wordlists for brute-force attacks are optimized for performance; large files may slow down tests.
- **Tripod**: If using a VPN, verify that the chosen port is forwarded and not blocked by VPN settings.
- **General**: Leverage auto-save for settings, but use manual **Save** in Forge for critical configurations.
- Check Burp’s output panel for detailed logs if errors occur.

## Configuration

- **Forge**:
  - **Global Marker**: Default is `FUZZ`; customize for specific insertion points.
  - **Payloads**: Edit in text areas or load external wordlists for each category.
  - **Threads/Delays**: Adjust per category for performance vs. thoroughness.
- **Hammer**:
  - **Wordlists**: Load via file chooser for brute-force attacks.
  - **Algorithms**: Supports HS256/384/512 for JWT generation; others available for analysis.
- **Tripod**:
  - **Port**: Choose any valid port (1-65535); default is 8080.
  - **IP Binding**: Listens on all interfaces (`0.0.0.0`) with detected IPs displayed.

Settings are auto-saved to Burp’s extension storage and can be manually saved in Forge for immediate backups.

## Screenshots

<img width="1901" height="875" alt="image" src="https://github.com/user-attachments/assets/25ed53a7-c04d-48b4-b2fa-559f24b46420" />
<img width="1900" height="915" alt="image" src="https://github.com/user-attachments/assets/d3c13634-1257-46fa-b2aa-f6d0f2b43ada" />
<img width="1764" height="834" alt="image" src="https://github.com/user-attachments/assets/14627b7f-1a63-486b-b0f0-f0ff88177f02" />
<img width="1681" height="808" alt="image" src="https://github.com/user-attachments/assets/de0c76bc-b251-4caa-92c2-0440bf2e0289" />

## Credits
- **Author**: Joel Indra
- **GitHub**: [joelindra](https://github.com/joelindra)
- **Website**: [docs.joelindra.id](https://docs.joelindra.id)
- **Dependencies**:
  - [jsonwebtoken (jjwt)](https://github.com/jwtk/jjwt) for JWT handling.
  - Burp Suite API for integration.
- **Inspiration**: Tools like Burp Intruder, jwt_tool, and webhook.site.

## License
Licensed under the Hades License. See [LICENSE](LICENSE) for details.

© 2025 Joel Indra | Underworld & AI
