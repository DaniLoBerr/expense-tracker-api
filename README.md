# Expense Tracker API

A REST API for tracking and analyzing personal expenses, built with **FastAPI** and **PostgreSQL**. This is the first project in my roadmap to become a Backend Engineer, and it serves as a testbed for applying new concepts (security, caching, authentication) as I learn them.

## 📌 Project goal

Build a solid, well-tested, and secure API for the simplest possible use case that still has real data relationships: users who log expenses, organized into categories, with aggregated statistics. The simplicity of the domain is intentional — the focus is on **implementation quality**, not business complexity.

## ⚙️ Features

### User management
- User registration and authentication
- Authentication via OAuth2 + JWT (access token + refresh token)
- Each user can only see and modify their own data

### Category management
- CRUD for expense categories (e.g. "Food", "Transport", "Entertainment")
- Default categories on user creation + ability to create custom categories

### Expense management
- CRUD for expenses: amount, date, description, associated category
- Filtering by date range and category
- Pagination on listings

### Statistics
- Total monthly spending summary
- Spending breakdown by category
- Month-over-month comparison

## 🔒 Security

Implemented following the [OWASP API Security Top 10](https://owasp.org/API-Security/editions/2023/en/0x00-header/):
- Object-level authorization (a user cannot access another user's expenses even by guessing the ID)
- Rate limiting on authentication endpoints
- Strict input validation (Pydantic)
- Secrets managed via environment variables, never hardcoded

## 🚀 Performance

- Redis caching on statistics endpoints (the most expensive to compute and the most frequently queried)
- Database indexes on the most frequently queried columns (user, date, category)

## 🧪 Testing

- Unit and integration test coverage with `pytest`
- TDD applied throughout development
- CI configured with GitHub Actions: tests + linting on every Pull Request

## 🛠️ Tech stack

| Category | Technology |
|---|---|
| Framework | FastAPI |
| Database | PostgreSQL |
| ORM | SQLAlchemy |
| Cache | Redis |
| Authentication | OAuth2 + JWT |
| Testing | Pytest |
| Containers | Docker + Docker Compose |
| CI/CD | GitHub Actions |

## 📂 Project structure

```
expense-tracker-api/
├── app/
│   ├── api/            # Endpoints (routers)
│   ├── models/         # SQLAlchemy models
│   ├── schemas/        # Pydantic schemas
│   ├── core/            # Configuration, security, dependencies
│   ├── services/         # Business logic
│   └── main.py
├── tests/
├── alembic/              # Database migrations
├── docker-compose.yml
├── Dockerfile
└── requirements.txt
```

## 🏁 How to run the project

```bash
# Clone the repository
git clone https://github.com/DaniLoBerr/expense-tracker-api.git
cd expense-tracker-api

# Start the services (API + PostgreSQL + Redis)
docker-compose up --build

# Run migrations
docker-compose exec web alembic upgrade head

# Run tests
docker-compose exec web pytest
```

The interactive API documentation will be available at `http://localhost:8000/docs`.

## 🕓 Project evolution

This project wasn't built all at once: it grew in distinct phases, each tied to a specific course or resource in my learning roadmap. This README describes the final state, but the commit history reflects this progression:

| Phase | What was added | Motivated by |
|---|---|---|
| 1 | Initial build — expense/category CRUD, basic auth | FastAPI Tutorial + TDD with FastAPI and Docker |
| 2 | Security (object-level authorization, rate limiting, validation) | OWASP API Security Top 10 |
| 3 | Redis caching on statistics endpoints | Redis University: RU101 |
| 4 | Authentication rewritten with OAuth2 + JWT | oauth.com + jwt.io |
| 5 | CI/CD pipeline (tests + lint on every PR) | GitHub Actions Quickstart |

## 📈 Project status

🚧 Actively in development — this README will be updated as the project progresses.

## 🗺️ Context

This project is part of my personal learning roadmap to become a Backend Engineer, which you can check out on my [GitHub profile](https://github.com/DaniLoBerr).
