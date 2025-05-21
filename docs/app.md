# Directory: `app`

**Purpose:** This directory contains the core application logic for the VulnScanAI Flask website. It includes configuration, models, forms, views, and supporting modules.

**Subdirectories:**

*   `reports`: Stores generated reports from various vulnerability scanners.  These reports are often in PDF or HTML format.
*   `scanners`: Contains the code for interacting with different vulnerability scanning tools. Each scanner has its own module for integration.
*   `static`: Holds static files like CSS, JavaScript, images, and PDFs.  These files are served directly to the client.
*   `templates`: Contains the HTML templates used to render the website's user interface. Jinja2 templating engine is used.
*   `uploads`: Likely stores uploaded files, such as mobile application binaries (APKs and IPAs) for MoBSF analysis.
*   `views`: Contains the route handlers (view functions) that define the application's behavior. These functions handle user requests and interact with the models.

**Files:**

*   `config.py`:
    *   **Description:** Configuration settings for the Flask application, such as database URLs, API keys, secret keys, and debug settings.
    *   **Key Functionality:** Defines various configuration variables for different environments (development, production, testing).  Uses `os.environ` to read configuration values from environment variables.  Includes a function to generate a secret key if one is not provided.
    *   **Dependencies:** `os`

*   `extensions.py`:
    *   **Description:** Initializes and configures Flask extensions, such as Flask-SQLAlchemy for database interaction, Flask-Mail for sending emails, and Flask-Login for user authentication.
    *   **Key Functionality:** Creates instances of the extensions (e.g., `db = SQLAlchemy()`), and provides a function `init_app(app)` to initialize the extensions with the Flask application instance.
    *   **Dependencies:** `flask_sqlalchemy`, `flask_mail`, `flask_login`, `flask_migrate`

*   `forms.py`:
    *   **Description:** Defines the forms used for user input, such as login, registration, scan configuration, and password reset.  Uses Flask-WTF for form handling and CSRF protection.
    *   **Key Functionality:** Defines form classes (e.g., `LoginForm`, `RegistrationForm`, `ScanForm`) using WTForms fields and validators.  Includes custom validators for email uniqueness, password strength, etc.
    *   **Dependencies:** `flask_wtf`, `wtforms`, `wtforms.validators`, `email_validator`

*   `__init__.py`:
    *   **Description:** Makes the `app` directory a Python package. Initializes the Flask application instance and configures it.
    *   **Key Functionality:** Creates the Flask application instance (`app = Flask(__name__)`), loads configuration from `config.py`, initializes extensions using `extensions.init_app(app)`, registers blueprints for the different views (e.g., `auth_bp`, `main_bp`, etc.).  Also sets up logging.
    *   **Dependencies:** `flask`, `config`, `extensions`, `views`, `logging`

*   `models.py`:
    *   **Description:** Defines the database models used by the application, such as `User`, `ScanResult`, `Subscription`, etc. Uses Flask-SQLAlchemy to define database tables and relationships.
    *   **Key Functionality:** Defines classes that inherit from `db.Model` to represent database tables. Includes methods for creating, reading, updating, and deleting data.
    *   **Dependencies:** `flask_sqlalchemy`, `flask_login`, `datetime`

*   `reports/`, `scanners/`, `static/`, `templates/`, `uploads/`, `views/`: *(These directories are documented separately)*