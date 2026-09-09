# Expense Tracker API

A personal expense-tracking REST API built with **FastAPI**. Deliberately simple domain, deliberately serious engineering: the point of this project is not what it does, it's **how well it's built**.

![Status](https://img.shields.io/badge/status-planned%20build-yellow)
![Python](https://img.shields.io/badge/python-3.12-blue)
![FastAPI](https://img.shields.io/badge/FastAPI-009688)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791)
![Docker](https://img.shields.io/badge/Docker-2496ED)

---

## 📍 Status — read this first

> **📋 Planned build.** This README describes the design of a project I have not started yet. It is the first build of my [backend engineering roadmap](https://github.com/DaniLoBerr), and it begins once I finish the FastAPI documentation and the TDD-with-Docker course that precede it.
>
> | | |
> |---|---|
> | ✅ **Done** | Scope, domain model, and engineering decisions below |
> | 🟡 **In progress** | Prerequisites — [FastAPI docs](https://github.com/DaniLoBerr/fastapi-docs), TDD with FastAPI & Docker |
> | 📋 **Next** | Phase 1 of the build table below |
>
> I keep the design public before the code exists on purpose: the plan is part of the work, and I'd rather show an honest roadmap than an inflated repo. Every phase below will be marked as it lands.

---

## 🎯 Why this project

A CRUD expense tracker is not an original idea, and that's the point. Choosing a domain everyone already understands means the interesting part of the repo is the engineering: how authorization is enforced per object, how the test suite is structured, how the pipeline is set up, how caching is invalidated, and how it all gets to production.

Ambitious domains hide weak implementation. This one has nowhere to hide.

## ⚙️ Scope

**Users and authentication**
- Registration and login with OAuth2 password flow
- JWT with access token + refresh token
- Password hashing, secrets from environment configuration

**Core domain**
- CRUD for expense categories
- CRUD for expenses: amount, date, category, notes
- Filtering (by date range, category, amount) and pagination
- Statistics endpoints: monthly totals, breakdown by category, trends

## 🔬 Engineering focus

This is what the project is actually for:

| Area | What gets demonstrated |
|---|---|
| **Object-level authorization** | A user can never read or modify another user's expenses — enforced in the data access layer and **proven with tests that try to break it** (OWASP API #1) |
| **Test suite design** | pytest with fixtures, factories and parametrization; unit and integration tests separated; coverage that means something |
| **CI/CD** | Tests, linting (`ruff`) and formatting checks on every pull request, with PostgreSQL as a service in the runner |
| **Security hardening** | Rate limiting, strict input validation with Pydantic, deliberate control of which fields each endpoint returns |
| **Caching** | Redis on the statistics endpoints — including the hard part, which is invalidation — with a documented before/after benchmark |
| **Infrastructure as code** | Terraform-managed AWS deployment, not a manual click-through |

## 🛠️ Tech stack

| Category | Technology |
|---|---|
| Framework | FastAPI |
| Database | PostgreSQL |
| ORM / migrations | SQLAlchemy · Alembic |
| Cache | Redis |
| Auth | OAuth2 password flow + JWT (access + refresh) |
| Testing | pytest · Locust (load) |
| Containers | Docker · Docker Compose |
| CI/CD | GitHub Actions |
| Infrastructure | Terraform · AWS |

## 🗓️ Build phases

Each phase is a separate step of the roadmap, and each one is motivated by something specific I studied for it.

| Phase | What gets added | Driven by |
|---|---|---|
| 1 | Initial build — CRUD, OAuth2 + JWT, PostgreSQL, pytest, Docker | FastAPI docs · TDD with FastAPI and Docker |
| 2 | CI/CD pipeline — tests, lint and format on every PR | GitHub Actions |
| 3 | Security hardening — object-level authorization, rate limiting, strict validation | OWASP API Security Top 10 (2023) |
| 4 | Production deployment on AWS with Terraform | Scalable FastAPI Applications on AWS |
| 5 | E2E test suite in the pipeline | Playwright |
| 6 | Load testing and documented benchmark | Locust |
| 7 | Redis caching on statistics + before/after comparison | Redis University |

## 🏁 Running it *(from phase 1 onwards)*

```bash
git clone https://github.com/DaniLoBerr/expense-tracker-api.git
cd expense-tracker-api

docker compose up --build
docker compose exec web alembic upgrade head
docker compose exec web pytest
```

Interactive API documentation at `http://localhost:8000/docs`.

## 🗺️ Context

This is project **1 of 3** in a public roadmap taking me from QA engineering to backend development. Project 2 ([Project Management SaaS API](https://github.com/DaniLoBerr/project-management-saas-api)) covers architecture integration; project 3 ([Event Tracking API](https://github.com/DaniLoBerr/event-tracking-analytics-api)) covers high-volume systems.

👉 Full roadmap on my **[GitHub profile](https://github.com/DaniLoBerr)**.
