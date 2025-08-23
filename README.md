# Hefaistos Fuzzer v1.0.0

<img width="200" height="300" alt="image" src="https://github.com/user-attachments/assets/62d3636d-e70e-447f-944c-85f556526e4d" />

Hefaistos Fuzzer is a powerful and flexible Burp Suite extension designed for advanced web application fuzzing. It enables security researchers and penetration testers to perform comprehensive fuzzing tests for vulnerabilities such as SQL Injection, XSS, Path Traversal, Open Redirects, and more. The extension integrates seamlessly with Burp Suite, offering an intuitive UI for configuring and executing fuzzing tasks, analyzing results, and interacting with other Burp Suite tools.

## Features

- **Multiple Fuzzing Categories**: Supports various vulnerability categories, including:
  - Injection (SQL Injection, XSS)
  - File/Path (Path Traversal, File Inclusion)
  - Redirects (Open Redirect, Unwanted HTTP Method)
  - Authentication (Username Enumeration, CRLF Injection, Broken Authentication)
  - Custom (Custom Payloads, Host Header Injection)
- **Customizable Payloads**: Load custom wordlists or use predefined payloads for each category.
- **Flexible Configuration**: Configure threads, delays, and specific markers for each fuzzing category.
- **Burp Collaborator Integration**: Supports out-of-band testing for Host Header Injection.
- **Interactive Results Table**: Filter results by category, view detailed request/response data, and send results to Burp Suite's Repeater, Intruder, or Comparer.
- **Auto-Detect Parameters**: Automatically identifies and marks parameters in HTTP requests for fuzzing.
- **Persistent Settings**: Save and load fuzzing configurations for consistent testing.
- **Export Results**: Export fuzzing results to CSV for further analysis.
- **Progress and Statistics**: Real-time progress tracking and detailed statistics (e.g., status code distribution).

## Installation

1. **Prerequisites**:
   - Burp Suite Professional or Community Edition.
   - Java Development Kit (JDK) 8 or higher.
   - Burp Suite API (included with Burp Suite).

2. **Steps**:
   - Download the `HefaistosFuzzer.jar` file from the [Releases](https://github.com/joelindra/HefaistosFuzzer/releases) page.
   - In Burp Suite, go to the **Extender** tab.
   - Click **Add**, select **Java** as the extension type, and browse to the `HefaistosFuzzer.jar` file.
   - Load the extension. You should see the "Hefaistos Fuzzer" tab appear in Burp Suite.

3. **Verify Installation**:
   - Check the **Output** tab in Burp Suite’s Extender for the message: `Hefaistos Fuzzer loaded successfully!`.
   - The extension tab should be visible and functional.

## Usage

### 1. Accessing the Extension
- Navigate to the **Hefaistos Fuzzer** tab in Burp Suite.
- Alternatively, right-click on an HTTP request in any Burp Suite tool (e.g., Proxy, Repeater) and select **Send to Hefaistos Fuzzer** to populate the request area.

### 2. Configuring Fuzzing
- **HTTP Request**: Paste or send an HTTP request to the request area. Use the **Auto-Detect Parameters** button to automatically mark injectable parameters with the global marker (`FUZZ` by default).
- **Global Marker**: Set a global marker (e.g., `FUZZ`) to define injection points in the request.
- **Fuzzing Categories**:
  - Enable/disable categories (e.g., SQL Injection, XSS) via checkboxes.
  - Configure threads and delay for each category.
  - For non-automated categories, specify payloads in the text area or load a wordlist file.
  - Optionally set specific markers for each category to override the global marker.
- **Automated Categories**:
  - **Broken Authentication**: Removes Authorization and Cookie headers to test for authentication bypass.
  - **Unwanted HTTP Method**: Cycles through HTTP methods (e.g., GET, POST, DELETE).
  - **Host Header Injection**: Injects Burp Collaborator payloads to detect out-of-band interactions.

### 3. Starting a Scan
- Click **Start Fuzzing** to begin the scan.
- Monitor progress via the progress bar and status label.
- Stop the scan at any time using the **Stop** button.

### 4. Analyzing Results
- **Results Table**: Displays fuzzing results with columns for ID, Category, Payload, Status, Length, Time, and Issues.
- **Filters**: Use the category filter dropdown to view results for specific categories.
- **Statistics**: View status code distribution (e.g., 2xx, 3xx, 4xx, 5xx) in the statistics panel.
- **Request/Response Viewers**: Select a result to view the modified request, original response, and modified response.
- **Context Menu Actions**:
  - Right-click a result to send it to Repeater, Intruder, or Comparer.
  - Copy modified request/response data to the clipboard.
- **Export Results**: Save results to a CSV file using the **Export Results** button.

### 5. Saving Settings
- Click **Save Settings** to persist configurations (global marker, payloads, category settings).
- Settings are automatically saved when the extension is unloaded.

### 6. Example Workflow
1. Send an HTTP request to the fuzzer from Burp Suite’s Proxy.
2. Use **Auto-Detect Parameters** to mark a parameter (e.g., `id=1` becomes `id=FUZZ`) or Manually add your mark
3. Enable desired categories (e.g., SQL Injection, XSS) and load custom payloads if needed.
4. Start the scan and monitor results.
5. Analyze results, send interesting requests to Repeater for further testing, and export results for reporting.

## Screenshots

<img width="1914" height="929" alt="image" src="https://github.com/user-attachments/assets/59af0bc1-c882-4519-b639-9a1b8229b366" />

## Dependencies

- **Burp Suite API**: Provided by Burp Suite (included in the Burp Suite installation).
- **GSON**: Included in the Burp Suite runtime for JSON serialization/deserialization.
- **Java Swing**: Used for the UI, included in the Java Runtime Environment (JRE).

## Issues

Report bugs or suggest features by creating an issue in the [GitHub Issues](https://github.com/joelindra/HefaistosFuzzer/issues) section. Provide detailed information, including:
- Burp Suite version
- Java version
- Steps to reproduce the issue
- Screenshots or logs (if applicable)

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Credits

- **Author**: Joel Indra (Anonre)
- **Inspiration**: Built for the security research community to enhance web application testing.

*Fear just an illusion. Hack responsibly!*
