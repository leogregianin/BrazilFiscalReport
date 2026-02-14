# Contributing

Contributions are welcome! Here's how to set up the project for development.

## Development Setup

1. Clone the repository:

    ```bash
    git clone https://github.com/Engenere/BrazilFiscalReport.git
    cd BrazilFiscalReport
    ```

2. Create a virtual environment and install dependencies:

    ```bash
    python -m venv .venv
    source .venv/bin/activate  # Linux/macOS
    pip install -e '.[dacte,damdfe,cli]'
    pip install pytest pytest-cov ruff
    ```

3. Install pre-commit hooks:

    ```bash
    pip install pre-commit
    pre-commit install
    ```

## Running Tests

The project uses `pytest` for testing. You'll also need `qpdf` installed for PDF comparison tests:

```bash
# Install qpdf (Ubuntu/Debian)
sudo apt-get install qpdf

# Run all tests
pytest

# Run with coverage
pytest --cov=./brazilfiscalreport --cov-branch

# Run tests for a specific document type
pytest tests/test_danfe.py
```

## Code Style

The project uses [Ruff](https://github.com/astral-sh/ruff) for linting and formatting. Pre-commit hooks will automatically check your code before each commit.

```bash
# Manual check
ruff check .
ruff format .
```

## Regenerating Reference PDFs

When making changes to PDF output, you can regenerate the reference PDFs used in tests:

```bash
BFR_GENERATE_EXPECTED=1 pytest tests/test_danfe.py
```

!!! warning
    Only regenerate reference PDFs when you intentionally changed the PDF output. Always review the visual diff before committing.

## Submitting Changes

1. Fork the repository
2. Create a feature branch (`git checkout -b my-feature`)
3. Commit your changes
4. Push to your fork and open a Pull Request

Make sure all tests pass and pre-commit hooks are clean before submitting.
