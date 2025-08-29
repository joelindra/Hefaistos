# Hefaistos

[![GitHub Release](https://img.shields.io/github/v/release/joelindra/hefaistos?style=flat-square)](https://github.com/joelindra/hefaistos/releases)
[![GitHub License](https://img.shields.io/badge/License-Hades-blue?style=flat-square)](https://github.com/joelindra/hefaistos/blob/main/LICENSE)
[![Burp Suite Extension](https://img.shields.io/badge/Burp%20Suite-Extension-orange?style=flat-square)](https://portswigger.net/burp)
[![Java](https://img.shields.io/badge/Java-11+-blue?style=flat-square)](https://www.oracle.com/java/)

Hefaistos is a powerful Burp Suite extension designed for penetration testers and security researchers. It integrates multiple specialized modules—**Forge** for advanced HTTP fuzzing, **Hammer** for comprehensive JSON Web Token (JWT) analysis and attacks, **Tripod** for webhook listening and port management, **Anvil** for request logging and analysis, and **Assistant** for AI-powered HTTP request analysis—into a single, streamlined interface. Built to enhance your security testing workflow, Hefaistos provides automated vulnerability detection, payload crafting, exploit simulation, and more within Burp Suite's environment.

<img width="427" height="640" alt="image" src="https://github.com/user-attachments/assets/4d7f49ff-5bbc-4e0a-b639-b34acd801ced" />

## Table of Contents
- [Key Features](#key-features)
  - [Forge: Multi-Threaded Fuzzing Module](#forge-multi-threaded-fuzzing-module)
  - [Hammer: JWT Analysis & Attack Module](#hammer-jwt-analysis--attack-module)
  - [Tripod: Webhook Listener & Port Management](#tripod-webhook-listener--port-management)
  - [Anvil: Request Logging & Analysis](#anvil-request-logging--analysis)
  - [Assistant: AI-Powered Request Analysis](#assistant-ai-powered-request-analysis)
  - [General Features](#general-features)
- [Installation](#installation)
- [Usage](#usage)
  - [Forge Usage](#forge-usage)
  - [Hammer Usage](#hammer-usage)
  - [Tripod Usage](#tripod-usage)
  - [Anvil Usage](#anvil-usage)
  - [Assistant Usage](#assistant-usage)
- [Screenshots](#screenshots)
- [License](#license)

## Key Features

### Forge: Multi-Threaded Fuzzing Module
- **Automated Parameter Detection**: Automatically detects fuzzing markers in HTTP requests (default: `FUZZ`).
- **Category-Based Fuzzing**: Supports multiple vulnerability categories with pre-built or custom payloads:
  - **Injection**: SQL Injection, XSS.
  - **File/Path**: Path Traversal, File Inclusion.
  - **Redirects**: Open Redirect, Unwanted HTTP Methods.
  - **Authentication**: Username Enumeration, CRLF Injection, Broken Authentication.
  - **Custom**: Custom Payloads, Host Header Injection (Burp Professional only).
- **Configurable Scans**: Customize threads, delays, and specific markers per category.
- **Results Analysis**: Tabular results with filtering by category, status codes, response lengths, timings, and detected issues.
- **Progress Tracking**: Real-time progress bar and statistics (e.g., 2xx, 3xx, 4xx, 5xx responses).
- **Export & Clear**: Export results to CSV or clear for new scans.
- **Settings Persistence**: Auto-saves configurations every 30 seconds or manually via the context menu.

### Hammer: JWT Analysis & Attack Module
- **Decoder**: Decodes JWT headers and payloads; verifies signatures with provided secrets or keys.
- **Security Analysis**: Identifies vulnerabilities such as weak algorithms, missing expiration, or invalid signatures.
- **Fuzzing Checklist**: Automated tests for common JWT vulnerabilities (e.g., 'none' algorithm, empty signatures, 'kid' injections).
- **Algorithm Confusion Attack**: Converts RS256 to HS256 using public keys for potential exploitation.
- **Brute-Force Attack**: Cracks weak HSxxx secrets using in-memory or file-based wordlists.
- **Builder**: Generates new JWTs with HS256/384/512 algorithms, custom payloads, and secrets.
- **Progress & Output**: Displays real-time progress for attacks with detailed, formatted results.

### Tripod: Webhook Listener & Port Management
- **Local HTTP Endpoint**: Creates a simple webhook listener on a specified port to capture out-of-band (OOB) requests for testing SSRF, Blind XSS, XXE, etc.
- **Real-Time Request Logging**: Displays incoming requests in a sortable table with method, URL, timestamp, and full raw request details.
- **IP Address Detection**: Automatically lists available IP addresses for crafting payload URLs.
- **Port Management**: Scans and kills processes using specific TCP ports to resolve "port in use" issues (with caution).
- **History Management**: Clear captured request history and stop/start the listener easily.

### Anvil: Request Logging & Analysis
- **Automatic Request Capture**: Logs HTTP requests from various Burp tools (e.g., Proxy, Repeater) into a sortable table.
- **Detailed Inspection**: View request summaries, raw requests/responses, and parsed parameters (URL and body) in a tabbed viewer.
- **Collection Panel**: Add selected requests to a side panel for easy collection of interesting findings; includes copy and clear functions.
- **Timestamped Entries**: Each log entry includes tool source, host, method, URL, and timestamp.
- **Clear History**: Reset the log and collected items with a single button.

### Assistant: AI-Powered Request Analysis
- **AI Integration**: Send HTTP requests to AI providers (e.g., Gemini, ChatGPT, Claude) for automated security vulnerability analysis.
- **Customizable Prompts**: Use pre-defined or custom templates to guide AI analysis; edit prompts directly in the interface.
- **API Key Management**: Securely store and manage API keys for multiple AI providers in the settings tab.
- **Response Viewer**: Displays AI-generated insights in a dedicated panel with real-time status updates.
- **Template Management**: Add, edit, or remove prompt templates to tailor analysis to specific needs.

### General Features
- **Context Menu Integration**: Send HTTP requests to Forge, Hammer, Tripod, Anvil, or Assistant directly from Burp Suite's context menu.
- **Modern UI**: Dark-themed interface matching Burp Suite, with glitch animations and hover effects for enhanced user experience.
- **Auto-Save Settings**: Automatically saves configurations to persist settings across sessions.
- **Error Logging**: Dual logging to Burp's Errors tab and system console for debugging.
- **Compatibility**: Works with Burp Suite Professional and Community editions (some features exclusive to Professional).
- **About & Usage Tabs**: Includes an "About" tab with tool info and a "Usage" tab with detailed instructions.

## Installation

1. **Download the JAR File**:
   - Grab the latest release from the [GitHub Releases page](https://github.com/joelindra/hefaistos/releases).

2. **Load in Burp Suite**:
   - Open Burp Suite.
   - Navigate to the **Extensions** tab.
   - Click **Add**, select **Java** as the extension type, and browse to the downloaded `Hefaistos.jar` file.
   - Ensure the extension loads successfully (check the **Output** tab for "Hefaistos loaded successfully!").

3. **Verify Installation**:
   - A new tab named **Hefaistos** should appear in Burp Suite with **Forge**, **Hammer**, **Tripod**, **Anvil**, **Assistant**, **Usage**, and **About** sub-tabs.

## Usage

### Forge Usage
1. **Send a Request**:
   - Right-click an HTTP request in Burp Suite (e.g., in Proxy or Repeater).
   - Select **Send to Hefaistos > Send to Forge**.
   - The request will populate in the **HTTP Request** panel.

2. **Configure Fuzzing**:
   - Use the **Global Marker** field (default: `FUZZ`) or click **Auto-Detect Parameters** to identify injection points.
   - Navigate the fuzzing categories (Injection, File/Path, etc.) and enable/disable tests, adjust threads, delays, or load custom wordlists.

3. **Run the Attack**:
   - Click **Start Attack** to begin fuzzing.
   - Monitor results in the **Fuzzing Results** table, filter by category, and view modified requests/responses.
   - Use **Export** to save results or **Clear** to reset.

4. **Save Settings**:
   - Click **Save** in the control panel or use the context menu (**Send to Hefaistos > Save Settings**) to persist configurations.

### Hammer Usage
1. **Send a JWT**:
   - Right-click an HTTP request containing a JWT (e.g., in the Authorization header or body).
   - Select **Send to Hefaistos > Send to Hammer** to populate the **Encoded JWT** field in the Decoder tab.

2. **Decode & Analyze**:
   - In the **Decoder** tab, view decoded header and payload, and enter a secret/key to verify the signature.
   - Check the **Security Analysis** panel for identified vulnerabilities.

3. **Run Attacks**:
   - In the **Security Tests** tab:
     - Use **JWT Fuzzer** for automated vulnerability checks.
     - Perform an **Algorithm Confusion Attack** by providing a public key.
     - Run a **Weak Secret Brute Force** with a wordlist (in-memory or file-based).
   - Monitor progress and results in the **Attack Output** panel.

4. **Build a JWT**:
   - In the **Builder** tab, select an HSxxx algorithm, enter a payload (JSON), and provide a secret.
   - Click **Generate Token** to create a new JWT.

### Tripod Usage
1. **Start the Listener**:
   - Enter a port number (e.g., 8080) and click **Start Listener**. It binds to all interfaces.
   - The status bar displays available IP addresses for crafting payload URLs.

2. **Capture Requests**:
   - Use the webhook URL in your payloads to trigger OOB interactions.
   - Incoming requests appear in the **Request History** table; select entries to view raw details.

3. **Manage Ports**:
   - Click **Kill Used Ports** to open a dialog listing processes on TCP ports.
   - Select and terminate processes to free up ports (use with caution).

4. **Stop & Clear**:
   - Click **Stop Listener** to shut down the server.
   - Use **Clear History** to reset the request log.

### Anvil Usage
1. **Capture Requests**:
   - Anvil automatically logs requests from Burp tools into the main table.

2. **Inspect Details**:
   - Select a log entry to view its **Summary**, **Request**, and **Response** in the tabbed viewer.

3. **Collect Findings**:
   - Click **Add to List** to append the selected request's summary to the **Collected Items** panel.
   - Use **Copy List** to copy collected items to the clipboard.

4. **Manage History**:
   - Click **Clear History** to reset the log and collected items.

### Assistant Usage
1. **Configure API Keys**:
   - In the **Settings** tab, enter API keys for providers like Gemini, ChatGPT, or Claude, then save.

2. **Send a Request**:
   - Right-click an HTTP request and select **Send to Hefaistos > Send to Assistant**.
   - The request populates in the prompt area with the selected template.

3. **Customize & Submit**:
   - Edit the prompt or switch templates via the dropdown.
   - Click **Submit to AI** to get analysis in the **AI Response** panel.

4. **Manage Templates**:
   - In the **Templates** tab, add, edit, or remove custom prompts.

## Screenshots

<img width="1916" height="946" alt="image" src="https://github.com/user-attachments/assets/ae64d089-5b10-4e58-99f4-24f26f18ab68" />
<img width="1863" height="838" alt="image" src="https://github.com/user-attachments/assets/2e69e86d-4e29-4cdb-997c-2db808116429" />
<img width="1857" height="628" alt="image" src="https://github.com/user-attachments/assets/86e48b53-ec64-4b37-b129-f793327d2530" />
<img width="1891" height="916" alt="image" src="https://github.com/user-attachments/assets/be407775-2e68-4296-80dc-206338c3cfe5" />
<img width="1658" height="778" alt="image" src="https://github.com/user-attachments/assets/37f19902-d3f9-4d33-a035-9368dc6151b6" />
<img width="1505" height="895" alt="image" src="https://github.com/user-attachments/assets/dd24d07c-17c5-4724-a107-4e58df49c4bc" />


## Credits
- **Creator:** Joel Indra
- **Inspiration:** Underworld & AI
- **Libraries:** Jackson (JSON), JJWT (JWT handling), Gson (settings), and Burp Suite API.

## License
Licensed under Hades. See [LICENSE](LICENSE) for details.

© 2025 Joel Indra | Underworld & AI
