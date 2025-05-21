# Directory: `app/views`

**Purpose:** This directory contains the view functions (route handlers) that define the application's behavior. These functions handle user requests, interact with models, and render HTML templates.

**Files:**

*   `analyze_report_ai.py`:
    *   **Description:** Analyzes scan reports using the Google Gemini model. Extracts text from PDFs, masks PII, and generates insights.
    *   **Key Functionality:** Uses `GeminiReportAnalyzer` class to handle PDF processing, PII masking, and Gemini API interactions.
    *   **Dependencies:** `google.generativeai`, `pypdf`, `flask`, `re`

*   `auth.py`:
    *   **Description:** Handles user authentication routes (login, registration, password reset, update password, email verification, etc.).
    *   **Key Functionality:** Manages user registration, login, logout, password reset, and email verification using Flask-Login, `bcrypt`, and itsdangerous for secure token generation and email verification process.
    *   **Dependencies:** `flask`, `flask_login`, `bcrypt`, `forms`, `models`, `flask_mail`, `itsdangerous`, `requests`, `os`

*   `genai.py`:
    *   **Description:** Contains routes and functions for interacting with the Gemini AI model for security report analysis.
    *   **Key Functionality:** Handles uploading reports, analyzing them with Gemini, and managing chat sessions for follow-up questions.
    *   **Dependencies:** `flask`, `flask_login`, `google.generativeai`, `werkzeug`, `os`, `logging`, `app.analyze_report_ai`

*   `main.py`:
    *   **Description:** Contains the main application routes (home page, profile page, about page, scan page, contact page, pricing page, download report page, etc.).
    *   **Key Functionality:** Handles core web application routes, manages vulnerability scans, provides report downloads, and facilitates user communication via contact forms.
    *   **Dependencies:** `flask`, `flask_login`, `werkzeug`, `os`, `requests`, `app.scanners.*`, `app.forms`, `app.models`, `app.analyze_report_ai`, `flask_mail`, `logging`, `json`

*   `payments.py`:
    *   **Description:** Handles payment-related functionality using the PayPal API (creates orders, captures payments, handles cancellations, updates subscriptions).
    *   **Key Functionality:** Integrates with PayPal to create and capture payments, manage user subscriptions, and record payment transactions in the database. Includes retry logic and error handling for API interactions.
    *   **Dependencies:** `flask`, `flask_login`, `app.extensions`, `app.models`, `datetime`, `os`, `requests`, `logging`, `uuid`, `time`, `random`, `sqlalchemy.exc`

*   `__init__.py`:
    *   **Description:** Makes the `views` directory a Python package.
    *   **Key Functionality:** Registers blueprints for the view modules (e.g., `auth`, `main`, `payments`, `genai`).
    *   **Dependencies:** `flask`