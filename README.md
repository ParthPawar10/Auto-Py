# Python Selenium Automation Testing Framework

This is a lightweight, modular, and beginner-friendly **UI automation testing framework** built using **Python** and **Selenium WebDriver**. It’s structured using the **Page Object Model (POM)** and includes reporting, logging, and easy-to-understand folder structure to help you get started quickly with web UI automation.

---

## Features

- Modular Design
- Supports multiple browsers
- HTML report generation
- Logging of test execution
- Easy-to-maintain folder structure

---

## Folder Structure

```
web_ui_testing/
│
├── Locators/             # Element locators (POM format)
├── src/
│   ├── Drivers/          # WebDrivers for browsers
│   ├── logs/             # Execution logs
│   ├── Reports/          # HTML reports
│   └── Utility/          # Helper functions/utilities
│
├── Tests/                # Test case implementations
├── Config.py             # Configuration data
├── Conftest.py           # Pytest fixtures and browser setup
└── requirements.txt      # Python dependencies
```

> **Future Scope:** Expand to include `api-testing/` module for API automation

---

##  Module Overview

### `Locators/`

Stores all element locators in Page Object Model (POM) format.

```python
from selenium.webdriver.common.by import By
SEARCH_INPUT = (By.NAME, "q")
```

### `src/Drivers/`

Contains WebDriver binaries like `chromedriver`, `geckodriver`, etc.

### `src/logs/`

Holds logs generated during test runs.

### `src/Reports/`

Includes HTML reports generated after test execution using `pytest-html`.

### `src/Utility/`

Reusable helper functions or wrappers.

### `Tests/`

Test cases written using the POM pattern.

```python
from tests import BaseClass
from locator.google_homepage_locator import *
from selenium.webdriver.common.keys import Keys

class TestGoogleSearch(BaseClass):
    def test_search_functionality(self):
        self.log().info("Starting Google Search Test")
        self.get_element(SEARCH_BAR).send_keys("Automation Testing")
        self.get_element(SEARCH_BAR).send_keys(Keys.RETURN)
        self.log().info("Search test completed successfully")
        assert True
```

### `Config.py`

Environment-specific configuration like base URL, credentials, etc.

```python
BASE_URL = "https://www.google.com/"
```

### `Conftest.py`

Houses pytest fixtures and browser setup logic.

```bash
pytest --browser_name chrome
pytest --browser_name firefox
```

---

## Sample Workflow

1. Define locator in `Locators/google_homepage_locator.py`
2. Write test in `Tests/test_google_search.py`
3. Run tests with `pytest`
4. Check logs and HTML report

---
