# CareerAI - Skill-Based Career Recommendation System

CareerAI is a Flask web application that analyzes a user profile (manual input or resume upload), computes role matches, and explains missing skills with a learning roadmap.

## Current Capabilities

- Account registration and login with bcrypt password hashing
- Email verification flow with link and OTP support
- Resume upload (`pdf`, `doc`, `docx`, `txt`) and profile extraction
- Manual profile entry (skills, interests, education, experience)
- Profile persistence in database and auto-load on dashboard
- Skill-based career matching with explainable output
- Live market jobs and market skill demand (Adzuna-backed service)
- Skill-gap summary and learning roadmap generation
- Feedback history and deletion
- Light and dark theme support across auth and dashboard pages

## Tech Stack

- Python 3.12+
- Flask 3
- Flask-SQLAlchemy
- Flask-WTF (CSRF protection)
- SQLite (default)
- Bootstrap 5 + Vanilla JavaScript

## Project Layout

- `backend/app.py` - Flask routes and application entry point
- `backend/config.py` - Environment-driven configuration
- `backend/models/` - SQLAlchemy models
- `backend/services/` - Matching, auth, and related services
- `frontend/templates/` - Jinja templates
- `frontend/static/` - CSS and JavaScript assets

## Local Setup

1. Create and activate a virtual environment.
2. Install dependencies.
3. Create environment file from the backend template.
4. Start the app.

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
cp backend/.env.template backend/.env
python backend/app.py
```

App URL:

`http://127.0.0.1:5000`

## Configuration Notes

- Environment variables are loaded from `backend/.env`.
- Default database is SQLite (`backend/instance/career_system.db`).
- SMTP settings in `backend/.env` enable email delivery for verification.
- Keep `DEBUG=False` in production.

## Docker

If you prefer containerized run:

```bash
docker-compose up --build
```

## Important Runtime Behavior

- Dashboard recommendations use a quality threshold and hide weak matches.
- If no recommendation meets threshold, dashboard shows a clear "no strong matches" state.
- Profile snapshots are saved from both manual input and resume upload, then auto-restored after login.
