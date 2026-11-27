# TaskBoard

Minimal task management REST API (FastAPI) used as the base project of the DevSecOps course at ESIEE Paris.

## Requirements

- Python 3.11 or newer
- Git

## Installation

```bash
git clone git@github.com:GaetanRW/taskboard.git
cd taskboard
python -m venv .venv
source .venv/bin/activate        # Windows (cmd): .venv\Scripts\activate
pip install -r requirements.txt
```

## Run

```bash
uvicorn app.main:app --reload
```

Run the command from the repository root (the folder that contains `app/`).

- API docs (Swagger UI): http://127.0.0.1:8000/docs
- Health check: http://127.0.0.1:8000/health

## Endpoints

| Method | Path | Description |
| --- | --- | --- |
| POST | `/tasks` | Create a task (201) |
| GET | `/tasks` | List all tasks |
| GET | `/tasks/{task_id}` | Get one task (404 if unknown) |
| PATCH | `/tasks/{task_id}` | Update only the fields sent (404 if unknown) |
| DELETE | `/tasks/{task_id}` | Delete a task (204, 404 if unknown) |

## Tests

```bash
pytest -v
```

## Environment variables

Copy `.env.example` to `.env` and adjust the values locally.
**Never commit `.env`**: it is ignored by `.gitignore`, and real secrets must never appear in the Git history.

## Project structure

```
app/
  main.py          # FastAPI app and /health
  schemas.py       # Pydantic models
  routers/tasks.py # CRUD endpoints (in-memory storage)
tests/             # pytest tests
docs/              # security notes
```