# DevOps Lab 2 – Practical Record

## Experiment 2

**Subject:** DevOps  
**Title:** Design and Implement a Basic CI Workflow Triggered by Commits Using GitHub Actions

## 1. Aim

To design and implement a basic Continuous Integration (CI) workflow using GitHub Actions that runs automated Python tests whenever code is pushed to the `main` branch.

## 2. Software Requirements

- Visual Studio Code
- Python 3.x
- Git
- GitHub account
- GitHub Actions

## 3. Project Structure

```text
CI-Lab2/
├── calculator.py
├── test_calculator.py
├── DEVOPS_LAB_2_PRACTICAL_RECORD.md
└── .github/
    └── workflows/
        └── ci.yml
```

## 4. Implementation

### `calculator.py`

```python
def add(a, b):
    return a + b


def subtract(a, b):
    return a - b


def multiply(a, b):
    return a * b


def divide(a, b):
    if b == 0:
        raise ValueError("Cannot divide by zero")
    return a / b
```

### `test_calculator.py`

The test module contains five tests covering addition, subtraction,
multiplication, division, and division by zero.

### `.github/workflows/ci.yml`

```yaml
name: Basic CI Workflow

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Code
        uses: actions/checkout@v4

      - name: Setup Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.12'

      - name: Run Tests
        run: python -m unittest -v
```

## 5. Local Execution

Command executed:

```text
python -m unittest -v
```

Result:

```text
Ran 5 tests in 0.001s

OK
```

All five local unit tests passed.

## 6. Git Execution

The project was initialized locally and committed on the `main` branch.

```text
Commit: 21c02ae Initial CI workflow commit
Remote: https://github.com/xavieramith-wq/CI-Lab2.git
```

The initial push is pending GitHub authentication and repository creation.

## 7. Evidence Checklist

Capture and attach the following screenshots after the GitHub repository is
created and the push succeeds:

1. Project structure showing the Python files and `.github/workflows/ci.yml`.
2. `calculator.py` source code.
3. `test_calculator.py` source code.
4. Successful local `python -m unittest -v` execution.
5. GitHub repository showing the uploaded files.
6. `ci.yml` configuration on GitHub.
7. Successful GitHub Actions run.
8. Failed GitHub Actions run after introducing an incorrect expected value.
9. Successful GitHub Actions run after correcting the test.

## 8. Result

The calculator application, unit tests, and GitHub Actions workflow were
implemented successfully. Local validation passed all five tests. GitHub
Actions execution and commit-trigger verification remain pending until the
GitHub repository is created and the project is pushed.
