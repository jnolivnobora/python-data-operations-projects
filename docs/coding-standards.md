# Coding Standards

## Overview

These standards apply to every Python file in this portfolio.
They reflect professional expectations for a Python Developer /
Data Operations Analyst role — code that is readable, maintainable,
auditable, and safe.

Following these standards consistently is more important than
writing clever code. A colleague should be able to read any file
in this portfolio and understand it within a few minutes.

---

## File structure

Every Python source file should follow this order:

```python
"""
module_name.py
--------------
One or two sentences describing what this module does.
Who uses it, and what it produces.

All data used here is synthetic and for educational purposes only.
"""

# 1. Standard library imports
import logging
from pathlib import Path

# 2. Third-party imports
import pandas as pd

# 3. Local imports
from src.config import DATABASE_URL

# 4. Module-level logger
logger = logging.getLogger(__name__)

# 5. Constants (if any)
REQUIRED_FIELDS = ["loan_id", "principal", "loan_status"]

# 6. Functions and classes
```

---

## Naming conventions

| Thing | Convention | Example |
|-------|-----------|---------|
| Variables | snake_case | `loan_id`, `principal_balance` |
| Functions | snake_case | `read_csv_file()`, `validate_loan()` |
| Classes | PascalCase | `LoanRecord`, `ValidationReport` |
| Constants | UPPER_SNAKE_CASE | `REQUIRED_FIELDS`, `MAX_INTEREST_RATE` |
| Files | snake_case | `file_utils.py`, `report_generator.py` |
| Folders | kebab-case | `01-automation-loan-file-validator/` |
| Branches | kebab-case with prefix | `feature/csv-ingestion` |

---

## Functions

Every function must have:

- A clear, action-oriented name: `read_csv_file()` not `do_stuff()`
- Type hints on all parameters and the return value
- A docstring explaining what it does, its arguments, and what it returns
- A single responsibility — if a function does two things, split it

```python
def validate_required_fields(
    df: pd.DataFrame,
    required_fields: list[str]
) -> pd.DataFrame:
    """
    Identify rows with missing values in required fields.

    Args:
        df: Input DataFrame containing loan records.
        required_fields: List of column names that must not be null.

    Returns:
        DataFrame containing only rows with at least one missing
        required field, with an added 'exception_reason' column.
    """
    mask = df[required_fields].isnull().any(axis=1)
    exceptions = df[mask].copy()
    exceptions["exception_reason"] = "Missing required field"
    logger.info(f"Found {len(exceptions)} records with missing required fields")
    return exceptions
```

---

## Logging rules

| Situation | Level | Example |
|-----------|-------|---------|
| Normal operations | INFO | `logger.info(f"Read {len(rows)} rows from {file_path.name}")` |
| Edge case, unusual but recoverable | WARNING | `logger.warning(f"File has 0 rows: {file_path}")` |
| Operation failed | ERROR | `logger.error(f"File not found: {file_path}")` |
| Detailed debugging info | DEBUG | `logger.debug(f"Processing row: {row}")` |

Never use `print()` in production code.
Use `print()` only in quick demo scripts or notebooks during development.

Log messages must be:

- Specific enough to diagnose a problem without reading the code
- Consistent: always include the file name, record count, or ID
- Free of sensitive data — never log real credentials or PII

---

## Error handling rules

Always raise specific exception types with descriptive messages:

```python
# Good
raise FileNotFoundError(
    f"Loan file not found: {file_path}. "
    f"Check that the file was delivered to the expected path."
)

# Bad
raise Exception("error")
```

Catch only what you can handle:

```python
# Good — handle only FileNotFoundError, let other errors propagate
try:
    rows = read_csv_file(file_path)
except FileNotFoundError as e:
    logger.error(f"Cannot read file: {e}")
    raise

# Bad — catches everything, hides real bugs
try:
    rows = read_csv_file(file_path)
except Exception:
    pass
```

Never use bare `except:` or `except Exception: pass`.
Silent failures are the hardest bugs to trace in production.

---

## File paths

Always use `pathlib.Path`. Never use string concatenation for paths.

```python
# Good
from pathlib import Path
file_path = Path(__file__).parent.parent / "data" / "sample" / "loans.csv"

# Bad
file_path = "../../data/sample/loans.csv"
```

`pathlib` is cross-platform — it works correctly on Windows, Mac,
and Linux without any changes to your code.

---

## Secrets and credentials

Never hardcode credentials, API keys, or passwords in code.

```python
# Good
import os
from dotenv import load_dotenv
load_dotenv()
api_key = os.getenv("OPENAI_API_KEY")

# Bad — never do this
api_key = "sk-abc123thisisreal"
```

Rules:

- Always add `.env` to `.gitignore` before the first commit
- Always commit a `.env.example` with placeholder values only
- Never commit a real `.env` file
- Never hardcode credentials in any Python file, config file, or notebook

---

## Testing rules

- Every function with logic must have at least one test
- Test the happy path, common edge cases, and error conditions
- Use fixtures for shared setup — do not repeat setup code in every test
- Use `tmp_path` (provided by pytest) for temporary file output in tests
- Test names must describe what they are testing:
  - `test_read_csv_returns_list` — good
  - `test_function_1` — bad
- Never use real data in tests — always use synthetic data or `tmp_path`

```python
# Good test structure
def test_validate_required_fields_flags_null_principal(sample_df):
    """Rows with null principal should appear in the exceptions output."""
    result = validate_required_fields(sample_df, ["principal"])
    assert len(result) > 0
    assert "exception_reason" in result.columns
```

---

## Code quality checklist

Before committing any code, verify:

- [ ] All functions have type hints and docstrings
- [ ] No `print()` statements in production code — use `logger`
- [ ] No hardcoded file paths — use `pathlib`
- [ ] No hardcoded credentials — use `python-dotenv`
- [ ] All error handling uses specific exception types
- [ ] Tests cover the happy path and at least one edge case
- [ ] Module-level docstring explains what the file does
- [ ] `requirements.txt` is updated if new packages were added
- [ ] `.env` is in `.gitignore`
- [ ] No real data or secrets anywhere in the commit

---

## What readable code means in practice

Readable code is code that a colleague can understand without asking
you to explain it. Before you commit, ask yourself:

1. Would a junior analyst understand what this function does
   from its name and docstring alone?
2. If this script ran at 3 AM and failed, would the log message
   tell an on-call analyst exactly what went wrong?
3. If someone had to maintain this code in six months,
   would they curse your name — or thank you?
