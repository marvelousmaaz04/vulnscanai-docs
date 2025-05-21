# Directory: `app/scanners`

**Purpose:** This directory contains the code for integrating with different vulnerability scanning tools. Each file in this directory represents a scanner integration. The scanners are designed to be modular and easily extensible.

**Files:**

*   `cloudsploit_scanner_azure.py`:
    *   **Description:** Integrates with the CloudSploit tool to perform security audits on Azure cloud environments. Uses the CloudSploit API (or command-line interface) to initiate scans and retrieve results.
    *   **Key Functionality:**
        *   `scan(target, credentials)`: Executes CloudSploit against the specified Azure subscription. Takes Azure credentials as input for authenticated scanning.
        *   Parses the CloudSploit JSON output to extract findings.
        *   Normalizes the findings into a standardized format for reporting.
    *   **Dependencies:** `subprocess` (if using the CLI), `requests` (if using the API), `json`, `os`

*   `mobsf_scanner.py`:
    *   **Description:** Integrates with the Mobile Security Framework (MoBSF) to analyze mobile application binaries (APKs and IPAs). Uses the MoBSF API to upload binaries and retrieve analysis reports.
    *   **Key Functionality:**
        *   `scan(binary_path)`: Uploads the mobile application binary to MoBSF and initiates the analysis.
        *   Retrieves the MoBSF report in JSON or XML format.
        *   Parses the report to extract vulnerabilities, code analysis findings, and other security-related information.
    *   **Dependencies:** `requests`, `json`, `os`

*   `nikto_scanner.py`:
    *   **Description:** Integrates with the Nikto web server scanner to identify potential vulnerabilities in web servers. Uses the Nikto command-line interface to initiate scans and parse the output.
    *   **Key Functionality:**
        *   `scan(target_url, options=None)`: Executes Nikto against the specified target URL with optional command-line arguments.
        *   Parses the Nikto output to extract identified vulnerabilities.
        *   Converts the Nikto output into a standardized format.
    *   **Dependencies:** `subprocess`, `os`

*   `nmap_scanner.py`:
    *   **Description:** Integrates with the Nmap port scanner to perform network reconnaissance and identify open ports and services. Uses the Nmap command-line interface.
    *   **Key Functionality:**
        *   `scan(target_host, options=None)`: Executes Nmap against the specified target host with optional command-line arguments (e.g., port ranges, scan types).
        *   Parses the Nmap XML output to extract open ports, service versions, and OS detection results.
    *   **Dependencies:** `subprocess`, `os`, `xml.etree.ElementTree`

*   `openvas_scanner.py`:
    *   **Description:** Integrates with the OpenVAS vulnerability scanner (if you're using it).
    *   **Key Functionality:** (Describe how it works)
    *   **Dependencies:** (List dependencies)

*   `prowler_scanner_aws.py`:
    *   **Description:** Integrates with Prowler to perform security assessments in AWS environments.
    *   **Key Functionality:** Executes Prowler, parses the results, and stores them.
    *   **Dependencies:** `subprocess`, `json`, `os`

*   `prowler_scanner_gcp.py`:
    *   **Description:** Integrates with Prowler to perform security assessments in GCP environments.
    *   **Key Functionality:** Executes Prowler, parses the results, and stores them.
    *   **Dependencies:** `subprocess`, `json`, `os`

*   `sqlmap_scanner.py`:
    *   **Description:** Integrates with the sqlmap SQL injection tool to identify and exploit SQL injection vulnerabilities.
    *   **Key Functionality:** Executes sqlmap against a target URL and parses the results.
    *   **Dependencies:** `subprocess`, `os`

*   `ssl_scanner.py`:
    *   **Description:** Performs SSL/TLS security checks on a target host.
    *   **Key Functionality:** Executes `sslscan` or similar tools and parses the results.
    *   **Dependencies:** `subprocess`, `os`

*   `zap_scanner.py`:
    *   **Description:** Integrates with the OWASP ZAP proxy to perform dynamic application security testing (DAST).
    *   **Key Functionality:** Starts ZAP, configures it, runs a scan against a target URL, and retrieves the report.
    *   **Dependencies:** `requests`, `os`

*   `__init__.py`:
    *   **Description:** Makes the `scanners` directory a Python package, allowing other modules to import the scanner integrations.
    *   **Key Functionality:** Likely contains import statements to make the scanner modules available: `from .nmap_scanner import scan as nmap_scan`. This enables easy calling of all scan functions.
    *   **Dependencies:** None