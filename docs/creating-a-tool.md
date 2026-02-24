# Creating a New Tool

This guide explains how to add a new tool capability to Hive.

## What a tool is in Hive

A tool is a callable capability that agents can use during execution (for example, calling an external API, reading internal data, or triggering an action).
In this repository, concrete tool code lives under `tools/src/aden_tools/`.

## Prerequisites

- Python 3.11+
- `uv` installed
- Local workspace initialized (`./quickstart.sh`)

## 1) Create the tool module

Add a new Python module under an appropriate tools package:

```bash
mkdir -p tools/src/aden_tools/tools/my_domain
```

Implement the tool with:

- Strong type hints
- Clear parameter validation
- User-safe error messages
- Google-style docstrings for public APIs

## 2) Define tool interface contract

For each public tool function/method, document:

- Inputs (name, type, required/optional, meaning)
- Return shape/type
- Error cases
- Example call

## 3) Register the tool

Wire the tool into the existing registration/discovery mechanism used in `tools/src/aden_tools`.
Follow patterns used by neighboring tool modules to keep consistency.

## 4) Add tests

Create unit tests in `tools/tests/` and cover:

- Successful execution
- Validation failures
- Downstream API failure handling

Run checks:

```bash
cd tools
uv run python -m pytest tests -v
ruff check .
ruff format --check .
```

## 5) Make it usable from agents

After registration, verify an agent/runtime path can call the tool and consume its output.
Document usage in the relevant agent README.

## Tool PR Checklist

- [ ] Public APIs include docstrings
- [ ] Type hints added for all function signatures
- [ ] Tests added/updated in `tools/tests/`
- [ ] `make check` passes from repo root
