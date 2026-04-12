# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Spendly** — a Flask-based personal expense tracker web app. The project is structured as a step-by-step student build; many routes in `app.py` are placeholders with "coming in Step N" stubs waiting to be implemented.

## Commands

```bash
# Install dependencies (activate venv first)
source venv/Scripts/activate          # Windows (bash)
pip install -r requirements.txt

# Run the dev server (port 5001)
python app.py

# Run tests
pytest

# Run a single test file
pytest tests/test_db.py
```

The database file (`expense_tracker.db`) is git-ignored and created at runtime.

## Architecture

- **`app.py`** — Flask application entry point. All routes live here. No blueprints yet.
- **`database/db.py`** — SQLite helpers (to be implemented in Step 1): `get_db()`, `init_db()`, `seed_db()`. `get_db()` should use `sqlite3.Row` as `row_factory` and enable `PRAGMA foreign_keys = ON`.
- **`templates/`** — Jinja2 templates. `base.html` is the shared layout (navbar + footer); all other templates extend it via `{% extends "base.html" %}`.
- **`static/css/style.css`** and **`static/js/main.js`** — single CSS and JS files; no build step.

## Step-by-step build plan

The placeholder routes signal the intended build order:
1. Database setup (`database/db.py`)
2. Auth — register & login (form handling, password hashing)
3. Auth — logout & session management
4. Profile page
5–6. Expense listing / dashboard
7. Add expense
8. Edit expense
9. Delete expense

## Key conventions

- SQLite database filename: `expense_tracker.db` (project root, git-ignored).
- Currency is Indian Rupees (₹); amounts are stored as integers or floats in INR.
- Flask debug mode is on (`debug=True`) during development.
