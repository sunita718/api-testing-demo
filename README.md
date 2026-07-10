# API Testing Demo

[![Python 3.10+](https://img.shields.io/badge/python-3.10%2B-blue.svg)](https://www.python.org/)
[![pytest](https://img.shields.io/badge/pytest-8.3.3-0A9EDC.svg)](https://pytest.org/)
[![CI](https://img.shields.io/badge/CI-GitHub%20Actions-2088FF.svg)](https://github.com/your-username/your-repo/actions)

A simple pytest-based API test suite for the public Reqres demo site (`https://reqres.in`).

## Project Structure

- `apis/users_api.py` – API helper functions for user CRUD operations.
- `tests/test_create_user.py` – Test for creating a user.
- `tests/test_get_user.py` – Parameterized tests for retrieving existing users and verifying behavior for non-existent users.
- `tests/test_update_user.py` – Parameterized tests for updating user data.
- `tests/test_delete_user.py` – Test for deleting a user.
- `conftest.py` – Pytest fixtures for shared API session configuration (session, timeout, environment switching).
- `requirements.txt` – Python dependencies for running the tests.

## Setup

1. Create a virtual environment:
   ```bash
   python -m venv venv
   ```

2. Activate the environment:
   - Windows PowerShell:
     ```powershell
     .\venv\Scripts\Activate.ps1
     ```
   - Windows Command Prompt:
     ```cmd
     .\venv\Scripts\activate.bat
     ```

3. Install dependencies:
   ```bash
   python -m pip install -r requirements.txt
   ```

## Dependencies

This project uses the following packages:

- pytest==8.3.3
- requests==2.32.3
- pytest-html==4.1.1
- jsonschema==4.23.0

These dependencies are listed in `requirements.txt` and can be installed together with:

```bash
python -m pip install -r requirements.txt
```

## Run Tests

Execute the full suite with:

```bash
pytest
```

Run a single test file:

```bash
pytest tests/test_get_user.py
```

Run tests against different environments:

```bash
pytest --env staging
pytest --env dev
pytest --env prod
```

The `--env` option is defined in `conftest.py` and defaults to `staging` when not provided.

## Reports

To generate an HTML report for your test run:

```bash
pytest --html=reports/report.html
```

If you want a self-contained HTML file, use:

```bash
pytest --html=reports/report.html --self-contained-html
```

Preview of the generated HTML report:

![HTML report preview](reports/html-report-screenshot.svg)

## Notes

- This project uses the public Reqres API for demonstration and learning purposes.
- The tests rely on the live demo site, so they require internet access.
- `requests` is used for HTTP calls and `pytest` is used for test execution.
- Parameterized tests help cover multiple input scenarios efficiently in `test_get_user.py` and `test_update_user.py`.
- When validating responses, check the status code, response headers, response time, and JSON payload content.
- Typical response checks include:
  - `response.status_code`
  - `response.headers`
  - `response.elapsed.total_seconds()`
  - `response.json()`
