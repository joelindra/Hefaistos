# Hefaistos v2.0.0

[![GitHub Release](https://img.shields.io/github/v/release/joelindra/hefaistos?style=flat-square)](https://github.com/joelindra/hefaistos/releases)
[![GitHub License](https://img.shields.io/badge/License-Hades-blue?style=flat-square)](https://github.com/joelindra/hefaistos/blob/main/LICENSE)
[![Burp Suite Extension](https://img.shields.io/badge/Burp%20Suite-Extension-orange?style=flat-square)](https://portswigger.net/burp)
[![Java](https://img.shields.io/badge/Java-11+-blue?style=flat-square)](https://www.oracle.com/java/)

<img width="427" height="640" alt="image" src="https://github.com/user-attachments/assets/4d7f49ff-5bbc-4e0a-b639-b34acd801ced" />

Hefaistos is a powerful Burp Suite extension designed for penetration testers and security researchers. It integrates two specialized modules—**Forge** for advanced HTTP fuzzing and **Hammer** for comprehensive JSON Web Token (JWT) analysis and attacks—into a single, streamlined interface. Built to enhance your security testing workflow, Hefaistos provides automated vulnerability detection, payload crafting, and exploit simulation within Burp Suite's environment.

## Table of Contents
- [Key Features](#key-features)
  - [Forge: Multi-Threaded Fuzzing Module](#forge-multi-threaded-fuzzing-module)
  - [Hammer: JWT Analysis & Attack Module](#hammer-jwt-analysis--attack-module)
  - [General Features](#general-features)
- [Installation](#installation)
- [Usage](#usage)
  - [Forge Usage](#forge-usage)
  - [Hammer Usage](#hammer-usage)
- [Screenshots](#screenshots)
- [License](#license)
- [Author](#author)
- [Support](#support)

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

### General Features
- **Context Menu Integration**: Send HTTP requests to Forge or Hammer directly from Burp Suite's context menu.
- **Modern UI**: Dark-themed interface matching Burp Suite, with glitch animations and hover effects for enhanced user experience.
- **Auto-Save Settings**: Automatically saves configurations to persist settings across sessions.
- **Error Logging**: Dual logging to Burp's Errors tab and system console for debugging.
- **Compatibility**: Works with Burp Suite Professional and Community editions (some features exclusive to Professional).

## Installation

1. **Download the JAR File**:
   - Grab the latest release from the [GitHub Releases page](https://github.com/joelindra/hefaistos/releases).

2. **Load in Burp Suite**:
   - Open Burp Suite.
   - Navigate to the **Extensions** tab.
   - Click **Add**, select **Java** as the extension type, and browse to the downloaded `Hefaistos.jar` file.
   - Ensure the extension loads successfully (check the **Output** tab for "Hefaistos loaded successfully!").

3. **Verify Installation**:
   - A new tab named **Hefaistos** should appear in Burp Suite with **Forge**, **Hammer**, and **About** sub-tabs.

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

## Screenshots

<img width="1917" height="946" alt="image" src="https://github.com/user-attachments/assets/bfc3e76f-3808-4e55-9bd4-ff66e949c04a" />
<img width="1915" height="952" alt="image" src="https://github.com/user-attachments/assets/70494160-fe69-4685-86b9-19ebc6605af3" />
<img width="1912" height="918" alt="image" src="https://github.com/user-attachments/assets/6fc26905-eed8-4c3c-9f77-1d004c2de023" />

## License

Hefaistos is licensed under the **Hades License**. See the [LICENSE](https://github.com/joelindra/hefaistos/blob/main/LICENSE) file for details.

## Author

- **Joel Indra**
  - GitHub: [joelindra](https://github.com/joelindra)
  - Website: [docs.joelindra.id](https://docs.joelindra.id)

## Support

For issues, feature requests, or questions:
- Open an issue on the [GitHub Issues page](https://github.com/joelindra/hefaistos/issues).
- Contact the author via the [website](https://docs.joelindra.id).

Happy testing, and stay secure!
