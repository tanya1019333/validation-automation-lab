- **Project Name**: Validation Automation Lab
- **Purpose**: A practice project for building a QA/validation automation workflow using Python and Linux.
- **Current status**: In progress (repo skeleton + tooling setup)

- **Planned features**:
    - test runner
    - log collection
    - retry/timeout handling
    - test report generation

## Project Structure

This repository is a practice project for building a QA / validation automation workflow in Python and Linux.

- `src/validation_lab/` — source code for the validation automation lab (test runner, log handling, reporting modules will be added here)
- `tests/` — automated tests (starting with a smoke test to verify the test workflow works)
- `configs/` — configuration files (e.g., sample test cases in YAML)
- `scripts/` — helper scripts for local execution
- `README.md` — project overview, setup, and roadmap

## Why These Files Exist

This repository is set up as a reusable engineering template (not just a one-off script). The goal is to practice a workflow that is reproducible, maintainable, and ready to grow into a real validation automation project.

- `requirements-dev.txt` — development dependencies (pytest, ruff, black, pre-commit, pyyaml)
- `pyproject.toml` — centralized configuration for code formatting, linting, and test settings
- `.pre-commit-config.yaml` — automated checks and formatting before commits
- `.gitignore` — excludes local environments, caches, and temporary files from version control
- `tests/test_smoke.py` — minimal test to confirm the test framework is working

## NOTE:
- pyproject.toml — 工具設定集中管理檔(這個專案的程式碼規則設定中心)
    - black 的格式規則（例如 line length）
    - ruff 的 lint 規則（檢查哪些問題）
    - pytest 要去哪裡找 tests、跑測試時帶什麼參數

    雖然沒有這個工具可能還是能跑，但規則不一致、之後很難維護。
- .pre-commit-config.yaml — commit 前檢查規則(告訴 pre-commit：「每次 commit 前要跑哪些檢查/自動修正」)
- required:
    - pytest（測試）
    - ruff（lint）
    - black（格式化）
    - pre-commit（commit 前檢查）
    - pyyaml（之後 config 會用到，可先裝）
- launch python virtual environment:
    ```bash
    python3 -m venv .venv
    source .venv/bin/activate

    python -m pip install --upgrade pip
    pip install pytest ruff black pre-commit pyyaml
    ```
- check python tools
    ```bash
    pytest --version
    ruff --version
    black --version
    pre-commit --version
    ```
- install pre-commit hooks:
    ```bash
    pre-commit install
    ```
- checks
    ```bash
    pytest
    ruff check .
    black --check .
    ```
    Returned
    ```
    (.venv) ... validation-automation-lab % pytest  .[100%]
    1 passed in 0.00s
    (.venv) ... validation-automation-lab % ruff check .
    All checks passed!
    (.venv) ... validation-automation-lab % black --check .
    would reformat .../validation-automation-lab/src/validation_lab/__init__.py
    would reformat .../validation-automation-lab/tests/test_smoke.py

    Oh no! 💥 💔 💥
    2 files would be reformatted.
    ```
    ```
    pre-commit run --all-files
    ```
- Debug
    ```
    //reformatted
    black .
    //add git track & ensure .gitignore included .venv
    git add .
    //run again if all passed then run checks again
    pre-commit run --all-files
    ```
